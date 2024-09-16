<template>
  <div>
    <div v-if="isMobile">
      <div class="menu-toggle-wrap">
        <button class="menu-toggle" @click="toggleMobileMenu">
          <span class="material-symbols-outlined">{{
            is_expanded
              ? "keyboard_double_arrow_left"
              : "keyboard_double_arrow_right"
          }}</span>
        </button>
      </div>
    </div>
    <div v-else>
      <aside :class="`${is_expanded ? 'is-expanded' : ''}`">
        <div class="logo">
          <img :src="require('../assets/logo.png')" alt="Vue" />
        </div>
        <div class="menu-toggle-wrap">
          <button class="menu-toggle" @click="ToggleMenu">
            <span class="material-symbols-outlined">{{
              is_expanded
                ? "keyboard_double_arrow_left"
                : "keyboard_double_arrow_right"
            }}</span>
          </button>
        </div>
        <h3>Menu</h3>
        <div class="menu">
          <router-link to="/atendimento" class="button">
            <span class="material-symbols-outlined">forum</span>
            <span class="text">Atendimento</span>
          </router-link>
          <router-link to="/contatos" class="button">
            <span class="material-symbols-outlined">contacts_product</span>
            <span class="text">Contatos</span>
          </router-link>
          <router-link to="/team" class="button">
            <span class="material-symbols-outlined">group</span>
            <span class="text">Team</span>
          </router-link>
          <router-link to="/contact" class="button">
            <span class="material-symbols-outlined">email</span>
            <span class="text">Contact</span>
          </router-link>
        </div>
        <div class="flex"></div>
        <div class="menu">
          <router-link to="/settings" class="button">
            <span class="material-symbols-outlined">settings</span>
            <span class="text">Settings</span>
          </router-link>
        </div>
      </aside>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";

const is_expanded = ref(localStorage.getItem("is_expanded") === "true");
const isMobile = ref(localStorage.getItem("mobile") === "true");
const isMenuOpen = ref(false);

const ToggleMenu = () => {
  is_expanded.value = !is_expanded.value;
  localStorage.setItem("is_expanded", is_expanded.value);
};

const toggleMobileMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};
</script>
<style scoped>
aside {
  display: flex;
  flex-direction: column;
  width: 64px;
  height: calc(100dvh - 60px);
  overflow: hidden;
  padding: 16px;
  background-color: #333;
  transition: 0.5s ease-in-out;
  margin: 30px;
  border-radius: 10px;
}
.flex {
  flex: 1 1 0%;
}
.logo {
  margin-bottom: 16px;
}
.logo img {
  width: 32px;
}
.menu-toggle-wrap {
  display: flex;
  justify-content: flex-end;
  position: relative;
  top: 0;
  margin-bottom: 16px;
  transition: 1s ease-in-out;
}
.menu-toggle {
  background: none;
  border: none;
  color: #fff;
  transition: 1s ease-in-out;
}
.menu-toggle .material-symbols-outlined {
  font-size: 32px;
  transition: 1s ease-out;
}
.menu-toggle:hover .material-symbols-outlined {
  color: #007bff;
  transform: translateX(16px);
}
h3,
.button .text {
  opacity: 0;
  transition: opacity 1s ease-in-out;
}
h3 {
  color: #ccc;
  font-size: 16px;
  margin-bottom: 8px;
  text-transform: uppercase;
}
.menu {
  margin: 0 -16px;
}
.button {
  display: flex;
  align-items: center;
  text-decoration: none;
  transition: 1s ease-in-out;
  padding: 8px 16px;
}
.button .material-symbols-outlined {
  font-size: 32px;
  color: #fff;
  transition: 1s ease-in-out;
}
.button .text {
  color: #fff;
  transition: 1s ease-in-out;
}
.button:hover {
  background-color: #212529;
}
.button.router-link-exact-active {
  background-color: #212529;
  border-right: 5px solid #007bff;
}
.is-expanded {
  width: calc(240px);
  .menu-toggle-wrap {
    top: -48px;
  }
  .menu-toggle:hover .material-symbols-outlined {
    color: #007bff;
    transform: translateX(-16px);
  }
  h3,
  .button .text {
    opacity: 1;
  }
  .button,
  .material-symbols-outlined {
    margin-right: 16px;
  }
}
</style>
