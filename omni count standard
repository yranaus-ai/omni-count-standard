<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Omni Count</title>

  <style>
    body {
      margin: 0;
      background: #050914;
      color: #00ffd5;
      font-family: monospace;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }

    #title {
      opacity: 0.6;
      font-size: 18px;
    }

    #oc {
      font-size: 40px;
      margin-top: 20px;
    }

    #sub {
      margin-top: 10px;
      opacity: 0.5;
      font-size: 12px;
    }
  </style>
</head>

<body>

<div id="title">Omni Count (OC)</div>
<div id="oc">Loading...</div>
<div id="sub">Atomic-time based system</div>

<script>
  const epoch = Date.parse("1945-07-16T11:29:21Z");
  const OT = 9192631770;

  function format(n){
    return n.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ":");
  }

  function update(){
    const now = Date.now();
    const seconds = (now - epoch) / 1000;
    const oc = Math.floor(seconds * OT);

    document.getElementById("oc").textContent =
      "OC " + format(oc);
  }

  setInterval(update, 50);
  update();
</script>

</body>
</html>