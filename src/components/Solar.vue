<template>
    <div>
        <i class="fas fa-play play" :class="{stop: !play}" @click="updateChart"></i>       
        <div class="chart">
            <h3>Solar Power</h3>
            <ChartLine :height="300" :chart-data="chartdata" :options="options"/>
        </div>
    </div>
</template>

<script>
import ChartLine from "./ChartLine.vue";

export default {
    name: 'Solar',
    components:{
        ChartLine,
    },
    data(){
        return{
            play: true,
            power: [0, 0, 0, 0, 0, 0, 10, 20, 40, 80, 100, 100,
                     100, 100, 80, 60, 40, 20, 10, 10, 5, 0, 0, 0],
            chartdata: {
                labels: ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11',
                            '12', '13', '14', '15', '16', '17', '18', '19', '20', '21', '22', '23'],
                datasets: [
                    {
                        label: 'Daily',
                        backgroundColor: '#9bbec366',
                        borderColor: '#9bbec3',
                        data: [],
                    }
                ],
            },
            options: {
                animation: false,
                scales:{
                    yAxes: [{
                            ticks: {
                                stepSize: 10,
                                min: 0,
                                suggestedMax: 100,
                            }
                    }],
                },
                layout: {
                    padding: {
                        top: 20,
                    }
                },
                responsive: true,
                maintainAspectRatio: false,
            },
        }
    },
    methods: {
        /**
         * Populate Chart
         */
        updateChart(){
            if(this.play){
                this.play = false;
                
                const dataArray = this.chartdata.datasets[0].data;

                // Reset Data
                dataArray.length = 0;

                let count = 0;
                const time = setInterval(() => {
                    dataArray.push(this.power[count] + (Math.round(Math.random()) ? 0 : this.randVar()));

                    // Check Limit
                    if(dataArray[count] < 0){
                        dataArray[count] += 5;
                    } else if(dataArray[count] > 100){
                        dataArray[count] -= 5
                    }

                    count++;

                    // Stop 
                    if(count >= this.power.length){
                        clearInterval(time);
                        this.play = true;
                    }
                }, 500);
            }
        },

        /**
         * Random Variation
         */
        randVar(){
            return Math.round(Math.random()) ? 5 : -5;
        }
    }
}
</script>

<style lang="scss" scoped>
    .play{         
        margin: 20px;
        padding: 10px;
        background-color: #fff;
        font-size: 1.3rem;
        color: #000;
        border-radius: 5px;
        cursor: pointer;

        &.stop{
            color: #ccc;
            cursor: not-allowed;
        }
    }
</style>