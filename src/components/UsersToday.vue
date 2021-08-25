<template>
    <div class="chart mid">
        <h3>Users Age Range</h3>
        <ChartBar :height="250" :chartdata="chartdata" :options="options"/>
    </div>
</template>

<script>
import ChartBar from './ChartBar.vue';

export default {
    name: 'UsersToday',
    components:{
        ChartBar,
    },
    props: {
        connections: Array,
    },
    data(){
        return {
            usersRange: [],
            usersCount: [],
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
                scales:{
                    yAxes: [{
                        ticks: {
                            stepSize: 10,
                            min: 0,
                            suggestedMax: 50,
                        }
                    }],
                },
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
        this.aggregate();
    },
    methods: {
        /**
         * Aggregate data from json
         */
        aggregate(){
            // Create Range array
            this.connections.forEach(item => {
                if(!this.usersRange.includes(item.age)){
                    this.usersRange.push(item.age)
                }
            })
            // Create objects with range property
            this.usersRange.forEach(item =>{
                this.usersCount.push({range: item, connections: 0})
            })
            // Add number of connections to objects
            this.connections.forEach(item => {
                const age = item.age;
                this.usersCount.forEach(obj => {
                    if(obj.range == age){
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
            this.usersCount.forEach(item => {
                this.chartdata.labels.push(item.range);
                this.chartdata.datasets[0].data.push(item.connections);
            })
        },

    }
}
</script>