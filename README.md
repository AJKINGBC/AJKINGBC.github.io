<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Command Categories</title>
  <style>
    /* Base Styling */
    :root {
      --bg-color-light: #f5f5f5;
      --bg-color-dark: #2c3e50;
      --bg-color-macos-dark: #1c1c1c;
      --text-color-light: #333;
      --text-color-dark: #ecf0f1;
      --link-color-light: #3498db;
      --link-color-dark: #3498db;
      --link-hover-color: #2ecc71;
      --button-bg-light: #3498db;
      --button-bg-dark: #2ecc71;
      --button-bg-macos-dark: #555;
      --button-text-light: #fff;
      --button-text-dark: #ecf0f1;
      --nav-bg-light: #ecf0f1;
      --nav-bg-dark: #34495e;
      --nav-bg-macos-dark: #2c2c2c;
      --nav-text-light: #333;
      --nav-text-dark: #ecf0f1;
    }

    body {
      background-color: var(--bg-color-macos-dark);
      color: var(--text-color-dark);
      transition: background-color 0.5s, color 0.5s;
      font-family: 'Courier New', Courier, monospace;
      margin: 0;
      padding: 0;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }

    .navigator {
      display: flex;
      justify-content: space-between;
      align-items: center;
      background-color: var(--nav-bg-macos-dark);
      padding: 15px;
      position: fixed;
      width: 100%;
      top: 0;
      transition: top 0.3s, background-color 0.5s;
      z-index: 1000;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    }

    .nav-menu {
      display: flex;
      gap: 15px;
    }

    .nav-item {
      color: var(--nav-text-dark);
      text-decoration: none;
      padding: 5px 10px;
      border-radius: 5px;
      transition: background-color 0.3s;
    }

    .nav-item:hover {
      background-color: rgba(255, 255, 255, 0.1);
    }

    .search-bar {
      border: none;
      border-radius: 20px;
      padding: 10px 15px;
      font-size: 16px;
      width: 200px;
      transition: width 0.3s, box-shadow 0.3s;
      background-color: rgba(255, 255, 255, 0.1);
      color: var(--text-color-dark);
    }

    .search-bar:focus {
      width: 250px;
      outline: none;
      box-shadow: 0 0 10px rgba(52, 152, 219, 0.5);
    }

    .theme-toggle {
      background-color: var(--button-bg-macos-dark);
      color: var(--button-text-dark);
      border: none;
      border-radius: 20px;
      padding: 10px 20px;
      cursor: pointer;
      font-size: 16px;
      transition: background-color 1.0s, transform 0.5s;
    }

    .theme-toggle:hover {
      background-color: var(--button-bg-dark);
      transform: scale(1.05);
    }

    .theme-options {
      display: none;
      position: absolute;
      top: 100%;
      right: 0;
      background-color: var(--nav-bg-macos-dark);
      border-radius: 5px;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    }

    .theme-option {
      display: block;
      padding: 10px 20px;
      color: var(--nav-text-dark);
      text-decoration: none;
      transition: background-color 0.3s;
    }

    .theme-option:hover {
      background-color: rgba(255, 255, 255, 0.1);
    }

    .content {
      margin-top: 80px;
      padding: 20px;
    }

    .category-button {
      background-color: var(--button-bg-macos-dark);
      color: var(--button-text-dark);
      border: none;
      border-radius: 5px;
      padding: 10px 20px;
      margin-bottom: 10px;
      cursor: pointer;
      font-size: 16px;
      transition: background-color 0.3s;
      width: 100%;
      text-align: left;
    }

    .category-button:hover {
      background-color: var(--button-bg-dark);
    }

    .category-content {
      display: none;
      background-color: rgba(255, 255, 255, 0.05);
      border-radius: 5px;
      padding: 15px;
      margin-bottom: 20px;
    }

    .link {
      text-decoration: none;
      color: var(--link-color-dark);
      transition: color 0.3s;
    }

    .link:hover {
      color: var(--link-hover-color);
    }

    .useless-button {
      background-color: var(--button-bg-macos-dark);
      color: var(--button-text-dark);
      border: none;
      border-radius: 5px;
      padding: 10px 20px;
      margin: 10px 0;
      cursor: pointer;
      font-size: 16px;
      transition: background-color 0.3s, transform 0.2s;
    }

    .useless-button:hover {
      background-color: var(--button-bg-dark);
      transform: scale(1.05);
    }

    /* Theme-specific styles */
    body.light-mode {
      --bg-color: var(--bg-color-light);
      --text-color: var(--text-color-light);
      --nav-bg: var(--nav-bg-light);
      --nav-text: var(--nav-text-light);
      --link-color: var(--link-color-light);
      --button-bg: var(--button-bg-light);
      --button-text: var(--button-text-light);
    }

    body.dark-mode {
      --bg-color: var(--bg-color-dark);
      --text-color: var(--text-color-dark);
      --nav-bg: var(--nav-bg-dark);
      --nav-text: var(--nav-text-dark);
      --link-color: var(--link-color-dark);
      --button-bg: var(--button-bg-dark);
      --button-text: var(--button-text-dark);
    }

    body.macos-dark-mode {
      --bg-color: var(--bg-color-macos-dark);
      --text-color: var(--text-color-dark);
      --nav-bg: var(--nav-bg-macos-dark);
      --nav-text: var(--nav-text-dark);
      --link-color: var(--link-color-dark);
      --button-bg: var(--button-bg-macos-dark);
      --button-text: var(--button-text-dark);
    }

    /* Apply theme */
    body.light-mode,
    body.dark-mode,
    body.macos-dark-mode {
      background-color: var(--bg-color);
      color: var(--text-color);
    }

    body.light-mode .navigator,
    body.dark-mode .navigator,
    body.macos-dark-mode .navigator {
      background-color: var(--nav-bg);
    }

    body.light-mode .nav-item,
    body.dark-mode .nav-item,
    body.macos-dark-mode .nav-item {
      color: var(--nav-text);
    }

    body.light-mode .theme-toggle,
    body.dark-mode .theme-toggle,
    body.macos-dark-mode .theme-toggle,
    body.light-mode .category-button,
    body.dark-mode .category-button,
    body.macos-dark-mode .category-button,
    body.light-mode .useless-button,
    body.dark-mode .useless-button,
    body.macos-dark-mode .useless-button {
      background-color: var(--button-bg);
      color: var(--button-text);
    }

    body.light-mode .link,
    body.dark-mode .link,
    body.macos-dark-mode .link {
      color: var(--link-color);
    }

    /* Responsive design */
    @media (max-width: 768px) {
      .navigator {
        flex-direction: column;
        align-items: flex-start;
      }

      .nav-menu {
        flex-direction: column;
        width: 100%;
      }

      .search-bar {
        width: 100%;
        margin: 10px 0;
      }

      .theme-toggle {
        width: 100%;
      }

      .theme-options {
        width: 100%;
        position: static;
        display: none;
      }
    }
  </style>
