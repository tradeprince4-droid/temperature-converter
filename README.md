# temperature-converter
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Temperature Converter</title>
<style>
body{margin:0;min-height:100vh;display:grid;place-items:center;background:linear-gradient(135deg,#172554,#0e7490);font-family:Arial;color:white}
.card{width:min(350px,85vw);padding:28px;background:#ffffff15;border:1px solid #ffffff35;border-radius:18px}
input,select,button{width:100%;box-sizing:border-box;padding:13px;margin:9px 0;border-radius:8px;border:0}
button{background:#67e8f9;cursor:pointer;font-weight:bold}
#result{font-size:23px;font-weight:bold;margin-top:18px}
</style>
</head>
<body>
<div class="card">
<h1>🌡 Temperature</h1>
<input id="value" type="number" placeholder="Enter temperature">
<select id="from">
<option value="C">Celsius (°C)</option>
<option value="F">Fahrenheit (°F)</option>
<option value="K">Kelvin (K)</option>
</select>
<select id="to">
<option value="F">Fahrenheit (°F)</option>
<option value="C">Celsius (°C)</option>
<option value="K">Kelvin (K)</option>
</select>
<button onclick="convert()">Convert</button>
<div id="result" aria-live="polite"></div>
</div>
<script>
function convert(){
const value=Number(document.getElementById("value").value);
const from=document.getElementById("from").value;
const to=document.getElementById("to").value;
const out=document.getElementById("result");
if(document.getElementById("value").value.trim()===""){
out.textContent="Enter a temperature first.";return;
}
let c=from==="C"?value:from==="F"?(value-32)*5/9:value-273.15;
if(c< -273.15){out.textContent="Temperature cannot be below absolute zero.";return}
let answer=to==="C"?c:to==="F"?c*9/5+32:c+273.15;
out.textContent=answer.toFixed(2)+" "+({C:"°C",F:"°F",K:"K"}[to]);
}
</script>
</body>
</html>
