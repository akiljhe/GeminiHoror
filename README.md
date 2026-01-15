<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8" />
<title>Gema Penderitaan</title>
<style>
html, body {
    margin: 0;
    overflow: hidden;
    background: black;
    font-family: monospace;
}
#ui {
    position: fixed;
    color: white;
    padding: 10px;
    z-index: 10;
}
#stamina {
    width: 200px;
    height: 10px;
    background: #333;
}
#stamina div {
    height: 100%;
    background: red;
}
#radar {
    position: fixed;
    top: 10px;
    right: 10px;
    width: 150px;
    height: 150px;
    background: rgba(0,0,0,.6);
    border: 1px solid #555;
}
</style>
</head>
<body>
<div id="ui">
    <div>STAMINA</div>
    <div id="stamina"><div></div></div>
</div>
<canvas id="radar"></canvas>

<script src="https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.min.js"></script>
<script>
/* ================== BASIC SETUP ================== */
const scene = new THREE.Scene();
scene.fog = new THREE.Fog(0x000000, 5, 35);

const camera = new THREE.PerspectiveCamera(75, innerWidth/innerHeight, 0.1, 100);
const renderer = new THREE.WebGLRenderer({antialias:true});
renderer.setSize(innerWidth, innerHeight);
document.body.appendChild(renderer.domElement);

/* ================== AUDIO ENGINE ================== */
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
function heartbeat(freq=2){
    const osc = audioCtx.createOscillator();
    const gain = audioCtx.createGain();
    osc.frequency.value = 80;
    gain.gain.value = 0.1;
    osc.connect(gain).connect(audioCtx.destination);
    osc.start();
    osc.stop(audioCtx.currentTime + 1/freq);
}

/* ================== MAZE GENERATION ================== */
const SIZE = 25;
const maze = Array.from({length:SIZE}, ()=>Array(SIZE).fill(1));

function carve(x,y){
    maze[y][x] = 0;
    const dirs = [[1,0],[-1,0],[0,1],[0,-1]].sort(()=>Math.random()-0.5);
    for(const [dx,dy] of dirs){
        const nx = x + dx*2;
        const ny = y + dy*2;
        if(nx>0 && ny>0 && nx<SIZE-1 && ny<SIZE-1 && maze[ny][nx]){
            maze[y+dy][x+dx]=0;
            carve(nx,ny);
        }
    }
}
carve(1,1);

/* ================== WALLS ================== */
const wallGeo = new THREE.BoxGeometry(1,2,1);
const wallMat = new THREE.MeshStandardMaterial({color:0x222222});
const walls = [];

for(let y=0;y<SIZE;y++){
    for(let x=0;x<SIZE;x++){
        if(maze[y][x]){
            const w = new THREE.Mesh(wallGeo, wallMat);
            w.position.set(x,1,y);
            scene.add(w);
            walls.push(w);
        }
    }
}

/* ================== LIGHTING ================== */
const light = new THREE.PointLight(0xff0000, 1, 10);
scene.add(light);
scene.add(new THREE.AmbientLight(0x111111));

/* ================== PLAYER ================== */
const player = {
    pos: new THREE.Vector3(1,1.5,1),
    stamina: 1,
    speed: 0.05
};
camera.position.copy(player.pos);

const keys = {};
addEventListener('keydown',e=>keys[e.code]=true);
addEventListener('keyup',e=>keys[e.code]=false);

/* ================== ENEMY ================== */
const enemyGeo = new THREE.SphereGeometry(0.4,16,16);
const enemyMat = new THREE.MeshBasicMaterial({color:0xff0000});
const enemy = new THREE.Mesh(enemyGeo, enemyMat);
enemy.position.set(SIZE-2,1.2,SIZE-2);
scene.add(enemy);

let teleportTimer = 0;

/* ================== RADAR ================== */
const radar = document.getElementById("radar");
radar.width = radar.height = 150;
const rctx = radar.getContext("2d");

/* ================== GAME LOOP ================== */
function animate(){
    requestAnimationFrame(animate);

    let move = new THREE.Vector3();
    if(keys.KeyW) move.z -= 1;
    if(keys.KeyS) move.z += 1;
    if(keys.KeyA) move.x -= 1;
    if(keys.KeyD) move.x += 1;

    let sprint = keys.ShiftLeft && player.stamina>0;
    let speed = sprint ? 0.1 : player.speed;
    if(sprint) player.stamina -= 0.005;
    else player.stamina += 0.002;
    player.stamina = Math.min(1,Math.max(0,player.stamina));

    move.normalize().multiplyScalar(speed);
    player.pos.add(move);
    camera.position.copy(player.pos);

    /* Enemy AI */
    enemy.position.lerp(player.pos, 0.002);
    const dist = enemy.position.distanceTo(player.pos);
    if(dist<5) heartbeat(5-dist);

    teleportTimer+=0.01;
    if(teleportTimer>15){
        teleportTimer=0;
        enemy.position.set(
            Math.floor(Math.random()*SIZE),
            1.2,
            Math.floor(Math.random()*SIZE)
        );
    }

    light.position.copy(enemy.position);

    /* UI */
    document.querySelector("#stamina div").style.width = (player.stamina*100)+"%";

    /* Radar */
    rctx.clearRect(0,0,150,150);
    rctx.fillStyle="white";
    rctx.fillRect(player.pos.x*5, player.pos.z*5, 4,4);
    rctx.fillStyle="red";
    rctx.fillRect(enemy.position.x*5, enemy.position.z*5, 4,4);

    renderer.render(scene,camera);
}
animate();

addEventListener('click',()=>audioCtx.resume());
addEventListener('resize',()=>{
    camera.aspect=innerWidth/innerHeight;
    camera.updateProjectionMatrix();
    renderer.setSize(innerWidth,innerHeight);
});
</script>
</body>
</html>
