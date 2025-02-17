<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>밤이네 하루하루</title>
    <style>
        body {
            font-family: 'Noto Serif KR', serif;
            font-weight: bold;
            margin: 0;
            padding: 0;
            text-align: center;
            background: linear-gradient(to bottom, #fff7f1, #f9e0c9, #e6b89c);
            transition: background 0.5s ease;
        }
        .container {
            width: 80%;
            margin: 0 auto;
            padding: 20px;
        }
        .navbar {
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 15px;
            background: rgba(255, 255, 255, 0.9);
            box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
            position: fixed;
            width: 100%;
            top: 0;
            left: 0;
            z-index: 1000;
            backdrop-filter: blur(10px);
        }
        .navbar a {
            text-decoration: none;
            color: black;
            margin: 0 20px;
            font-weight: bold;
            font-size: 18px;
            cursor: pointer;
            transition: color 0.3s ease, transform 0.3s ease;
        }
        .navbar a:hover {
            color: #d94b2b;
            transform: scale(1.1);
        }
        #sakuraCanvas {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        pointer-events: none; 
        z-index: 0; 
    }
    .main-content {
        position: relative; 
        overflow: hidden; 
    }
        .main-content {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            min-height: 60vh; 
            padding-top: 80px;
        }
        .main-content h1 {
            font-size: 48px;
            font-weight: bold;
            color: #5a4033;;
            animation: fadeIn 1s ease-in-out;
        }
        .main-content p {
            max-width: 600px;
            font-size: 20px;
            font-weight: bold;
            color: #666;
            animation: fadeIn 1.5s ease-in-out;
            line-height: 1.8;
        }
        .btn {
            margin-top: 20px;
            padding: 14px 30px;
            border: none;
            border-radius: 30px;
            background: #ff5733;
            color: white;
            cursor: pointer;
            font-size: 18px;
            font-weight: bold;
            transition: background 0.3s, transform 0.3s;
        }
        .btn:hover {
            background: #d94a2b;
            transform: scale(1.1);
        }
            .gallery {
            background: #f8d7b9;
            padding: 40px;
            display: grid;
            grid-template-columns: repeat(3, minmax(150px, 1fr)); gap: 20px; padding: 20px; align-items: center; justify-items: center;
            gap: 80px 1cm;
            justify-content: center;
            max-width: 95%;
            margin: auto;
            border-radius: 15px;
        }
        .gallery img {
            width: 100%;
            height: auto;
            object-fit: cover;
            border-radius: 15px;
            box-shadow: 2px 4px 8px rgba(0, 0, 0, 0.2); margin: 0; padding: 10px;
            cursor: pointer;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .gallery img:hover {
            box-shadow: 6px 6px 15px rgba(0, 0, 0, 0.3);
        }
        .popup {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            justify-content: center;
            align-items: center;
        }
        .popup-content {
            background: white;
            padding: 20px;
            border-radius: 10px;
            position: relative;
            max-width: 500px;
            text-align: center;
            box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.3);
        }
        .popup .close {
            position: absolute;
            top: 10px;
            right: 10px;
            font-size: 10px;
            font-weight: bold;
            cursor: pointer;
            color: #d94b2b;
            background: white;
            padding: 5px 5px;
            border-radius: 50%;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
            transition: transform 0.2s ease, background 0.2s ease;
        }
            .popup .close:hover {
            background: #ff6650;
            color: white;
            transform: scale(1.1);
        }
        .popup img {
            width: 80%;
            height: auto;
            border-radius: 10px;
        }
        .popup img {
        width: 100%;
        max-width: 800px;
        height: auto;
        transition: transform 0.3s ease-in-out;
        cursor: zoom-in;
        }
        .popup img.enlarged {
        transform: scale(1.5);
        cursor: zoom-out;
        }
@media screen and (max-width: 430px) {
    .container {
        width: 95%;
    }
    .main-content {
        min-height: 70vh;
    }
    .gallery {
        grid-template-columns: repeat(2, 1fr);
        gap: 10px;
        padding: 10px;
    }
    .gallery img {
        width: 100%;
        height: auto;
    }
}
    }
            .container {
                width: 95%;
            }
            .main-content {
                min-height: 70vh;
            }
            .gallery {
                margin-top: 20px;
            }
            .gallery img {
                width: 70%;
                margin: auto;
            }
    }
            .container {
                width: 95%;
            }
            .main-content {
                min-height: 70vh;
            }
            .gallery {
                margin-top: 20px;
            }
        }

    </style>
</head>
<body>
<div class="container">
    <div class="navbar">
        <a onclick="showTextPopup('이곳은 밤이와 하루의 소중했던 순간순간을 간직한 공간이기도, 기억 속 따뜻한 시간들을 담아둔 작은 보금자리이기도 합니다.')">About</a>
        <a onclick="showTextPopup('이곳엔 순간의 떨림과 설렘, 마음 가득한 사랑이 담겨 있습니다. 직접 담아낸 추억의 조각들을 만나보세요.')">Feature</a>
        <a onclick="showTextPopup('느리고 긴 호흡의 대화를 나누고 싶으시다면 언제나 환영합니다. 편하게 연락 주세요. (nec_8@naver.com)')">Contact</a>
    </div>
    <div class="main-content">
        <canvas id="sakuraCanvas"></canvas>
        <p>그 순간, 그 따뜻함을 기억하며</p>
        <h1>시간의 흐름 속에서 피어난 이야기</h1>
        <p>"추억이 쌓이고 감정이 머무는 곳, <br>제 아이들의 소중한 시간들이 머문 자리입니다."</p>
        <button class="btn" onclick="showImagePopup()">Others</button>
    </div>
