<template>
  <div class="canvasContainer">
    <canvas id="history"></canvas>
  </div>
</template>

<script>
  import Chart from 'chart.js';

  export default {

    mounted() {
      this.$bitcoin.fetchHistory((data) => {
        this.data = data;
        this.drawGraph();
      });
    },

    methods: {
      drawGraph() {
        let ctx = document.getElementById('history').getContext('2d');
        this.chart = new Chart(ctx, {
          type: 'line',
          data: {
            labels: Object.keys(this.data),
            datasets: [{
              data: Object.values(this.data),
              pointBackgroundColor: 'rgb(1, 255, 112)',
              borderColor: 'rgb(61, 153, 112)', 
              fill: true,
              backgroundColor: "",
            }]
          },
          options: {    
           legend: false,
           
            scales: {              
              xAxes: [{
                display: true,
                ticks: {
                    fontColor: "white",
                    fontStyle: "bold",
                },
              }],
               yAxes: [{
                ticks: {
                    fontColor: "white",
                    fontStyle: "bold",
                    
                    

                    
                },
}]
              
            }            
          }
        });
      },
    },

    data () {
      return {
        chart: null,
        data: {},
      }
    }
  }
</script>

<style lang="scss">
  .canvasContainer {
    height: 70vh;
    width: 95%;
    margin: left;
  
   
    
     
  }
</style>
