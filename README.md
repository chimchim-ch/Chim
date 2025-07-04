# Chim
Army card maker 
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ARMY Card Maker</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Parisienne&family=Quicksand:wght@400;600&display=swap');body {
  font-family: 'Quicksand', sans-serif;
  background: #fef9f8;
  color: #333;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
}
h1 {
  font-family: 'Parisienne', cursive;
  color: #c1839f;
  font-size: 2.5rem;
  margin-bottom: 20px;
}
.form-container {
  background: #fff;
  padding: 20px;
  border-radius: 20px;
  box-shadow: 0 6px 16px rgba(0,0,0,0.1);
  width: 90%;
  max-width: 400px;
  margin-bottom: 30px;
}
label {
  display: block;
  margin: 12px 0 5px;
  font-weight: 600;
}
input {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 10px;
  font-size: 1rem;
}
#card {
  width: 300px;
  background: linear-gradient(135deg, #f8e4eb, #e2f0e6);
  padding: 20px;
  border-radius: 25px;
  text-align: center;
  font-family: 'Parisienne', cursive;
  color: #8d6074;
  position: relative;
  box-shadow: 0 8px 20px rgba(0,0,0,0.15);
}
#profile-pic {
  width: 90px;
  height: 90px;
  object-fit: cover;
  border-radius: 50%;
  border: 3px solid #d7b5c4;
  margin-bottom: 15px;
}
.card-text {
  font-family: 'Quicksand', sans-serif;
  font-size: 0.9rem;
  margin: 4px 0;
}
button {
  background-color: #c1839f;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 15px;
  font-size: 1rem;
  cursor: pointer;
  margin-top: 20px;
  font-weight: 600;
}
canvas { display: none; }

  </style>
</head>
<body>
  <h1>ARMY Card Maker</h1>
  <div class="form-container">
    <label>Name</label>
    <input type="text" id="name" />
    <label>Bias</label>
    <input type="text" id="bias" />
    <label>ARMY Since</label>
    <input type="text" id="since" />
    <label>Birthday</label>
    <input type="text" id="birthday" />
    <label>MBTI</label>
    <input type="text" id="mbti" />
    <label>ARMY Level</label>
    <input type="text" id="level" />
    <label>Favorite Song</label>
    <input type="text" id="song" />
    <label>Profile Picture</label>
    <input type="file" id="imageInput" accept="image/*" />
  </div>  <div id="card">
    <img src="" id="profile-pic" alt="Profile Picture" />
    <h2 id="preview-name"></h2>
    <p class="card-text"><strong>Bias:</strong> <span id="preview-bias"></span></p>
    <p class="card-text"><strong>ARMY Since:</strong> <span id="preview-since"></span></p>
    <p class="card-text"><strong>Birthday:</strong> <span id="preview-birthday"></span></p>
    <p class="card-text"><strong>MBTI:</strong> <span id="preview-mbti"></span></p>
    <p class="card-text"><strong>ARMY Level:</strong> <span id="preview-level"></span></p>
    <p class="card-text"><strong>Favorite Song:</strong> <span id="preview-song"></span></p>
  </div><button onclick="downloadCard()">Download Card</button> <canvas id="canvas"></canvas>

  <script>
    const inputs = ['name', 'bias', 'since', 'birthday', 'mbti', 'level', 'song'];
    inputs.forEach(id => {
      document.getElementById(id).addEventListener('input', () => {
        document.getElementById('preview-' + id).textContent = document.getElementById(id).value;
      });
    });

    document.getElementById('imageInput').addEventListener('change', (e) => {
      const reader = new FileReader();
      reader.onload = function(event) {
        document.getElementById('profile-pic').src = event.target.result;
      };
      reader.readAsDataURL(e.target.files[0]);
    });

    function downloadCard() {
      html2canvas(document.getElementById("card")).then(canvas => {
        const link = document.createElement("a");
        link.download = "ARMY_ID_Card.png";
        link.href = canvas.toDataURL();
        link.click();
      });
    }
  </script>  <script src="https://cdn.jsdelivr.net/npm/html2canvas@1.4.1/dist/html2canvas.min.js"></script></body>
</html>
