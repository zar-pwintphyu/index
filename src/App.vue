<template>
  <div id="app" class ="grid-container">
    <div class="grid-child ">
       <h1>JDR Index™ β　powered by JDRpro</h1>
       <br>
       <history></history>
    </div>

    <div class="grid-child ">
      <br>
        <lastPrice></lastPrice>
        <previousPrice></previousPrice>
        <highPrice></highPrice>
        <lowPrice></lowPrice>
    </div>
    
    <div class="grid-child">
      <p>ようこそJDR.株式会社へ！      本日のBTCの値動きは・・・</p>
     
    </div>
 
  </div>

</template>

<script>
  import lastPrice from './components/lastPrice.vue';
  import history from './components/history.vue';
  import highPrice from './components/highPrice.vue';
  import lowPrice from './components/lowPrice.vue';
  import previousPrice from './components/previousPrice.vue';
  export default {
    name: 'app',
    components: {
      lowPrice,
      previousPrice,
      lastPrice,
      highPrice,
      history
    },
  }
</script>

<style lang="scss">

  $font-italic: 'Indie Flower', cursive;
  $gray: #ddd;

  html {
    @media (max-width: 1000px) {
      font-size: 12px;
    }
  }

  body {
    background: linear-gradient(to right, purple 30%, darkblue 90%);
    color: $gray;
    
    
    
  }

  h1 {
        text-align: center ;
        font-size: 2rem;
  }
  .grid-container {
    display: grid;
    grid-template-columns: 2fr 300px;
    font-family: $font-italic;
    font-style: italic;
}
p {
    text-align: center ;
    margin-bottom: 10vh;
    font-size: 1.2rem;

  }


</style>
