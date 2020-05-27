<template>
  <div class="lastPrice">
    <h4>現在値</h4>
    <span>$ {{ lastPrice }}</span>
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
        this.$bitcoin.fetchPrice((price) => {
          this.lastPrice = price;
        });
      }
    },

    data () {
      return {
        interval: null,
        lastPrice: 0,
      }
    }
  }
</script>

<style lang="scss">
  .lastPrice {
    margin: 5vh auto 0;
    border: 2px solid blue;
    border-radius: 12px;
    

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