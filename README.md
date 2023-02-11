# vue-user-card

Simple user card component

#### DEMO https://vue-user-card.netlify.app/

![vue-user-avatar.png](src%2Fassets%2Fvue-user-avatar.png)

![vue-user-card.gif](src%2Fassets%2Fvue-user-card.gif)

Easily implement into your projects, just copy "user-card.vue" into your project.

Mobile friendly.

External props passed to the component:

```
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

<template >
  <user-card :user-data="user" />
</template>

props: {
    userData: {
    type: Object,
    }
},

UI Config CSS:
/* CARD SETTINGS */
--avatar-size: 7rem;
--user-card-size: 20rem;
--user-card-height: 30rem;
--card-bg: #2d2d2d;
--card-font-color:#cae5e5;
--card-accent-color: coral;
--card-radius: 1.5rem;

```

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
