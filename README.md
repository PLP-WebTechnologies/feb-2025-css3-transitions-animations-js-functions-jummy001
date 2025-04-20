# CSS3 Transitions, Animations, and Advanced JavaScript Functions

## Objectives

Create smooth CSS transitions and animations.
Use JavaScript functions for dynamic behavior.
Implement local storage for data persistence.

## Instructions
Add CSS animations to elements like buttons or images.

>[!NOTE]
> - Write a JavaScript function that:
> - Stores and retrieves user preferences using localStorage.
> - Implements an animation triggered by user actions.

## Tasks

Create a CSS animation.
Store data in localStorage.
Apply JavaScript to trigger animations.

Happy Coding! 💻✨

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Animations & LocalStorage</title>
  <style>
    :root {
      --bg-color-light: #f0f0f0;
      --bg-color-dark: #121212;
      --text-color-light: #333;
      --text-color-dark: #f9f9f9;
      --card-bg-light: white;
      --card-bg-dark: #1e1e1e;
    }

    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background-color: var(--bg-color-light);
      color: var(--text-color-light);
      transition: background-color 0.5s ease, color 0.5s ease;
    }

    body.dark-mode {
      background-color: var(--bg-color-dark);
      color: var(--text-color-dark);
    }

    .container {
      text-align: center;
      padding: 40px 20px;
    }

    .toggle-theme {
      background-color: #007bff;
      color: white;
      border: none;
      padding: 12px 24px;
      font-size: 16px;
      border-radius: 30px;
      cursor: pointer;
      transition: background-color 0.3s ease, transform 0.3s ease;
    }

    .toggle-theme:hover {
      background-color: #0056b3;
      transform: scale(1.05);
    }

    .card-container {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      margin-top: 40px;
      gap: 20px;
    }

    .card {
      width: 200px;
      padding: 20px;
      border-radius: 16px;
      background-color: var(--card-bg-light);
      box-shadow: 0 8px 16px rgba(0,0,0,0.1);
      opacity: 0;
      transform: translateY(20px);
      animation: slideIn 0.8s forwards;
    }

    body.dark-mode .card {
      background-color: var(--card-bg-dark);
      box-shadow: 0 8px 16px rgba(255,255,255,0.05);
    }

    .card:nth-child(1) { animation-delay: 0.2s; }
    .card:nth-child(2) { animation-delay: 0.4s; }
    .card:nth-child(3) { animation-delay: 0.6s; }

    @keyframes slideIn {
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>Welcome to the Fancy UI</h1>
    <button class="toggle-theme" onclick="toggleTheme()">Toggle Theme</button>

    <div class="card-container">
      <div class="card">🔥 Feature One</div>
      <div class="card">🚀 Feature Two</div>
      <div class="card">🎯 Feature Three</div>
    </div>
  </div>

  <script>
    // Toggle dark/light theme and store in localStorage
    function toggleTheme() {
      const body = document.body;
      const isDark = body.classList.toggle('dark-mode');
      localStorage.setItem('theme', isDark ? 'dark' : 'light');

      animateCards(); // Optional: reanimate on theme toggle
    }

    // Apply saved theme on load
    window.addEventListener('DOMContentLoaded', () => {
      const savedTheme = localStorage.getItem('theme');
      if (savedTheme === 'dark') {
        document.body.classList.add('dark-mode');
      }

      animateCards(); // Trigger initial animation
    });

    // Re-apply animation on cards
    function animateCards() {
      const cards = document.querySelectorAll('.card');
      cards.forEach(card => {
        card.style.animation = 'none';
        card.offsetHeight; // Reflow to reset animation
        card.style.animation = '';
        card.classList.add('slideIn');
      });
    }
  </script>

</body>
</html>
