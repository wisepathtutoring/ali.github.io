# ali.github.io



<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Google Script Tool</title>
</head>
<body>
  <h1>Submit Your Data</h1>
  <form id="myForm">
    <input type="text" name="name" placeholder="Your Name" required><br>
    <input type="email" name="email" placeholder="Your Email" required><br>
    <textarea name="message" placeholder="Your Message" required></textarea><br>
    <button type="submit">Submit</button>
  </form>

  <p id="response"></p>

  <script>
    document.getElementById('myForm').addEventListener('submit', function(e) {
      e.preventDefault();
      const formData = new FormData(e.target);
      const data = {
        name: formData.get('name'),
        email: formData.get('email'),
        message: formData.get('message')
      };

      fetch('https://script.google.com/macros/s/AKfycbxpePW_gSZj_Bhzi1WgkbtIrO0Bc3XiQ4z1ocf8njwD4cqMq1G50zhD5xsi_qTTqZiR/exec', {
        method: 'POST',
        body: JSON.stringify(data),
        headers: { 'Content-Type': 'application/json' }
      })
      .then(res => res.json())
      .then(res => {
        document.getElementById('response').innerText = 'Data Submitted Successfully!';
      })
      .catch(err => {
        document.getElementById('response').innerText = 'Error submitting data';
      });
    });
  </script>
</body>
</html>
