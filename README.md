<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>NEC College - Subject Results</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #4497b8;
    }

    #header {
      background-color: darkviolet;
      color: #fff;
      text-align: center;
      padding: 10px;
    }

    .container {
      text-align: center;
      background-color: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
      width: 80%;
      max-width: 600px;
      margin: 20px auto;
    }

    h2 {
      color: #007BFF;
    }

    form {
      margin-bottom: 20px;
    }

    label {
      margin-right: 10px;
    }

    input {
      padding: 10px;
      border: 1px solid #ddd;
      border-radius: 5px;
      margin-bottom: 10px;
      width: 60%;
    }

    button {
      padding: 10px 15px;
      background-color: #007BFF;
      color: #fff;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    button:hover {
      background-color: #0056b3;
    }

    #result {
      margin-top: 20px;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
      border: 2px solid #007BFF;
      background-color: #87CEEB;
      border: 2px dotted black;
    }

    th, td {
      border: 2px solid #007BFF;
      padding: 8px;
      text-align: left;
      font-size: 14px;
      background-color: #87CEEB;
    }

    th {
      background-color: #007BFF;
      color: #fff;
    }

    tr:nth-child(even) {
      background-color: #f9f9f9;
    }

    tr:nth-child(odd) {
      background-color: #e6e6e6;
    }

    tr:hover {
      background-color: #d4d4d4;
    }

    #logo {
      max-width: 100%;
      height: auto;
      margin-bottom: 20px;
    }
  </style>
</head>
<body>

  <div id="header">
    <h1>NARASARAOPETA ENGINEERING COLLEGE (Autonomous)</h1>
    <p style="color:white;">Kotappakonda Rd, Narasaraopeta, Andhra Pradesh 522601</p>
  </div>
  
  <div class="container">
    <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRc4SgtUOy1CagqoaQt37OIcISQF_pqY1batg&usqp=CAU" alt="NEC College Logo" id="logo">
    <h2>(2-2) Semester Results</h2>
    <form id="resultForm">
      <label for="rollNumber">Enter HT Number :</label>
      <input type="text" id="rollNumber" name="rollNumber" required>
      <button type="button" onclick="generateResults()">Get Results</button>
    </form>
    <div id="result"></div>
  </div>

  <script>
    const students = {
      "22471A1201": "ADAKA JAGAPATHI",
      "22471A1202": "ADIPUDI WIJAYA WANI",
      "22471A1203": "AINALA MALLIKAR JUN",
      "22471A1204": "ALUGULA EMINEJAR",
      "22471A1205": "ANUMULA VIJAYA ARCHITHA",
      "22471A1206": "BANDARUPALLI VENKATESWARLU",
      "22471A1207": "BHUVANESWARI BANDARU",
      "22471A1208": "BODA ESWAR",
      "22471A1209": "CHIMATA NANDA KISHOR",
      "22471A1210": "CHINTHAKUNTA VHSL DURGA POOJITHA",
      "22471A1211": "DASARI NAGESWARI",
      "22471A1212": "DASARI SRI SARAN",
      "22471A1213": "ELAPROLU VAMSI VARMA",
      "22471A1214": "GADDAM SANTHI",
      "22471A1215": "GATTA SADVIKA LAKSHMI",
      "22471A1217": "GUDUGUNTLA LOKESH",
      "22471A1218": "GUNJI SUNEETHA",
      "22471A1219": "IMMADISETTY SUBBARAO",
      "22471A1220": "KANJULA SUPRAJA",
      "22471A1222": "KOLLI VENKATA SAI BHAVANI",
      "22471A1223": "KOMMATHOTI MARY",
      "22471A1224": "KOPPULA SANGEETHA",
      "22471A1225": "KOTHA ANJANI",
      "22471A1226": "KURRA TIRUMALA",
      "22471A1227": "MAHANKALI MEGHANA",
      "22471A1228": "MARELLA GOPI KRISHNA",
      "22471A1229": "MEKALA KARTHIK",
      "22471A1230": "MERAJOTH BALA KRISHNA NAIK",
      "22471A1231": "MIRIYALA MOHAN SIVA PRASAD",
      "22471A1232": "MULLAMURI SRILATHA",
      "22471A1233": "MUMMANA VEERA VENKATA DURGA PRAKASH",
      "22471A1234": "MURARI RADHIKA",
      "22471A1235": "NAGALINGAM PHANI ROHITH",
      "22471A1236": "NIDAMANURI VENU",
      "22471A1237": "PALLAPATI VENKATESH",
      "22471A1238": "PANITHAM MADHAVI",
      "22471A1239": "PAPANA YALAMANDARAO",
      "22471A1240": "PATHAN RASHEED",
      "22471A1241": "POKALA RENU SREE",
      "22471A1242": "PRATHI PATI ANANDA RAJU",
      "22471A1243": "SANGEETH KUMAR KOTTI",
      "22471A1244": "SHAIK APPAPURAM FIROZ",
      "22471A1245": "SHAIK ISMAIL",
      "22471A1246": "SHAIK JAYNUL IRSHAD",
      "22471A1247": "SHAIK MINNEKALLU MEHARUNNISA",
      "22471A1248": "SHAIK NAGOOR VALI",
      "22471A1249": "SHAIK SAIDAVALI",
      "22471A1250": "SHAIK SHABEENA",
      "22471A1251": "SHAIK SHABNAM",
      "22471A1252": "SIDDARAPU CHINA BAJI",
      "22471A1253": "THIRUMALASETTY NAGA KALYAN",
      "22471A1254": "THOKA NARENDRA",
      "22471A1255": "THUMMALAGUNTA SOWJANYA",
      "22471A1256": "TURAKA ANANDA BABU",
      "22471A1257": "YALAGALA SAMBASIVARAO",
      "22471A1258": "YAMALA RAJYA LAKSHMI",
      "22471A1259": "GUVVALA THRINADH MAHESH",
      "22471A1260": "KOLAGATLA VENKATA SUBBA REDDY",
      "22471A1261": "SHAIK MOHAMMAD AASHIK",
      "22471A1262": "DUGGEMPUDI ANJI REDDY",
      "22471A1263": "BETHA MADHAVA REDDY",
      "22471A1264": "SANDIREDDY PURNA GOPI KRISHNA",
      "23475A1201": "SHAIK KUNDURTHI KHASIM",
      "23475A1202": "KATTULA SASIDHAR SAI",
      "23475A1203": "SHAIK USMAN SHARIF",
      "23475A1204": "KORA MOUNISH",
      "23475A1205": "MYSORE SAITEJA",
      "23475A1206": "YARRAMSETTI SRIKIRAN SAI"
    };
