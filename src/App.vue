<template>
  <div id="app">
    <page-content></page-content>
    <div class="fade" />
    <div class="tip">
      <img class="scape-img"
        :src="ScapeImg" />
      <p>请使用纵向</p>
    </div>
  </div>
</template>

<script>
import ScapeImg from './assets/scape.png';
import PageContent from './PageContent';

export default {
  components: {
    PageContent
  },
  data () {
    return {
      ScapeImg,
    }
  },
}
</script>

<style lang="less">
* {
  margin: 0;
  padding: 0;
}
@keyframes imgRotate {
  from {
    transform: rotate(-90deg);
  }

  50% {
    transform: rotate(0);
  }

  to {
    transform: rotate(-90deg);
  }
}
.fade,
.tip {
  display: none;
}
@media (orientation: portrait) {
  .fade {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: black;
    opacity: 0.5;
    display: block;
  }
  .tip {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    display: block;
    .scape-img {
      max-width: 100vw;
      max-height: 100vh;
      transform: rotate(-90deg);
      animation-duration: 1s;
      animation-name: imgRotate;
      animation-iteration-count: infinite;
    }
    p {
      color: white;
      font-weight: bold;
    }
  }
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
