<script setup lang="ts">
import TheMenu from "./components/TheMenu.vue"
import Home from "./components/Home.vue"
import Projects from "./components/Projects.vue"
import Contact from "./components/Contact.vue"
import { ref, computed } from "vue";

const lang = ref("fr");
const selected = ref("home"); 

function onSelect(selectedMenu: string) {
  selected.value = selectedMenu;
}

// flag 
function toggleLang() {
  lang.value = lang.value === "fr" ? "en" : "fr";
}

function getFlagName() {
    return lang.value === "en" ? "french_flag.png" : "english_flag.png";
}

</script>

<template>

  <header>
    <TheMenu @select="onSelect" :lang="lang" />
  </header>
  <main>
    <div class="main-header">
      <img :src="`./img/${getFlagName()}`" @click="toggleLang"/>
      <!-- switch theme -->
    </div>
    <Home v-if="selected=='home'" :lang="lang" />
    <Projects v-else-if="selected=='projects'" :lang="lang" />
    <Contact v-else-if="selected=='contact'" :lang="lang" />
  </main>

</template>

<style scoped>
.main-header {
  height: 30px;
  display: flex;
  align-items: center;
  padding: 10px;
}

.main-header img {
  height: 20px;
  margin: 0 5px;
}

main {
  height: 100vh;
  overflow-y: scroll;
}
</style>
