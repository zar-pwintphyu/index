<template>
  <div class="lowPrice">
    <h4>安値</h4>
    <span>$ {{ lowPrice }}</span>
  </div>
  
</template>

<script>
  export default {

    mounted() {
      this.interval = setInterval(() => {
        this.updatePrice();
      }, 1000 * 60);

      this.updatePrice();
    },

    methods: {
      updatePrice() {
        this.$bitcoin.fetchPrice2((price) => {
          this.lowPrice = price;
        });
      }
    },

    data () {
      return {
        interval: null,
        lowPrice: 0,
      }
    }
  }
</script>

<style lang="scss">
  .lowPrice {
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