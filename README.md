<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Age Calculator by Alok</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap');

  body {
    background: linear-gradient(135deg, #667eea, #764ba2);
    font-family: 'Poppins', sans-serif;
    color: #f0f0f0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
  }

  h1 {
    font-weight: 700;
    font-size: 3rem;
    margin-bottom: 0.2em;
  }

  p.subtitle {
    font-weight: 400;
    font-size: 1.2rem;
    margin-bottom: 2em;
    letter-spacing: 0.05em;
    opacity: 0.8;
  }

  input[type="date"] {
    padding: 12px 20px;
    border-radius: 30px;
    border: none;
    font-size: 1rem;
    width: 250px;
    text-align: center;
    outline: none;
    margin-bottom: 1.5em;
    transition: box-shadow 0.3s ease;
  }

  input[type="date"]:focus {
    box-shadow: 0 0 8px 2px #f0f0f0;
  }

  button {
    background: #f0f0f0;
    color: #5a2d82;
    border: none;
    padding: 12px 40px;
    border-radius: 30px;
    font-weight: 700;
    font-size: 1rem;
    cursor: pointer;
    transition: background 0.3s ease;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  }

  button:hover {
    background: #dcdde1;
  }

  #result {
    margin-top: 2em;
    font-size: 1.5rem;
    font-weight: 600;
    letter-spacing: 0.02em;
  }

  .signature {
    margin-top: 4em;
    font-style: italic;
    opacity: 0.7;
    font-size: 1rem;
  }
</style>
</head>
<body>

<h1>Age Calculator</h1>
<p class="subtitle">Age by Alok</p>

<input type="date" id="dob" max="" />

<button onclick="calculateAge()">Calculate Age</button>

<div id="result"></div>

<div class="signature">Made with love by Alok</div>

<script>
  // Set max date to today (to prevent future dates)
  document.getElementById('dob').max = new Date().toISOString().split('T')[0];

  function calculateAge() {
    const dobInput = document.getElementById('dob').value;
    if (!dobInput) {
      document.getElementById('result').innerText = "Please enter your birth date.";
      return;
    }

    const dob = new Date(dobInput);
    const today = new Date();

    let years = today.getFullYear() - dob.getFullYear();
    let months = today.getMonth() - dob.getMonth();
    let days = today.getDate() - dob.getDate();

    if (days < 0) {
      months--;
      days += new Date(today.getFullYear(), today.getMonth(), 0).getDate();
    }
    if (months < 0) {
      years--;
      months += 12;
    }

    document.getElementById('result').innerText = `Alok, your age is: ${years} years, ${months} months, and ${days} days.`;
  }
</script>

</body>
</html>
