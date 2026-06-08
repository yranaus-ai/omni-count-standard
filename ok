<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Omni Count Dashboard</title>

<style>
body {
  margin: 0;
  background: #050914;
  color: #00ffd5;
  font-family: monospace;
  display: flex;
  flex-direction: column;
  align-items: center;
}

header {
  margin-top: 20px;
  opacity: 0.7;
  font-size: 14px;
}

#oc {
  font-size: 34px;
  margin-top: 20px;
}

.panel {
  margin-top: 30px;
  width: 80%;
  max-width: 600px;
  border: 1px solid rgba(0,255,213,0.3);
  padding: 15px;
}

.row {
  display: flex;
  justify-content: space-between;
  margin: 6px 0;
}

.bar {
  height: 10px;
  background: rgba(0,255,213,0.1);
  margin-top: 5px;
  position: relative;
}

.fill {
  height: 100%;
  background: #00ffd5;
  width: 0%;
}
</style>
</head>

<body>

<header>Omni Count Dashboard (OC-DASH v1)</header>

<div id="oc">Loading...</div>

<div class="panel">
  <div class="row"><span>Cycle</span><span id="cycle"></span></div>
  <div class="row"><span>Segment</span><span id="segment"></span></div>
  <div class="row"><span>Beat</span><span id="beat"></span></div>
  <div class="row"><span>Pulse</span><span id="pulse"></span></div>
  <div class="row"><span>Tick</span><span id="tick"></span></div>
</div>

<div class="panel">
  <div>Cycle Progress</div>
  <div class="bar"><div class="fill" id="bar"></div></div>
</div>

<script>
const EPOCH = Date.parse("1945-07-16T11:29:21Z");
const OT = 9192631770;

// breakdown constants
const PULSES_PER_BEAT = 1000;
const BEATS_PER_SEGMENT = 1000;
const SEGMENTS_PER_CYCLE = 1000;

function format(n){
  return n.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ":");
}

function update(){

  const now = Date.now();
  const oc = Math.floor(((now - EPOCH)/1000) * OT);

  // breakdown
  let pulse = Math.floor(oc / OT);
  let beat = Math.floor(pulse / PULSES_PER_BEAT);
  let segment = Math.floor(beat / BEATS_PER_SEGMENT);
  let cycle = Math.floor(segment / SEGMENTS_PER_CYCLE);

  let tick = oc % OT;

  // display
  document.getElementById("oc").textContent = "OC " + format(oc);

  document.getElementById("cycle").textContent = cycle;
  document.getElementById("segment").textContent = segment % 1000;
  document.getElementById("beat").textContent = beat % 1000;
  document.getElementById("pulse").textContent = pulse % 1000;
  document.getElementById("tick").textContent = tick;

  // cycle progress bar
  let progress = (segment % 1000) / 1000 * 100;
  document.getElementById("bar").style.width = progress + "%";
}

setInterval(update, 50);
update();
</script>

</body>
</html>