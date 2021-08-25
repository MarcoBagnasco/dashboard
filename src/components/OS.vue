<template>
    <div class="chart mid">
        <h3>Operating System</h3>
        <ChartDoughnut :height="250" :chartdata="chartdata" :options="options"/>
    </div>
</template>

<script>
import ChartDoughnut from "./ChartDoughnut.vue";

export default {
    name: 'OS',
    props:{
        devices: Array,
    },
    components: {
        ChartDoughnut,
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
                        hoverBorderWidth: 8,
                        data: []
                    }
                ],
            },
            options: {
                legend: {
                    position: 'right',
                    align: 'start',
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
            this.devices.forEach(item => {
                this.chartdata.labels.push(item.os);
                this.chartdata.datasets[0].data.push(item.connections);
            })
        }
    }    
}
</script>