</head>
<body class="macos-dark-mode">
  <nav class="navigator">
    <div class="nav-menu">
      <a href="#" class="nav-item">Home</a>
      <a href="#" class="nav-item">Commands</a>
      <a href="#" class="nav-item">About</a>
    </div>
    <input type="text" class="search-bar" placeholder="Search commands...">
    <div class="theme-container">
      <button class="theme-toggle">Choose Theme</button>
      <div class="theme-options">
        <a href="#" class="theme-option" data-theme="light-mode">Light</a>
        <a href="#" class="theme-option" data-theme="dark-mode">Sky Blue</a>
        <a href="#" class="theme-option" data-theme="macos-dark-mode">MacOS Dark</a>
      </div>
    </div>
  </nav>

  <div class="content">
    <button class="category-button">Gemini Commands</button>
    <div class="category-content">
      <p><strong><a href="#" class="link">Link1</a></strong>: Description of Gemini Link1</p>
      <p><strong><a href="#" class="link">Link2</a></strong>: Description of Gemini Link2</p>
      <p><strong><a href="#" class="link">Link3</a></strong>: Description of Gemini Link3</p>
      <p><strong>API Key Link</strong>: <a href="#" class="link">Get API Key</a></p>
    </div>

    <button class="category-button">Other Commands</button>
    <div class="category-content">
      <p><strong><a href="#" class="link">Other Link1</a></strong>: Description of Other Link1</p>
      <p><strong><a href="#" class="link">Other Link2</a></strong>: Description of Other Link2</p>
    </div>

    <button class="useless-button">Test Tutton 1</button>
    <button class="useless-button">Test Button 2</button>
    <button class="useless-button">Test Button 3</button>
  </div>

  <script>
    // Theme Toggle Functionality
    const themeToggle = document.querySelector('.theme-toggle');
    const themeOptions = document.querySelector('.theme-options');
    const body = document.body;

    themeToggle.addEventListener('click', () => {
      themeOptions.style.display = themeOptions.style.display === 'block' ? 'none' : 'block';
    });

    document.querySelectorAll('.theme-option').forEach(option => {
      option.addEventListener('click', (e) => {
        e.preventDefault();
        body.className = option.dataset.theme;
        themeOptions.style.display = 'none';
      });
    });

    // Category Toggle Functionality
    document.querySelectorAll('.category-button').forEach(button => {
      button.addEventListener('click', () => {
        const content = button.nextElementSibling;
        content.style.display = content.style.display === 'block' ? 'none' : 'block';
      });
    });

    // Close theme options when clicking outside
    document.addEventListener('click', (e) => {
      if (!e.target.matches('.theme-toggle') && !e.target.matches('.theme-option')) {
        themeOptions.style.display = 'none';
      }
    });

    // Useless Button Functionality
    document.querySelectorAll('.useless-button').forEach(button => {
      button.addEventListener('click', () => {
        alert('This button Is Only For Test!');
      });
    });
  </script>
</body>
</html>
