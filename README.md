<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>My Age</title>

<style>
  body {
    margin: 0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background: transparent;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  }

  .card {
    padding: 28px 36px;
    border-radius: 16px;
    background: #ffffff;
    box-shadow: 0 8px 25px rgba(0,0,0,0.12);
    text-align: center;
    min-width: 220px;
  }

  .title {
    font-size: 14px;
    letter-spacing: 1px;
    color: #777;
    margin-bottom: 8px;
    text-transform: uppercase;
  }

  .age {
    font-size: 26px;
    font-weight: 600;
    color: #111;
  }
</style>
</head>

<body>

<div class="card">
  <div class="title">My Age</div>
  <div class="age" id="age"></div>
</div>

<script>
  const birthDate = new Date("2000-02-25");

  function updateAge() {
    const now = new Date();

    let years = now.getFullYear() - birthDate.getFullYear();
    let months = now.getMonth() - birthDate.getMonth();
    let days = now.getDate() - birthDate.getDate();

    if (days < 0) {
      months--;
      const lastMonth = new Date(now.getFullYear(), now.getMonth(), 0);
      days += lastMonth.getDate();
    }

    if (months < 0) {
      years--;
      months += 12;
    }

    document.getElementById("age").textContent =
      `${years} years ${months} months ${days} days`;
  }

  updateAge();
  setInterval(updateAge, 1000 * 60 * 60);
</script>

</body>
</html>
