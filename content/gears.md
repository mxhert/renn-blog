
---
# 

<!DOCTYPE html>
<html>
<head>
  <style>
    input[type=number]::-webkit-inner-spin-button,
    input[type=number]::-webkit-outer-spin-button {
        -webkit-appearance: none;
        margin: 0;
    }
    input[type=number] {
        -moz-appearance: textfield;
    }
  </style>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script>
    function calculateSpeeds() {
      const redline = parseFloat(document.getElementById('redline').value);
      const redline2 = parseFloat(document.getElementById('redline2').value);
      const width = parseFloat(document.getElementById('width').value);
      const width2 = parseFloat(document.getElementById('width2').value);
      const aspectRatio = parseFloat(document.getElementById('aspectRatio').value);
      const aspectRatio2 = parseFloat(document.getElementById('aspectRatio2').value);
      const wheelDiameter = parseFloat(document.getElementById('wheelDiameter').value);
      const wheelDiameter2 = parseFloat(document.getElementById('wheelDiameter2').value);
      const tireDiameter = wheelDiameter + 2 * (width / 25.4) * (aspectRatio / 100);
      const tireDiameter2 = wheelDiameter2 + 2 * (width2 / 25.4) * (aspectRatio2 / 100);
      const constant = 336;

      const manual6Ratios = [4.23, 2.52, 1.67, 1.23, 1, 0.83];
      const manual5Ratios = [4.2, 2.49, 1.66, 1.24, 1];
      const DCTshortRatios = [4.78, 2.933, 2.153, 1.678, 1.39, 1.203, 1];
      const DCTlongRatios = [4.806, 2.593, 1.701, 1.277, 1, 0.844, 0.671];
	  const ZF8hpRatios = [4.806, 2.593, 1.701, 1.277, 1, 0.844, 0.671, 1];
      const auto5Ratios = [3.842, 2.353, 1.529, 1, 0.839];

      const transmissionType = document.getElementById("transmissionBefore").value;
      const transmissionType2 = document.getElementById("transmissionAfter").value;

      let beforeFinalDrive = parseFloat(document.getElementById("beforeFinalDriveText").value) || parseFloat(document.getElementById("beforeFinalDrive").value);
      let afterFinalDrive = parseFloat(document.getElementById("afterFinalDriveText").value) || parseFloat(document.getElementById("afterFinalDrive").value);

      const outputBefore = document.getElementById("outputBefore");
      const outputAfter = document.getElementById("outputAfter");
      const cruisingRPMBefore = document.getElementById("cruisingRPMBefore");
      const cruisingRPMAfter = document.getElementById("cruisingRPMAfter");

      outputBefore.innerHTML = "";
      outputAfter.innerHTML = "";

      let gearRatios = transmissionType === "manual6" ? manual6Ratios : transmissionType === "DCTlong" ? DCTlongRatios : transmissionType === "DCTshort" ? DCTshortRatios : transmissionType === "auto5" ? auto5Ratios : transmissionType === "8hp" ? ZF8hpRatios : manual5Ratios;
      let gearRatios2 = transmissionType2 === "manual6" ? manual6Ratios : transmissionType2 === "DCTlong" ? DCTlongRatios : transmissionType2 === "auto5" ? auto5Ratios : manual5Ratios;

      gearRatios.forEach((gearRatio, index) => {
        let topSpeedBefore = (redline * tireDiameter) / (beforeFinalDrive * gearRatio * constant);
        outputBefore.innerHTML += `Gear ${index + 1}: ${topSpeedBefore.toFixed(2)} mph<br>`;
      });

      gearRatios2.forEach((gearRatio, index) => {
        let topSpeedAfter = (redline2 * tireDiameter2) / (afterFinalDrive * gearRatio * constant);
        outputAfter.innerHTML += `Gear ${index + 1}: ${topSpeedAfter.toFixed(2)} mph<br>`;
      });

      let highestGearRatio = gearRatios[gearRatios.length - 1];
      let highestGearRatio2 = gearRatios2[gearRatios2.length - 1];

      let cruisingRPMBeforeValue = (75 * highestGearRatio * beforeFinalDrive * constant) / tireDiameter;
      let cruisingRPMAfterValue = (75 * highestGearRatio2 * afterFinalDrive * constant) / tireDiameter2;

      cruisingRPMBefore.innerHTML = `Engine Speed at 75 mph: ${cruisingRPMBeforeValue.toFixed(2)} RPM`;
      cruisingRPMAfter.innerHTML = `Engine Speed at 75 mph: ${cruisingRPMAfterValue.toFixed(2)} RPM`;
    }
	
	function setE36M3Manual() {
      document.getElementById("transmissionBefore").value = "manual5";
      document.getElementById("redline").value = 7200;
      document.getElementById("width").value = 235;
      document.getElementById("aspectRatio").value = 40;
      document.getElementById("wheelDiameter").value = 17;
      document.getElementById("beforeFinalDrive").value = 3.23;
	  document.getElementById("transmissionAfter").value = "manual5";
      document.getElementById("redline2").value = 7200;
      document.getElementById("width2").value = 235;
      document.getElementById("aspectRatio2").value = 40;
      document.getElementById("wheelDiameter2").value = 17;
      document.getElementById("afterFinalDrive").value = 3.23;
      calculateSpeeds();
    }
	
		function setE36M3Auto() {
      document.getElementById("transmissionBefore").value = "manual5";
      document.getElementById("redline").value = 7200;
      document.getElementById("width").value = 235;
      document.getElementById("aspectRatio").value = 40;
      document.getElementById("wheelDiameter").value = 17;
      document.getElementById("beforeFinalDrive").value = 3.23;
	  document.getElementById("transmissionAfter").value = "manual5";
      document.getElementById("redline2").value = 7200;
      document.getElementById("width2").value = 235;
      document.getElementById("aspectRatio2").value = 40;
      document.getElementById("wheelDiameter2").value = 17;
      document.getElementById("afterFinalDrive").value = 3.23;
      calculateSpeeds();
    }
	
  </script>
