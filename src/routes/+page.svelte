<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Ski Club</title>
<style>
  body {
    margin: 0;
    height: 100vh;
    background: linear-gradient(135deg, #1e1e1e 0%, #121212 70%);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    color: #fca311;
  }
  .welcome-box {
    background-color: #2f3437;
    border: 2px solid #6c757d;
    padding: 3rem 4rem;
    border-radius: 16px;
    box-shadow: 0 0 15px 4px rgba(173, 216, 230, 0.5);
    text-align: center;
    max-width: 400px;
    margin-bottom: 2rem;
  }
  h1 {
    margin: 0;
    font-size: 3rem;
    font-weight: 900;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    text-shadow: 0 0 10px #fca311aa, 0 0 20px #fca31177;
  }
  .carousel {
    position: relative;
    width: 400px;
    height: 250px;
    border-radius: 12px;
    overflow: hidden;
    border: 2px solid #6c757d;
    box-shadow: 0 0 15px 4px rgba(173, 216, 230, 0.3);
  }
  .carousel img {
    position: absolute;
    width: 100%;
    height: 100%;
    object-fit: cover;
    opacity: 0;
    transition: opacity 1s ease-in-out;
  }
  .carousel img.active {
    opacity: 1;
    z-index: 1;
  }
</style>
</head>
<body>
  <div class="welcome-box">
    <h1>Welcome to RIT Alpine Ski Club!</h1>
  </div>

  <div class="carousel" aria-label="Ski Club photo carousel">
    <img src="https://images.unsplash.com/photo-1512820790803-83ca734da794?auto=format&fit=crop&w=800&q=80" alt="Snowy mountain peak" class="active" />
    <img src="https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=800&q=80" alt="Skiers on a slope" />
    <img src="https://images.unsplash.com/photo-1483683804023-6ccdb62f86ef?auto=format&fit=crop&w=800&q=80" alt="Snow-covered trees" />
  </div>

<script>
  const images = document.querySelectorAll('.carousel img');
  let current = 0;
  const total = images.length;

  function rotateImages() {
    images[current].classList.remove('active');
    current = (current + 1) % total;
    images[current].classList.add('active');
  }

  setInterval(rotateImages, 4000); // Change image every 4 seconds
</script>
</body>
</html>
