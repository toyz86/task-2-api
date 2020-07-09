<template>
  <section class="home-page">
    <!-- FRAME WINDOW -->
    <div id="frame-top"></div>
    <div id="frame-right"></div>
    <div id="frame-bottom"></div>
    <div id="frame-left"></div>
    
    <div class="main-page">
      <div class="nav-bar d-flex justify-content-center mt-4">
        <nuxt-link to="/load-api" class="nav-link">Go to Data</nuxt-link>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data(){
    return {

    }
  },
}
</script>

<style scoped>
  .main-page {
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: 1rem 20rem;
    background-image: url("/img/home-bg.jpg");
    background-repeat: no-repeat;
    background-size: cover;
    height: 100vh;
  }
    h1 {
    color: cornsilk;
  }
  span {
    font-weight: lighter;
  }
  #frame-top, #frame-bottom, #frame-left, #frame-right {
    background: #fff;
    position: fixed;
    }
    #frame-left, #frame-right {
      top: 0; bottom: 0;
      width: 18px;
      }
      #frame-left { left: 0; }
      #frame-right { right: 0; }
      
    #frame-top, #frame-bottom {
      left: 0; right: 0;
      height: 18px;
      }
      #frame-top { top: 0; }
      #frame-bottom { bottom: 0; }
  p {
    color: #ccc;
  }

  .portfolio {
    margin-top: -130px;
    padding: 0px 50px 0px 50px;
  }

.nav-link {
      float: left;
      font-size: 30px;
      border: 1px solid rgb(77, 83, 84);
      text-decoration: none;
      color: rgba(255, 255, 255, .7);
      padding: 5px 15px;
      border-radius: 20px;
      margin: 0px 10px;
      text-align: center;
      transition: 0.5s;
      align-items: center;
      cursor: pointer;
    }
  .nav-link:hover {
        background-color: #47c9e5;
        color: black;    
  }
  
</style>