</head>
<body onload="calculateSpeeds()">
  <h2>BMW Gear Ratio and Final Drive Calculator</h2>
  
  <table>
  <tr>
    <th>E30</th>
    <th>E36</th>
    <th>E46</th>
    <th>E90</th>

  </tr>
  <tr>
    <td><button onclick="setE36M3Manual()">E30 325i Manual</button></td>
    <td><button onclick="setE36M3Manual()">E36 M3 Manual</button></td>
    <td><button onclick="setE36M3Manual()">E46 M3 Manual</button></td>
	<td><button onclick="setE36M3Manual()">E36 318i Manual</button></td>
  </tr>
  <tr>
    <td><button onclick="setE36M3Manual()">E30 325i Auto</button></td>
    <td><button onclick="setE36M3Manual()">E36 M3 Manual</button></td>
    <td><button onclick="setE36M3Manual()">E46 M3 SMG</button></td>
	<td><button onclick="setE36M3Manual()">E36 M3 Manual</button></td>
  </tr>
  <tr>
    <td><button onclick="setE36M3Manual()">E30 325e Manual</button></td>
    <td><button onclick="setE36M3Manual()">E36 M3 Manual</button></td>
    <td><button onclick="setE36M3Manual()">E46 330i Manual</button></td>
	<td><button onclick="setE36M3Manual()">E36 M3 Manual</button></td>
  </tr>