</div>
<div class="popup" id="text-popup">
    <div class="popup-content">
        <span class="close" onclick="closePopup('text-popup')">&times;</span>
        <p id="popup-text"></p>
    </div>
</div>
<div class="popup" id="image-popup">
    <div class="popup-content">
        <span class="close" onclick="closePopup('image-popup')">&times;</span>
        <p>찰나의 순간을 소중히 담으려 노력하였습니다.</p>
        <img src="https://i.imgur.com/pfa4pfQ.jpeg" alt="More View Image">
    </div>
</div>
<script>
    function showTextPopup(text) {
      document.getElementById("popup-text").innerText = text;
      document.getElementById("text-popup").style.display = "flex";
    }
    function showImagePopup() {
      document.getElementById("image-popup").style.display = "flex";
    }
    function closePopup(id) {
      document.getElementById(id).style.display = "none";
    }
    document.getElementById("gallery-popup").addEventListener("click", function(event) {
        if (event.target === this) {
            closePopup("gallery-popup");
        }
    });
    document.getElementById("popup-img").addEventListener("click", function() {
      this.classList.toggle("enlarged");
    });


</script>

<div class="gallery">
    <img src="https://i.imgur.com/jBzlWAF.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/clDycMf.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/S0PpUXe.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/E29d3B3.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/YNXh19x.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/rOJh1us.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/mQuCuEQ.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/L7pUqRk.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/vxS3HFO.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/wwQmTvR.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/mwDDrix.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/wv9UVAo.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/CBrGVWn.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/C2zcw1v.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/pAnsKrj.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/mefVLwd.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/WtsE9X3.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/OCd385s.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/lYWGNWw.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/SIowbe4.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/FEbk8Me.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/PimMS4W.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/VMCD84V.jpeg" onclick="showGalleryPopup(this.src)">
    <img src="https://i.imgur.com/cQm2van.jpeg" onclick="showGalleryPopup(this.src)">
</div>
<div class="popup" id="gallery-popup">
    <div class="popup-content">
        <span class="close" onclick="closePopup('gallery-popup')">&times;</span>
        <img id="popup-img" src="" alt="Gallery Image">
    </div>
</div>
<script>
    function showGalleryPopup(src) {
        document.getElementById("popup-img").src = src; 
        document.getElementById("gallery-popup").style.display = "flex"; 
    }
    function closePopup(id) {
        document.getElementById(id).style.display = "none"; 
    }
</script>
</html>
</title>
</head>
<body>
<script>
    const canvas = document.getElementById("sakuraCanvas");
    const ctx = canvas.getContext("2d");

    
    function setCanvasSize() {
      const mainContent = document.querySelector(".main-content");
      canvas.width = mainContent.clientWidth;
      canvas.height = mainContent.clientHeight;
    }

    
    setCanvasSize();

    
    window.addEventListener("resize", setCanvasSize);

    
    const petals = [];
    const petalCount = 25; // 벚꽃 잎 개수

    class Petal {
      constructor() {
          this.x = Math.random() * canvas.width;
          this.y = Math.random() * canvas.height;
          this.size = Math.random() * 6 + 3;
          this.speedX = Math.random() * 1 - 0.5;
          this.speedY = Math.random() * 2 + 1;
          this.angle = Math.random() * Math.PI * 2;
          this.spin = Math.random() * 0.02;
          this.opacity = Math.random() * 0.7 + 0.3;
      }

      update() {
          this.x += this.speedX;
          this.y += this.speedY;
          this.angle += this.spin;

          if (this.y > canvas.height) {
              this.y = -10;
              this.x = Math.random() * canvas.width;
          }
      }

      draw() {
          ctx.fillStyle = `rgba(255, 182, 193, ${this.opacity})`; 
          ctx.beginPath();
          ctx.ellipse(this.x, this.y, this.size, this.size / 2, this.angle, 0, Math.PI * 2);
          ctx.fill();
      }
    }

    
    for (let i = 0; i < petalCount; i++) {
      petals.push(new Petal());
    }

   
    function animate() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      for (const petal of petals) {
          petal.update();
          petal.draw();
      }
      requestAnimationFrame(animate);
    }

    animate();
</script>


<audio id="bg-music" loop>
    <source src="./assets/audio/background-music.mp3" type="audio/mp3">
</audio>

<script>
    document.addEventListener("DOMContentLoaded", function() {
        const audio = document.getElementById("bg-music");

        audio.volume = 0.8;  

       
        function enableAudioPlayback() {
            audio.play().then(() => {
                console.log("배경 음악 자동 재생 성공");
                document.removeEventListener("click", enableAudioPlayback);
                document.removeEventListener("scroll", enableAudioPlayback);
                document.removeEventListener("mousemove", enableAudioPlayback);
            }).catch(error => console.log("자동 재생 차단됨:", error));
        }

       
        document.addEventListener("click", enableAudioPlayback);
        document.addEventListener("scroll", enableAudioPlayback);
        document.addEventListener("mousemove", enableAudioPlayback);
    });
</script>
<footer>
    <p>© 2025 밤이네 하루하루 | Designed with Nchae</p>
</footer>
</body>
</html>
