<script setup>
  import { ref } from 'vue'

  const quote = ref({})

  function refresh() {
    fetch('https://api.gameofthronesquotes.xyz/v1/random')
      .then( response => response.json() )
      .then( data => {
        quote.value = data;
        return data;
      } );
  }

  refresh();

  // Refresh every 4 seconds.
  const interval = setInterval(refresh, 4000);
</script>

<template>
  <p v-if="quote.sentence">
    {{ quote.sentence }}
    <hr />
    <small>{{ quote.character.name }}</small>
  </p>
</template>

<style>
  @import url('https://fonts.googleapis.com/css?family=Baloo+2:400,800&display=swap" rel="stylesheet');

  * {
    box-sizing: border-box;
  }

	body {
    min-height: 100vh;
    margin: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    font: 2vw system-ui;
    background-color: #f9cdad;
  }

  #app {
    max-width: 80%;
  }

  p {
    transform: translatey(0px);
    -webkit-animation: float 5s ease-in-out infinite;
            animation: float 5s ease-in-out infinite;
    mix-blend-mode: multiply;
    text-align: center;
    text-transform: uppercase;
    font-weight: bold;
    letter-spacing: 3px;
    font-size: 15px;
    color: #774f38;
    background-color: #ece5ce;
    padding: 50px;
    border-radius: 11px;
    position: relative;
    box-shadow: 20px 20px #83af9b;
    font-family: "Baloo 2", cursive;
  }

  p:after {
    transform: translatey(0px);
    -webkit-animation: float2 5s ease-in-out infinite;
            animation: float2 5s ease-in-out infinite;
    content: ".";
    font-weight: bold;
    -webkit-text-fill-color: #ece5ce;
    text-shadow: 22px 22px #83af9b;
    text-align: left;
    font-size: 55px;
    width: 55px;
    height: 11px;
    line-height: 30px;
    border-radius: 11px;
    background-color: #ece5ce;
    position: absolute;
    display: block;
    bottom: -30px;
    left: 0;
    box-shadow: 22px 22px #83af9b;
    z-index: -2;
  }

  p small {
    text-transform: none;
    font-weight: 400;
    font-style: italic;
  }

  @-webkit-keyframes float {
    0% {
      transform: translatey(0px);
    }
    50% {
      transform: translatey(-20px);
    }
    100% {
      transform: translatey(0px);
    }
  }

  @keyframes float {
    0% {
      transform: translatey(0px);
    }
    50% {
      transform: translatey(-20px);
    }
    100% {
      transform: translatey(0px);
    }
  }

  @-webkit-keyframes float2 {
    0% {
      line-height: 30px;
      transform: translatey(0px);
    }
    55% {
      transform: translatey(-20px);
    }
    60% {
      line-height: 10px;
    }
    100% {
      line-height: 30px;
      transform: translatey(0px);
    }
  }

  @keyframes float2 {
    0% {
      line-height: 30px;
      transform: translatey(0px);
    }
    55% {
      transform: translatey(-20px);
    }
    60% {
      line-height: 10px;
    }
    100% {
      line-height: 30px;
      transform: translatey(0px);
    }
  }
</style>
