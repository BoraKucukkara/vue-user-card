<template>
  <div class="user-card" :class="{'toggle-index': toggle}"
       tabindex="0" @focus="togglePop(true)" @focusout="togglePop(false)">
    <div class="user-card_avatar" @mouseover="togglePop(true)">
      <img :src="userData.avatar" :class="{'user-card_avatar_border': toggle}" alt="user-avatar" />
    </div>
    <div class="user-card_popup" :class="{'toggle-show': toggle, 'toggle-hide': !toggle, 'toggle-reset': firstLoad}">
      <div class="user-card_avatar_bokeh">
        <img :src="userData.avatar" alt="user-avatar" />
      </div>
      <div class="user-card_content" @mouseleave="togglePop(false)" >
        <p class="user-card_badge">PRO</p>
        <h1>{{userData.name}}</h1>
        <span>{{userData.country}}</span>
        <span>{{userData.title}}</span>
        <div class="user-card_tags" >
          <span v-for="(tag,index) in userData.tags" :key="index">{{tag}}</span>
        </div>
        <button class="user-card_cta">Follow</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      toggle: false,
      firstLoad: true
    }
  },
  props: {
    userData: {
      type: Object,
    }
  },
  methods: {
    togglePop(event) {
      this.firstLoad = false
      this.toggle = event;
    }
  }
}
</script>

<style scoped>
.user-card {
  /* CARD SETTINGS */
  --avatar-size: 7rem;
  --user-card-size: 20rem;
  --user-card-height: 30rem;
  --card-bg: #2d2d2d;
  --card-font-color:#cae5e5;
  --card-accent-color: coral;
  --card-radius: 1.5rem;

  position:relative;
  width: var(--avatar-size);
  height: var(--avatar-size);
  display: inline-block;
}
.user-card_popup {
  position: absolute;
  overflow: hidden;
  color: var(--card-font-color);
  width:var(--user-card-size);
  height: var(--user-card-height);
  top:calc(var(--avatar-size) / -2 + -2rem);
  left:calc((var(--avatar-size) - var(--user-card-size)) / 2);
  background: var(--card-bg);
  z-index: 0;
  border-radius: var(--card-radius);
  box-shadow: rgb(55, 56, 56) 0 1rem 2rem -.5rem;
}
.user-card_avatar {
  width: inherit;
  height: inherit;
}
.user-card_avatar img {
  position: absolute;
  width: inherit;
  height: inherit;
  object-fit: cover;
  border-radius: 50%;
  z-index: 3;
  transition: all .2s;
}
.user-card_avatar_border {
  box-shadow:  0 0 0 .3rem var(--card-bg);
}
.user-card_avatar_bokeh {
  width: var(--user-card-size);
  height: calc(var(--avatar-size) + 2rem);
  overflow: hidden;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
}
.user-card_avatar_bokeh:after {
  content:"";
  backdrop-filter: blur(.3rem);
  background: #00000022;
  -webkit-backdrop-filter: blur(.3rem);
  position: absolute;
  z-index: 4;
  inset: 0;
}
.user-card_avatar_bokeh img {
  position: absolute;
  width: calc(var(--user-card-size) * 1.2); /* bokeh image zoom */
}
.user-card_badge {
  position: absolute;
  top: 0;
  right: 0;
  margin:1rem;
  background: var(--card-accent-color);
  padding: .3rem;
  border-radius: .4rem;
  font-size: .8rem;
  color:#fff;
  z-index: 4;
}
/* CARD CONTENT */
.user-card_content {
  padding: calc(var(--avatar-size) * 1.8 ) 1rem 0rem 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  position: absolute;
  inset: 0;
  z-index: 4;
}
.user-card_content h1 {font-size: 1.5rem; font-weight: normal}
.user-card_tags {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
  gap:.5rem;
  margin: 1rem 0;
}
.user-card_tags span {
  color:#777;
  padding: .2rem .3rem;
  border: 1px solid #777;
  border-radius: .3rem;
  font-size: .8rem;
}
.user-card_cta {
  width: calc(var(--user-card-size) - 2rem);
  margin: 1rem;
  padding: .5rem 1rem;
  background: var(--card-accent-color);
  font-size: 1rem;
  color:#fff;
  border-radius: 1rem;
  border:none;
  transition: all .2s;
  cursor: pointer;
}
.user-card_cta:hover {box-shadow: 0 0 .5rem  var(--card-accent-color)}
/* TOGGLE */
.toggle-show {
  opacity: 0;
  animation: fade-in .5s ease forwards;
}
.toggle-hide {
  opacity: 0;
  animation: fade-out .5s ease forwards;
}
.toggle-index {
  z-index: 99;
}
.toggle-reset {
  display: none;
}
@keyframes fade-in {
  0% {
    opacity: 1;
    clip-path: circle(8% at 50% 27%);
  }
  1%{display: block}
  100% {
    opacity:1;
    clip-path: circle(100% at 50% 50%);
  }
}
@keyframes fade-out {
  0% {
    opacity:1;
    clip-path: circle(100% at 50% 50%);
  }
  99% {
    opacity:1;
    clip-path: circle(8% at 50% 27%);
  }
  100% {display: none}
}
</style>
