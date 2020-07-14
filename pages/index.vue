<template>
  <section class="home-page">
    <!-- FRAME WINDOW -->
    <div id="frame-top"></div>
    <div id="frame-right"></div>
    <div id="frame-bottom"></div>
    <div id="frame-left"></div>
    
    <div class="main-page d-flex">
      <div class="nav-bar">
        <button class="btn btn-primary btn-more" @click="loadData">Open Data</button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data(){
    return {
      loading: true
    }
  },
  methods: {
    loadData(){
      this.$router.push({ 'path': '/load-api' })
    }
  }
}
</script>
