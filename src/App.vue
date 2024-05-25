<template>
  <div>
    <header>
      <div class="container">
        <h1>Harmonic Apparel</h1>
        <nav>
          <ul>
            <li><a href="#home">Home</a></li>
            <li><a href="#products">Products</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#contact">Contact</a></li>
          </ul>
        </nav>
      </div>
    </header>
    <div class="q-pa-md">
    <q-carousel
      animated
      v-model="slide"
      navigation
      infinite
      :autoplay="autoplay"
      arrows
      transition-prev="slide-right"
      transition-next="slide-left"
      @mouseenter="autoplay = false"
      @mouseleave="autoplay = true"
    >
      <q-carousel-slide :name="1" img-src="/images/Logo1.png" />
      <q-carousel-slide :name="2" img-src="/images/Logo2.png" />
      <q-carousel-slide :name="3" img-src="/images/Logo3.png" />
      <q-carousel-slide :name="4" img-src="/images/Logo4.png" />
    </q-carousel>
  </div>

    <section id="home" class="hero">
      <div class="container">
        <h2>Welcome to Harmonic Apparel</h2>
        <p>Your Luxury Branded Outfits</p>
        <a href="#products" class="btn">Shop Now</a>
      </div>
    </section>

    <div class="q-pa-md row items-start q-gutter-md">
    <q-card class="my-card" flat bordered>
      <q-img
        src="/images/heskuyy.png"
      />

      <q-card-section>        
        <div class="text-h5 q-mt-sm q-mb-xs">Septia Heska</div>
        <div class="text-caption text-grey">
          CEO Harmonic Apparel
        </div>
      </q-card-section>

      

      <q-card-actions>
        <q-btn flat color="primary" label="Instagram" href="https://www.instagram.com/septiaheskaa?igsh=MTJzNGZhamQ5Zjh3OA%3D%3D&utm_source=qr"/>
        <q-btn flat color="primary" label="TikTok" href="https://www.tiktok.com/@heskuyy?_t=8lHHVzP0A6y&_r=1"/>

        <q-space />

        <q-btn
          color="grey"
          round
          flat
          dense
          :icon="expanded ? 'keyboard_arrow_up' : 'keyboard_arrow_down'"
          @click="expanded = !expanded"
        />
      </q-card-actions>

      <q-slide-transition>
        <div v-show="expanded">
          <q-separator />
          <q-card-section class="text-subtitle2">
            {{ lorem }}
          </q-card-section>
        </div>
      </q-slide-transition>
    </q-card>
  </div>

    <section id="products" class="products">
      <div class="container">
        <h2>Featured Products</h2>
        <div class="product-grid">
          <div v-for="product in products" :key="product.id" class="product-card">
            <img :src="product.image" :alt="product.name" />
            <h3>{{ product.name }}</h3>
            <p>{{ product.price }}</p>
          </div>
        </div>
      </div>
    </section>

    <section id="about" class="about">
      <div class="container">
        <h2>About Us</h2>
        <p>Our apparel is crafted from the finest materials, ensuring premium quality and ultimate comfort.</p>
      </div>
    </section>

    <section id="contact" class="contact">
      <div class="container">
        <h2>Contact Us</h2>
        <form @submit.prevent="submitForm">
          <label for="name">Name:</label>
          <input type="text" id="name" v-model="form.name" required />
          
          <label for="email">Email:</label>
          <input type="email" id="email" v-model="form.email" required />
          
          <label for="message">Message:</label>
          <textarea id="message" v-model="form.message" required></textarea>
          
          <button type="submit" class="btn">Submit</button>
        </form>
      </div>
    </section>
  </div> 
  <footer class="bg-body-tertiary text-center text-lg-start"> 
  <div class="text-center p-3" style="background-color: rgba(0, 0, 0, 0.05);">
    © 2024 Copyright
    <a class="text-body">@septiaheskaa</a>
  </div>
  <!-- Copyright -->
</footer>  
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const slide = ref(1);
    const autoplay = ref(true);
    const products = ref([
      { id: 1, name: 'BS Wear', price: 'Rp 90.000.000', image: '/src/images/brand1.png' },
      { id: 2, name: 'CnK Wear', price: 'Rp 80.000.000', image: '/src/images/brand2.png' },
      { id: 2, name: 'BW Shirt', price: 'Rp 54.500.000', image: '/src/images/brand3.png' },
      { id: 2, name: 'PM Sweater', price: 'Rp 87.500.000', image: '/src/images/brand4.png' },
      { id: 3, name: 'LW Sweater', price: 'Rp 39.000.000', image: '/src/images/brand5.png' }
    ]);

    const form = ref({
      name: '',
      email: '',
      message: ''
    });

    const submitForm = () => {
      alert(`Name: ${form.value.name}\nEmail: ${form.value.email}\nMessage: ${form.value.message}`);
      form.value.name = '';
      form.value.email = '';
      form.value.message = '';
    };

    return {
      slide,
      autoplay,
      products,
      form,
      submitForm,
      expanded: ref(false),
      lorem: 'Septia Heska, at just 20 years old, is already a CEO and a distinguished graduate from one of the worlds top universities. She holds a degree in Business Management and has studied under renowned designers.'
    };
  }
}
</script>

<style scoped>
body {
  font-family: 'Times New Roman', Times, serif, sans-serif;
  margin: 0;
  padding: 0;
  color: #333;
}

header {
  background-color: hwb(35 9% 25%);
  color: #b5a793;
  padding: 1em 0;
}

header .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1em;
}

header nav ul {
  list-style: none;
  display: flex;
  gap: 1em;
}

header nav a {
  color: #fff;
  text-decoration: none;
}

.hero {
  background: url('./images/storess.png') no-repeat center center/cover;
  color: #fff;
  text-align: center;
  padding: 5em 1em;
}

.products {
  padding: 2em 1em;
  background-color: #f9f9f9;
}

.product-grid {
  display: flex;
  gap: 1em;
  flex-wrap: wrap;
}

.product-card {
  background-color: #c89108;
  border: 1px solid #ddd;
  padding: 1em;
  flex: 1 1 calc(33.333% - 2em);
  box-sizing: border-box;
  text-align: center;
}

.product-card img {
  background-color: #c89108;
  border: 1px solid #ddd;
  max-width: 100%;
  height: auto;
}

.about, .contact {
  padding: 2em 1em;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1em;
}

.btn {
  background-color: #333;
  color: #fff;
  padding: 0.5em 1em;
  text-decoration: none;
  border-radius: 5px;
}

form label {
  display: block;
  margin: 0.5em 0 0.25em;
}

form input, form textarea {
  width: 100%;
  padding: 0.5em;
  margin-bottom: 1em;
  border: 1px solid #ddd;
  border-radius: 5px;
}

form button {
  background-color: #333;
  color: #fff;
  padding: 0.5em 1em;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
</style>
