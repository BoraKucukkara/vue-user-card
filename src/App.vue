<template >
  <user-card :user-data="user" />
</template>

<script>
import userCard from './components/user-card.vue'

export default {
  name: 'App',
  components: {
    userCard
  },
  data() {
    return{
      user: {
        name:"Bora Kucukkara",
        country: "Turkey",
        title: "UI Designer / Front-end Developer",
        tags: ["UI/UX", "HTML", "CSS", "javaScript", "VueJS", "SASS", "JSON", "GIT"],
        avatar: "https://i.pravatar.cc/"
      }
    }
  }
}
</script>

<style>
/* RESET */
*,
*::before,
*::after {
  box-sizing: border-box;
}

body {
  margin:0;
  font-family: system-ui;
  display:flex;
  align-items: center;
  justify-content: center;
  width: 100vw;
  height: 100vh;
}
</style>
