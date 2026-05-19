<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Click Here</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@800&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #f5f4f0;
      font-family: 'Syne', sans-serif;
    }

    .wrap {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 2rem;
      padding: 3rem 2rem;
      text-align: center;
    }

    .label {
      font-size: 13px;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: #888;
      font-family: sans-serif;
    }

    .btn {
      font-family: 'Syne', sans-serif;
      font-size: clamp(3rem, 12vw, 7rem);
      font-weight: 800;
      color: #111;
      text-decoration: none;
      line-height: 1;
      padding: 0.2em 0.5em;
      border: 3px solid #111;
      border-radius: 6px;
      position: relative;
      display: inline-block;
      transition: background 0.18s, color 0.18s, transform 0.15s;
      cursor: pointer;
    }

    .btn:hover {
      background: #111;
      color: #f5f4f0;
      transform: scale(1.03);
    }

    .btn:active {
      transform: scale(0.97);
    }

    .arrow {
      font-size: 0.55em;
      vertical-align: middle;
      margin-left: 0.15em;
      display: inline-block;
      transition: transform 0.18s;
    }

    .btn:hover .arrow {
      transform: translate(4px, -4px);
    }

    .hint {
      font-size: 13px;
      color: #aaa;
      font-family: monospace;
      word-break: break-all;
    }
  </style>
</head>
<body>
  <div class="wrap">
    <span class="label">tap to visit</span>
    <a
      class="btn"
      href="https://ishtiaq-chatbot-613594729885.asia-southeast1.run.app"
      target="_blank"
      rel="noopener noreferrer"
    >
      Click Here<span class="arrow">↗</span>
    </a>
    <span class="hint">ishtiaq-chatbot-613594729885.asia-southeast1.run.app</span>
  </div>
</body>
</html>