function generateResults() {
  var rollNumber = document.getElementById("rollNumber").value.trim();
  if (!isValidRollNumber(rollNumber)) {
    alert("Please enter a valid HT number (e.g., 22471A1201).");
    return;
  }

  var studentName = students[rollNumber] || "Unknown Student";

  var subjects = [
    "Technical and Communicative English - II",
    "Database Management Systems",
    "Software Engineering",
    "Design Analysis of Algorithms",
    "Computer Networks",
    "Database Management Systems Lab",
    "Mobile Application Development Lab",
    "SE and UML Lab",
    "Artificial Intelligence Tools"
  ];

  var subjectCodes = [
    "R20BSH-TCE02",
    "R20DBS-DMS",
    "R20SE-SWE",
    "R20DAA-DAA",
    "R20CN-CNET",
    "R20DBL-DMSLAB",
    "R20MAL-MADLAB",
    "R20SEU-SEULAB",
    "R20AIT-AIT"
  ];

  var credits = [3, 3, 3, 3, 3, 1.5, 1.5, 1.5, 1.5];
  var resultContainer = document.getElementById("result");

  resultContainer.innerHTML = "";

  var tableHTML = "<h3>Results for " + studentName + "</h3>";
  tableHTML += "<table><tr><th>Subject Code</th><th>Subject</th><th>Grades</th><th>Points</th><th>Credits</th></tr>";

  for (var i = 0; i < subjects.length; i++) {
    var subjectCredits = credits[i];
    var subjectResult;

    if (subjectCredits === 1.5) {
      subjectResult = Math.random() < 0.5 ? 10 : 9; // Points 9 or 10 for 1.5 credits
    } else {
      subjectResult = Math.floor(Math.random() * 6) + 5; // Points 5 to 10 for 3 credits
    }

    var grade = calculateGrade(subjectResult);

    var bgColor = i % 2 === 0 ? '#e6e6e6' : '#f9f9f9';

    tableHTML += "<tr style='background-color:" + bgColor + "'>";
    tableHTML += "<td>" + subjectCodes[i] + "</td>";
    tableHTML += "<td>" + subjects[i] + "</td>";
    tableHTML += "<td>" + grade + "</td>";
    tableHTML += "<td>" + subjectResult + " points</td>";
    tableHTML += "<td>" + subjectCredits + " credits</td>";
    tableHTML += "</tr>";
  }

  tableHTML += "</table>";
  resultContainer.innerHTML += tableHTML;
}

function isValidRollNumber(rollNumber) {
  var rollNumberPattern = /^(22471A12|23475A12)(0[1-9]|[1-6]\d|70)$/;
  return rollNumberPattern.test(rollNumber);
}

function calculateGrade(points) {
  if (points === 10) return 'A+';
  else if (points === 9) return 'A';
  else if (points === 8) return 'B';
  else if (points === 7) return 'C';
  else if (points === 6) return 'D';
  else if (points === 5) return 'E';
  else return 'F';
}


    function isValidRollNumber(rollNumber) {
      var rollNumberPattern = /^(22471A12|23475A12)(0[1-9]|[1-6]\d|70)$/;
      return rollNumberPattern.test(rollNumber);
    }

    function calculateGrade(points) {
      if (points === 10) return 'A+';
      else if (points === 9) return 'A';
      else if (points === 8) return 'B';
      else if (points === 7) return 'C';
      else if (points === 6) return 'D';
      else if (points === 5) return 'D';
      else return 'F';
    }
  </script>
  
  <div class="container">
    <h1>Contact Us</h1>
    <p style="color:green">For More Queries</p>
    <div id="contactDetails">
      <p>Email: <a href="mailto:yalamandap6@gmail.com">yalamandap6@gmail.com</a></p>
      <p>Phone: 6301932724</p>
    </div>
  </div>

</body>
</html>
