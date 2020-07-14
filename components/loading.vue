<template>
  <section v-if="loading">
    <div class="site-nav-canvas d-flex">
      <div class="spinner">
        <div class="bounce1"></div>
        <div class="bounce2"></div>
        <div class="bounce3"></div>
        <h4 class="counter">{{ onLoaded }}</h4>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data: () => ({
    loading: false,
    interval: null,
    loadingPercent: 0,
    loadTime: 0
  }),
  created() {
      this.countProgress();
  },
  methods: {
    start () {
      this.loading = true
    },
    finish () {
      this.loading = false
    },
    countProgress() {
      let step = this.loadTime / 100;
      this.interval = setInterval(() => {
        this.loadingPercent++
      }, step);
    }
  },
  computed: {
    onLoaded(){
      return this.loadingPercent + '%'
    }
  },
  watch: {
    loadingPercent(val) {
      if (val >= 100) {
        console.log('data complete');
        clearInterval(this.interval)
      }
    }
  },
}
</script>

<style scoped>
.counter {
  color: #fff
}
.site-nav-canvas {
  background-color: #47c9e5;
  opacity: 0.7;
  height: 100vh;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}
.spinner {
  margin: auto;
  width: 70px;
  text-align: center;
  justify-content: center;
  align-items: center;  
}

.spinner > div {
  width: 18px;
  height: 18px;
  background-color: #fff;

  border-radius: 100%;
  display: inline-block;
  -webkit-animation: sk-bouncedelay 1.4s infinite ease-in-out both;
  animation: sk-bouncedelay 1.4s infinite ease-in-out both;
}

.spinner .bounce1 {
  -webkit-animation-delay: -0.32s;
  animation-delay: -0.32s;
}

.spinner .bounce2 {
  -webkit-animation-delay: -0.16s;
  animation-delay: -0.16s;
}

@-webkit-keyframes sk-bouncedelay {
  0%, 80%, 100% { -webkit-transform: scale(0) }
  40% { -webkit-transform: scale(1.0) }
}

@keyframes sk-bouncedelay {
  0%, 80%, 100% { 
    -webkit-transform: scale(0);
    transform: scale(0);
  } 40% { 
    -webkit-transform: scale(1.0);
    transform: scale(1.0);
  }
}
</style>
