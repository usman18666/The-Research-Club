<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Research Club Feedback</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f5f7fa;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .container {
      background: #ffffff;
      padding: 25px;
      border-radius: 12px;
      box-shadow: 0 6px 18px rgba(0, 0, 0, 0.15);
      width: 400px;
    }
    h2 {
      text-align: center;
      color: #2c3e50;
    }
    label {
      font-weight: bold;
      margin-top: 10px;
      display: block;
    }
    input, textarea {
      width: 100%;
      padding: 10px;
      margin: 6px 0;
      border: 1px solid #ccc;
      border-radius: 6px;
      font-size: 14px;
    }
    button {
      width: 100%;
      padding: 12px;
      background: #3498db;
      color: #fff;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      font-size: 16px;
    }
    button:hover {
      background: #2980b9;
    }
    .success {
      color: green;
      text-align: center;
      margin-top: 10px;
      font-size: 14px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>📋 Research Club Feedback</h2>
    <form id="feedbackForm">
      <label for="name">Name:</label>
      <input type="text" id="name" name="name" required>

      <label for="email">Email:</label>
      <input type="email" id="email" name="email" required>

      <label for="feedback">Your Feedback:</label>
      <textarea id="feedback" name="feedback" rows="4" required></textarea>

      <label for="suggestions">Any Suggestions?</label>
      <textarea id="suggestions" name="suggestions" rows="3"></textarea>

      <button type="submit">Submit</button>
    </form>
    <p id="responseMessage" class="success"></p>
  </div>

  <script>
    const scriptURL = "https://script.google.com/macros/s/AKfycbyOXB1xzRmeTM2mrexIO1_MJ2CN2pqPU4j-rUxYgQKMw1Mf8SegJ60HVWfBL6An730M/exec"; // Replace with your Google Apps Script Web App URL

    document.getElementById("feedbackForm").addEventListener("submit", async (e) => {
      e.preventDefault();

      const formData = {
        name: document.getElementById("name").value,
        email: document.getElementById("email").value,
        feedback: document.getElementById("feedback").value,
        suggestions: document.getElementById("suggestions").value,
      };

      try {
        await fetch(scriptURL, {
          method: "POST",
          body: JSON.stringify(formData),
        });
        document.getElementById("responseMessage").innerText = "✅ Thank you! Your feedback has been submitted.";
        document.getElementById("feedbackForm").reset();
      } catch (err) {
        alert("⚠️ Error submitting feedback. Please try again.");
      }
    });
  </script>
</body>
</html>
