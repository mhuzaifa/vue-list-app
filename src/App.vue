<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
      <router-view/>
    </nav>
  </div>
</template>

<script>
import Skills from "./components/Skills.vue";
import './style.scss';

export default {
  name: "app",
  components: {
    // eslint-disable-next-line
    Skills
  },
  created(){
    document.title = "Add Skill App"
  }
};
</script>
