<template>
  <div class="banner-container">
      <img src="../assets/ebanx.png" alt="logo ebanx" class="logo-ebanx" />
      <div class="text-header">
        <div class="text-header-name">
          Anomaly Detection in Request
        </div>
        <div class="text-header-powered">
          Hackathon powered by EBANX
        </div>
      </div>
    </div>
</template>

<script>
  export default {
    name: "HeaderComponent"
  }
</script>

<style>
  .banner-container{
    display: flex;
    width: 100%;
    position: relative;
    background: url('https://a.storyblok.com/f/168569/2880x480/a1abdf8973/img-wide.jpg');
    background-size: cover;
    border-radius: 10px;
    height: 200px;
    overflow: hidden;
  }
  .logo-ebanx {
    width: 260px;
    position: absolute;
    top: 0px;
    right: 0px;
  }
  .text-header {
    width: 520px;
    height: 90px;
    margin: auto 0 10px;
    background-color: white;
    opacity: 0.5;
    border-top-right-radius: 10px;
    border-bottom-right-radius: 10px;
    padding-left: 15px;
  }
  .text-header-name {
    font-size: 34px;
    font-weight: bold;
  }
  .text-header-powered {
    width: 100%;
    display: flex;
    justify-content: flex-start ;
    align-items: flex-end;
    text-align: right;
  }
</style>
