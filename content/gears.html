---
title: Gear Ratio Calculator
---
# 

<!DOCTYPE html>
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

      const manual6Ratios = [3.794, 2.324, 1.624, 1.271, 1, 0.794];
      const auto7Ratios = [4.924, 3.194, 2.043, 1.412, 1, 0.862, 0.772];
      const auto5Ratios = [3.842, 2.353, 1.529, 1, 0.839];

      const transmissionType = document.getElementById("transmissionBefore").value;
      const transmissionType2 = document.getElementById("transmissionAfter").value;
      const beforeFinalDrive = parseFloat(document.getElementById("beforeFinalDrive").value);
      const afterFinalDrive = parseFloat(document.getElementById("afterFinalDrive").value);

      const outputBefore = document.getElementById("outputBefore");
      const outputAfter = document.getElementById("outputAfter");
      const cruisingRPMBefore = document.getElementById("cruisingRPMBefore");
      const cruisingRPMAfter = document.getElementById("cruisingRPMAfter");

      outputBefore.innerHTML = "";
      outputAfter.innerHTML = "";

      let gearRatios = transmissionType === "manual6" ? manual6Ratios : transmissionType === "auto7" ? auto7Ratios : auto5Ratios;
      let gearRatios2 = transmissionType2 === "manual6" ? manual6Ratios : transmissionType2 === "auto7" ? auto7Ratios : auto5Ratios;

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
  </script>
</head>
<body onload="calculateSpeeds()">
  <h2>BMW Gear Ratio and Final Drive Calculator</h2>
  <button onclick="calculateSpeeds()">Recalculate</button>
  <div style="display: flex; gap: 20px;">
    <div>
      <h3>Before:</h3>
      <label for="transmissionBefore">Transmission:</label>
      <select id="transmissionBefore">
        <option value="manual6">6-Speed Manual</option>
        <option value="auto7">7-Speed Automatic</option>
        <option value="auto5">5-Speed Automatic</option>
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
      <input type="number" id="wheelDiameter" value="19" style="width: 2ch;" />
      <br />
      <label for="beforeFinalDrive"> Final Drive Ratio:</label>
      <select id="beforeFinalDrive">
        <option value="3.36">3.36</option>
        <option value="3.54" selected>3.54</option>
        <option value="3.69">3.69</option>
        <option value="3.91">3.90</option>
        <option value="4.09">4.09</option>
        <option value="4.36">4.36</option>
      </select>
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
        <option value="auto7">7-Speed Automatic</option>
        <option value="auto5">5-Speed Automatic</option>
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
      <label for="afterFinalDrive"> Final Drive Ratio:</label>
      <select id="afterFinalDrive">
        <option value="3.36">3.36</option>
        <option value="3.54">3.54</option>
        <option value="3.69">3.69</option>
        <option value="3.91">3.90</option>
        <option value="4.09" selected>4.09</option>
        <option value="4.36">4.36</option>
      </select>
      <h4>Top Speed Per Gear:</h4>
      <div id="outputAfter"></div>
      <h4>Cruising RPM:</h4>
      <div id="cruisingRPMAfter"></div>
    </div>
  </div>
</body>
</html>
