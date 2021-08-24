<template>
    <div class="chart">
        <h3>Users Age Range</h3>
        <ChartBar :height="300" :chartdata="chartdata" :options="options"/>
    </div>
</template>

<script>
import ChartBar from './ChartBar.vue';

export default {
    name: 'UsersAge',
    props:{
        ages: Array,
    },
    components:{
        ChartBar,
    },
    data(){
        return { 
            chartdata: {
                labels: [],
                datasets: [
                    {
                        backgroundColor: [
                            '#3e95cd',
                            '#8e5ea3',
                            '#5abb9f',
                            '#e8c3b9',
                            '#c45850'
                        ],
                        data: []
                    }
                ],
            },
            options: {
                legend: {
                    display: false,
                },
                layout: {
                    padding: {
                        top: 30,
                    }
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
            this.ages.forEach(item => {
                this.chartdata.labels.push(item.range);
                this.chartdata.datasets[0].data.push(item.connections);
            })
        }
    }
}
</script>

<style lang="scss" scoped>
    .chart{
        margin-right: 20px;
        width: calc(50% - 20px);
    }
</style>