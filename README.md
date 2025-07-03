<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>자리 뽑기</title>
  <style>
    body {
      font-family: sans-serif;
      text-align: center;
      background: #f5f5f5;
    }
    h1 {
      margin-top: 20px;
    }
    .container {
      display: flex;
      justify-content: center;
      gap: 40px;
      margin-top: 20px;
      flex-wrap: wrap;
    }
    .section {
      display: grid;
      gap: 10px;
    }
    .section1, .section2 {
      grid-template-columns: repeat(2, 60px);
      grid-template-rows: repeat(5, 60px);
    }
    .section3 {
      grid-template-columns: repeat(2, 60px);
      grid-template-rows: repeat(4, 60px);
    }
    .seat {
      background: white;
      border: 2px solid #333;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: bold;
      font-size: 16px;
    }
    button {
      margin-top: 30px;
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>🪑 자리 뽑기</h1>
  <div class="container">
    <div class="section section1" id="section1"></div>
    <div class="section section2" id="section2"></div>
    <div class="section section3" id="section3"></div>
  </div>
  <button onclick="generateSeats()">자리 다시 뽑기</button>

  <script>
    function shuffle(array) {
      for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
      }
      return array;
    }

    function generateSeats() {
      const section1 = document.getElementById('section1');
      const section2 = document.getElementById('section2');
      const section3 = document.getElementById('section3');

      section1.innerHTML = '';
      section2.innerHTML = '';
      section3.innerHTML = '';

      const numbers = shuffle([...Array(28).keys()].map(n => n + 1));

      // 1번 분단: 10명
      for (let i = 0; i < 10; i++) {
        const seat = document.createElement('div');
        seat.className = 'seat';
        seat.textContent = numbers[i];
        section1.appendChild(seat);
      }

      // 2번 분단: 10명
      for (let i = 10; i < 20; i++) {
        const seat = document.createElement('div');
        seat.className = 'seat';
        seat.textContent = numbers[i];
        section2.appendChild(seat);
      }

      // 3번 분단: 8명
      for (let i = 20; i < 28; i++) {
        const seat = document.createElement('div');
        seat.className = 'seat';
        seat.textContent = numbers[i];
        section3.appendChild(seat);
      }
    }

    // 초기 자리 배정
    generateSeats();
  </script>
</body>
</html>
