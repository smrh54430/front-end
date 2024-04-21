<script setup>
import { ref } from 'vue';


const databaseItems = ref([]);

const requestOptions = {method: 'GET',};

fetch('https://front-end-7a266-default-rtdb.europe-west1.firebasedatabase.app/indhold.json', requestOptions)
  .then(response => response.json())
  .then(data => {
    databaseItems.value = data;
    console.log(databaseItems.value);

  })
  .catch(error => {
    console.error('Error:', error);

  });
  
</script>

<template>
<div class="header"> 
    <p>Tlf: +45 40 19 49 54</p>
</div>
<div class="main-container">
  <div class="container-en">
    <div class="profile">
      <img src="../assets/profilbilled.webp" alt="close up">
      <h3>Cecilie Mackeprang</h3>
      <p>Content Creator, Personlig Stylist & Konsulent</p>
    </div>
    <div class="social-links">
      <div class="link">
        <a href="https://www.instagram.com/ps.cecilie/"> 
          <h2>Instagram</h2>
          <img src="../assets/instagram.png" alt="instagram logo">
        </a>
      </div>
      <div class="link">
        <a href="https://www.pscecilie.dk/">
          <h2>PScecilie</h2> 
          <img src="../assets/website.webp" alt="hjemmeside logo"> 
        </a>
      </div>  
    </div>
  </div>
  <div class="container-to">
    <div class="om-mig">
      <h1>Lidt om mig...</h1>
      <p>Jeg har mere end 15 års erfaring indenfor tøjbranchen og er oprindelig uddannet tekstil- og beklædningshåndværker med speciale i design. Jeg har blandt andet arbejdet som Visuel Merchandiser i butikker som Bestseller, Envii og Samsøe Samsøe. 
          De sidste par år har jeg arbejdet som Personlig Shopper hos Magasin, men er nu gået selvstændig. 
          Jeg glæder mig til at vise dig en masse tips, tricks og personlighed.</p>
      <div class="database-container">
        <div class="database-items">
          <div v-for="(item, index) in databaseItems" :key="index" class="database-item">
            <h2>{{ item.title }}</h2>
            <div class="image-boxes">
              <div v-for="(billede, billedeIndex) in item.billeder" :key="billedeIndex" class="image-box">
                <div class="image-wrapper">
                  <img :src="billede.billede" :alt="'Billede' + (billedeIndex + 1)">
                  <p>{{ billede.billedtekst }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>



 <h2>Kontakt mig for en uforpligtende samtale!</h2>
    <form id="contact-form">
      <label for="name">Navn:</label>
      <input type="text" id="name" name="name" required>
      <label for="email">Email:</label>
      <input type="email" id="email" name="email" required>
      <label for="message">Besked:</label>
      <textarea id="message" name="message" rows="4" required></textarea>
      <button type="submit">Send</button>
    </form>
  </template>
  
 
