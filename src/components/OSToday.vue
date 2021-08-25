<template>
    <div class="chart mid">
        <h3>Operating System</h3>
        <ChartDoughnut :height="300" :chartdata="chartdata" :options="options"/>
    </div>
</template>

<script>
import ChartDoughnut from "./ChartDoughnut.vue";

export default {
    name: 'OSToday',
    props:{
        connections: Array,
    },
    components: {
        ChartDoughnut,
    },
    data(){
        return {
            os: [],
            osCount: [],
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
        this.aggregate();
    },
    methods: {
        /**
         * Aggregate data from json
         */
        aggregate(){
            // Create Range array
            this.connections.forEach(item => {
                if(!this.os.includes(item.device)){
                    this.os.push(item.device)
                }
            })
            // Create objects with range property
            this.os.forEach(item =>{
                this.osCount.push({os: item, connections: 0})
            })
            // Add number of connections to objects
            this.connections.forEach(item => {
                const device = item.device;
                this.osCount.forEach(obj => {
                    if(obj.os == device){
                        obj.connections++;
                    }
                })
            });

            this.setData();
        },

        /**
         * Set Data for the Chart
         */
        setData(){
            this.osCount.forEach(item => {
                this.chartdata.labels.push(item.os);
                this.chartdata.datasets[0].data.push(item.connections);
            })
        },
    }    
}
</script>