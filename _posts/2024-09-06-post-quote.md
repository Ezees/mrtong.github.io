---
layout: post
title: "Post: Quote"
categories:
  - Blog
tags:
  - Post Formats
  - quote
---

> Only one thing is impossible for God: To find any sense in any copyright law on the planet.
  
> <cite><a href="https://jawolaray.blogspot.com/">Blogspot</a></cite>

\assets\images
<div class="image-grid">
  <img src="assets/images/gif-box.jpg" class="grid-image" alt="Image 1" onclick="showPopup('/assets/images/gif-box.jpg')">
  <img src="assets/images/gif-box.jpg" class="grid-image" alt="Image 2" onclick="showPopup('/assets/images/bio-photo.png')">
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