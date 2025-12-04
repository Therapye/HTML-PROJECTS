<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/contact">Contact</RouterLink>

        <span class="divider">|</span>

        <RouterLink to="/onboarding" class="new-link"> Start App</RouterLink>
        <RouterLink to="/login" class="new-link">Login</RouterLink>
        <RouterLink to="/register" class="new-link">Register</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
/* Стилі для верхньої смуги (header) */
header {
  line-height: 1.5;
  max-height: 100vh;
  background-color: #333; /* Темний фон */
  padding: 1rem;
}

nav {
  width: 100%;
  font-size: 14px;
  text-align: center;
}

/* Стилі для самих посилань */
nav a {
  display: inline-block;
  padding: 0.5rem 1rem; /* Трохи збільшив відступи, щоб було зручніше наводити */
  color: #fff;
  text-decoration: none;
  border-left: 1px solid var(--color-border);
  
  /* --- ДОДАНО: Плавність анімації --- */
  transition: all 0.3s ease; 
}

nav a:first-of-type {
  border: 0;
}

/* --- ДОДАНО: Ефект при наведенні мишкою --- */
nav a:hover {
  color: #FF5F5F; /* Текст стає червоним (як твій логотип) */
  background-color: rgba(255, 255, 255, 0.1); /* Легкий світлий фон при наведенні */
  border-radius: 4px; /* Закруглені кути */
  cursor: pointer;
}

/* Стиль активного посилання (сторінка, на якій ти зараз) */
nav a.router-link-exact-active {
  color: #FF5F5F; 
  font-weight: bold;
  background-color: rgba(255, 95, 95, 0.1); /* Слабкий червоний фон для активної сторінки */
  border-radius: 4px;
}

.divider {
  color: gray;
  margin: 0 5px;
}

/* Стиль для нових посилань (Start App тощо) */
.new-link {
  color: #FF5F5F !important; /* Вони за замовчуванням червоні */
}

/* При наведенні на нові посилання вони стають білими */
.new-link:hover {
  color: #fff !important;
  background-color: #FF5F5F; /* Фон стає червоним */
}
</style>