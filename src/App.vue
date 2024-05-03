<template>
  <div>
    <header>
      <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

      <div class="wrapper">
        <HelloWorld :msg="message" />
      </div>
    </header>

    <main>
      <h1>{{ pageTitle }}</h1>
      <p :class="{ 'highlight': isHighlighted }">This is a paragraph.</p>
      <input type="text" v-model="inputValue" @input="updateMessage" />

      <div class="content-box" :style="{ backgroundColor: boxColor }">
        <h2>Content Box</h2>
        <p>This is a content box.</p>
      </div>
    </main>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { RouterLink } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'

const pageTitle = ref('Welcome to My Page')
const isHighlighted = ref(false)
const message = ref('Hello Vue!')
const inputValue = ref('')
const boxColor = ref('lightblue')

const updateMessage = () => {
  message.value = inputValue.value
}


const changeBoxColor = () => {
  const colors = ['lightblue', 'lightgreen', 'lightcoral', 'lightsalmon']
  const randomIndex = Math.floor(Math.random() * colors.length)
  boxColor.value = colors[randomIndex]
}
</script>

<style scoped>
body {
  margin: 0;
  padding: 0;
  background-image: url('assets\bg.png');
  background-size: cover;
  background-repeat: no-repeat;
  width: 100vw;
  height: 100vh;
}

.content-box {
  margin-top: 2rem;
  padding: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  text-align: center;
}
header {
  line-height: 1.5;
  max-height: 100vh;
  text-align: center;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

.main {
  text-align: center;
}

.highlight {
  color: red;
}

input {
  margin-top: 1rem;
  padding: 0.5rem;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}

header, main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

/* Menengahkan navigasi */
nav {
  margin-top: 1rem;
  text-align: center;
}

/* Mengatur margin untuk kotak konten di tengah */
.content-box {
  margin-top: 1rem; 
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
  @media (orientation: portrait) {
  header {
    max-height: none; /* Menghapus batasan tinggi maksimum untuk header */
  }

  .logo {
    margin: 2rem auto; /* Menengahkan logo */
  }

  nav {
    margin-top: 1rem; /* Menurunkan navigasi sedikit */
  }

  .content-box {
    margin-top: 1rem; 
  }
}

}
</style>