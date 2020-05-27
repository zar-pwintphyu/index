<template>
  <div class="previousPrice">
    <h4>前日比</h4>
    <span>$ {{ previousPrice }}</span>
  </div>
  
</template>

<script>
  export default {

    mounted() {
      this.interval = setInterval(() => {
        this.previousPrice();
      }, 1000 * 60);

      this.previousPrice();
    },

    methods: {
      previousPrice() {
        this.$bitcoin.fetchPrice((price) => {
          this.previousPrice = price;
        });
      }
    },

    data () {
      return {
        interval: null,
        previousPrice: 0,
      }
    }
  }
</script>

<style lang="scss">
  .previousPrice {
    margin: 5vh auto 0;

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