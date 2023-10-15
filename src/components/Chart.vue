<template>
    <div class="pie-chart">
      <canvas ref="chartCanvas"></canvas>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted, onBeforeUnmount } from 'vue';
 
  
 
      const chartCanvas = ref(null);
      let chart = null;
  
      const fetchData = () => {
        
        const data = {
          labels: [
            'Dhaka',
             'Chittagong',
              'Khulna',
               'Rajshahi',
               'Sylhet',
               'Rangpur',
               'Barisal',
               'Mymensingh'
            ],
          datasets: [
            {
              data: [
                100,
                200,
                300,
                400,
                500,
                600,
                700,
                800
              ],
              backgroundColor: [
                'rgb(255, 99, 132)',
                'rgb(54, 162, 235)',
                'rgb(255, 205, 86)',
                'rgb(75, 192, 192)',
                'rgb(153, 102, 255)',
                'rgb(255, 159, 64)',
                'rgb(255, 99, 132)',
                'rgb(54, 162, 235)',
              ],
            },
          ],
          options: {
    legend: {display: false},
    title: {
      display: true,
      text: "Population of Bangladesh in 2022",
    }
  }
        };
  
        return data;
      };
  
      onMounted(() => {
        const chartData = fetchData();
        const ctx = chartCanvas.value.getContext('2d');
        if (ctx) {
          chart = new Chart(ctx, {
            type: 'pie',
            data: chartData,
          });
        }
      });
  
      onBeforeUnmount(() => {
        // Clean up resources
        if (chart) {
          chart.destroy();
        }
      });
  
   
 
  </script>
  
  <style>
  .pie-chart {
    text-align: center;
  }
  </style>
  