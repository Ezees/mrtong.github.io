---
layout: post
title: "Image Grid Popup"
date: 2024-09-01
---


<div class="image-grid">
  <img src="path/to/image1.jpg" class="grid-image" alt="Image 1" onclick="showPopup('path/to/image1.jpg')">
  <img src="path/to/image2.jpg" class="grid-image" alt="Image 2" onclick="showPopup('path/to/image2.jpg')">
  <img src="path/to/image3.jpg" class="grid-image" alt="Image 3" onclick="showPopup('path/to/image3.jpg')">
  <img src="path/to/image4.jpg" class="grid-image" alt="Image 4" onclick="showPopup('path/to/image4.jpg')">
  <img src="path/to/image5.jpg" class="grid-image" alt="Image 5" onclick="showPopup('path/to/image5.jpg')">
  <img src="path/to/image6.jpg" class="grid-image" alt="Image 6" onclick="showPopup('path/to/image6.jpg')">
</div>

<div id="popup" class="popup" onclick="closePopup()">
  <span class="close">&times;</span>
  <img id="popup-img" class="popup-content" alt="Popup Image">
</div>

<style>
  .image-grid {
    display: grid;
    grid-template-columns: repeat(3, 100px);
    gap: 10px;
  }

  .grid-image {
    width: 100px;
    height: 100px;
    cursor: pointer;
    border: 2px solid #ccc;
  }

  .popup {
    display: none;
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.8);
    justify-content: center;
    align-items: center;
  }

  .popup-content {
    max-width: 80%;
    max-height: 80%;
  }
</style>

<script>
  function showPopup(imageSrc) {
    const popup = document.getElementById('popup');
    const popupImg = document.getElementById('popup-img');
    popupImg.src = imageSrc;
    popup.style.display = 'flex';
  }

  function closePopup() {
    document.getElementById('popup').style.display = 'none';
  }
</script>

