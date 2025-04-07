<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Tên Game</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap" rel="stylesheet"/>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Inter', sans-serif;
      background: linear-gradient(to bottom, #0f0f0f, #1f1f1f);
      color: #fff;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 20px;
    }
    img.logo {
      max-width: 200px;
      margin-bottom: 30px;
    }
    h1 {
      font-size: 2.5rem;
      margin-bottom: 10px;
    }
    p.description {
      font-size: 1.1rem;
      color: #ccc;
      margin-bottom: 40px;
      max-width: 600px;
    }
    a.download-button {
      background-color: #00c853;
      color: white;
      text-decoration: none;
      padding: 15px 30px;
      border-radius: 8px;
      font-weight: bold;
      transition: background-color 0.3s;
    }
    a.download-button:hover {
      background-color: #00b34f;
    }
    footer {
      position: absolute;
      bottom: 20px;
      font-size: 0.9rem;
      color: #666;
    }
    @media (max-width: 600px) {
      h1 {
        font-size: 2rem;
      }
      .description {
        font-size: 1rem;
      }
    }
  </style>
</head>
<body>

  <img src="https://via.placeholder.com/200x200.png?text=Logo" alt="Game Logo" class="logo" />

  <h1>Tên Game Của Bạn</h1>
  <p class="description">Game chiến thuật phòng thủ kịch tính, đơn giản nhưng gây nghiện! Bắt đầu cuộc chiến sinh tồn ngay hôm nay!</p>
  
  <a href="https://play.google.com" class="download-button">Tải trên Google Play</a>

  <footer>© 2025 Tên Studio của bạn</footer>

</body>
</html>
