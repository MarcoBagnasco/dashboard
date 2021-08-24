<template>
  <div class="connections">
      <h3>Monthly Connections</h3>
      <ChartLine :height="250" :chartdata="chartdata" :options="options"/>
  </div>
</template>

<script>
import ChartLine from "./ChartLine.vue";

export default {
    name: 'Connections',
    components:{
        ChartLine,
    },
    props: {
        connections: Array,
    },
    data(){
        return { 
            chartdata: {
                labels: [],
                datasets: [
                    {
                        label: 'Monthly',
                        backgroundColor: '#9bbec366',
                        borderColor: '#9bbec3',
                        data: []
                    }
                ],
            },
            options: {
                scales:{
                    yAxes: [{
                            ticks: {
                                stepSize: 1000,
                                min: 0,
                                suggestedMax: 5000,
                            }
                    }],
                },
                responsive: true,
                maintainAspectRatio: false,
            },
        }
    },
    created(){
        this.setData();
    },
    methods: {
        /**
         * Set Data for the Chart
         */
        setData(){
            this.connections.forEach(item => {
                this.chartdata.labels.push(item.month);
                this.chartdata.datasets[0].data.push(item.connections);
            })
        }
    }
}
</script>

<style lang="scss" scoped>
    .connections{
        margin-top: 20px;
        padding: 10px;
        background-color: #fff;
        border-radius: 5px;

        h3{
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
        }
    }
</style>