</table>
  
   <br />
    <br />
  <button onclick="calculateSpeeds()">Recalculate</button>

  <div style="display: flex; gap: 20px;">
    <div>
      <h3>Before:</h3>
      <label for="transmissionBefore">Transmission:</label>
      <select id="transmissionBefore">
        <option value="manual6">Getrag 420G - 6 Speed Manual</option>
        <option value="manual5">5-Speed Manual (ZF S5D)</option>
        <option value="DCTlong">7-Speed DCT (Long Ratio)</option>
        <option value="DCTshort">7-Speed DCT (Short Ratio)</option>
        <option value="auto5">5-Speed Automatic</option>
		<option value="8hp">ZF 8HP</option>
      </select>
      <br />
      <label for="redline">Redline (RPM):</label>
      <input type="number" id="redline" value="7500" style="width: 6ch;" />
      <br />
      <label for="width">Rear Tire Size:</label>
      <input type="number" id="width" value="275" style="width: 3ch;" />
      <label for="aspectRatio">/</label>
      <input type="number" id="aspectRatio" value="35" style="width: 2ch;" />
      <label for="wheelDiameter">R</label>
      <input type="number" id="wheelDiameter" value="18" style="width: 2ch;" />
      <br />
      <label for="beforeFinalDrive">Final Drive Ratio:</label>
      <select id="beforeFinalDrive">
        <option value="2.79">2.79</option>
        <option value="2.93">2.93</option>
        <option value="3.07">3.07</option>
        <option value="3.15">3.15</option>
        <option value="3.23">3.23</option>
        <option value="3.38">3.38</option>
        <option value="3.46">3.46</option>
        <option value="3.64">3.64</option>
        <option value="3.73">3.73</option>
        <option value="3.85">3.85</option>
        <option value="3.91">3.91</option>
        <option value="4.10">4.10</option>
        <option value="4.27">4.27</option>
      </select>
      or custom input <input type="number" id="beforeFinalDriveText" style="width: 5ch;" />
      <h4>Top Speed Per Gear:</h4>
      <div id="outputBefore"></div>
      <h4>Cruising RPM:</h4>
      <div id="cruisingRPMBefore"></div>
    </div>
    <div>
      <h3>After:</h3>
      <label for="transmissionAfter">Transmission:</label>
      <select id="transmissionAfter">
        <option value="manual6">6-Speed Manual</option>
        <option value="manual5">5-Speed Manual (ZF S5D)</option>
        <option value="DCTlong">7-Speed DCT (Long Ratio)</option>
		<option value="DCTshort">7-Speed DCT (Short Ratio)</option>
        <option value="auto5">5-Speed Automatic</option>
		<option value="8hp">ZF 8HP</option>
      </select>
      <br />
      <label for="redline2">Redline (RPM):</label>
      <input type="number" id="redline2" value="7500" style="width: 6ch;" />
      <br />
      <label for="width2">Rear Tire Size:</label>
      <input type="number" id="width2" value="275" style="width: 3ch;" />
      <label for="aspectRatio2">/</label>
      <input type="number" id="aspectRatio2" value="35" style="width: 2ch;" />
      <label for="wheelDiameter2">R</label>
      <input type="number" id="wheelDiameter2" value="19" style="width: 2ch;" />
      <br />
      <label for="afterFinalDrive">Final Drive Ratio:</label>
      <select id="afterFinalDrive">
        <option value="2.79">2.79</option>
        <option value="2.93">2.93</option>
        <option value="3.07">3.07</option>
        <option value="3.15">3.15</option>
        <option value="3.23">3.23</option>
        <option value="3.38">3.38</option>
        <option value="3.46">3.46</option>
        <option value="3.64">3.64</option>
        <option value="3.73">3.73</option>
        <option value="3.85">3.85</option>
        <option value="3.91">3.91</option>
        <option value="4.10">4.10</option>
        <option value="4.27">4.27</option>
      </select>
      or custom input <input type="number" id="afterFinalDriveText" style="width: 5ch;" />
      <h4>Top Speed Per Gear:</h4>
      <div id="outputAfter"></div>
      <h4>Cruising RPM:</h4>
      <div id="cruisingRPMAfter"></div>
    </div>
  </div>
  <canvas id="gearChart" width="800" height="400"></canvas>
</body>
</html>
