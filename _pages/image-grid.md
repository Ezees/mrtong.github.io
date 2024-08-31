---
layout: default
title: Image Grid
---



<style>
  .image-grid {
    display: grid;
    grid-template-columns: repeat(3, 100px);
    gap: 10px;
    margin: 20px;
  }
  .image-grid img {
    width: 100px;
    height: 100px;
    cursor: pointer;
    transition: transform 0.3s;
  }
  .image-grid img:hover {
    transform: scale(1.05);
  }
  .popup {
    display: none;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: white;
    border: 2px solid #ccc;
    padding: 20px;
    z-index: 999;
  }
  .popup img {
    max-width: 100%;
    height: auto;
  }
  .overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.7);
    display: none;
    z-index: 998;
  }
</style>

<div class="image-grid">
  {% for img in site.data.images %}
    <img src="{{ img.url }}" alt="{{ img.alt }}" onclick="showPopup('{{ img.url }}')">
  {% endfor %}
</div>

<div class="overlay" onclick="hidePopup()"></div>
<div class="popup" id="popup">
  <img id="popup-image" src="" alt="">
</div>

<script>
  function showPopup(src) {
    document.getElementById('popup-image').src = src;
    document.getElementById('popup').style.display = 'block';
    document.querySelector('.overlay').style.display = 'block';
  }

  function hidePopup() {
    document.getElementById('popup').style.display = 'none';
    document.querySelector('.overlay').style.display = 'none';
  }
</script>
