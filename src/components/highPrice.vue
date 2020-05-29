<template>
  <div class="highPrice">
    <h4>高値</h4>
    <span>$ {{ highPrice }}</span>
  </div>
  
</template>

<script>
  export default {

    mounted() {
      this.interval = setInterval(() => {
        this.updatePrice();
      },1000 * 60 );

      this.updatePrice();
    },

    methods: {
     updatePrice() {
        this.$bitcoin.fetchPrice1((price) => {
          this.highPrice = price;
        });
      }
    },

    data () {
      return {
        interval: null,
        highPrice: 0,
      }
    }
  }
</script>

<style lang="scss">
  .highPrice {
    margin: 5vh auto 0;
    border: 2px solid darkblue;
    border-radius: 12px;
    background-color: darkblue;
    

    h4 {
      margin: 0 0 .2vh;
      font-size: 1.5rem;
    }

    span {
      color: #2ECC40;
      font-size: 3rem;
      text-shadow: 1px 1px #3D9970;
    }
  }
</style>