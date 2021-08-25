<template>
    <div class="main-content">
        <MainHeader/>
        <!-- Chart Area -->
        <div v-if="load1 && load2" class="scroll-part">
            <!-- Monthly Connections -->
            <Connections :connections="data.MonthlyConnections"/>     

            <div class="flex jc-between">
                <!-- Users Age Range -->
                <UsersAge :ages="data.UsersAgeRange"/>

                <!-- Operating System -->
                <OS :devices="data.Devices"/>
            </div>  

            <!-- Solar Power -->
            <Solar/>   

            <!-- Today -->
            <h2>Today</h2>
            <div class="flex jc-between">
                <!-- Users Age Range -->
                <UsersToday :connections="connections"/>

                <!-- Operating System -->
                <OS :devices="data.Devices"/>
            </div>  
        </div>
    </div>
</template>

<script>
import MainHeader from './MainHeader.vue';
import Connections from './Connections.vue';
import UsersAge from './UsersAge.vue';
import OS from './OS.vue';
import Solar from './Solar.vue';
import UsersToday from './UsersToday.vue';
import axios from 'axios';

export default {
    name: 'Main',
    components:{
        MainHeader,
        Connections,
        UsersAge,
        OS,
        Solar,
        UsersToday,
    },
    data(){
        return {
            load1: false,
            load2: false,
            data: {},
            connections: [],
            url: 'https://api.jsonbin.io/v3/b',
            config: {
                headers: {
                    'X-Master-Key': '$2b$10$uF.P5J6WPLO1FKJz.ms4BuEirEJB0LqkQzw4Pfg6U48oBjz2nd21.',
                    'X-Bin-Meta' : false
                }
            },
        }
    },
    created(){
        this.getData();
        this.getConnections();
    },
    methods: {
        /**
         * Get data.json from server
         */
        getData(){
            axios.get(`${this.url}/6123d5ab2aa80036126e9315`, this.config)
            .then(res => {
                this.data = res.data;
                this.load1 = true;
            })
            .catch(err => {
                console.log(err);
            });
        },

        /**
         * Get connections.json from server
         */
        getConnections(){
            axios.get(`${this.url}/6123d5712aa80036126e92f9`, this.config)
            .then(res => {
                this.connections = res.data;
                // res.data.forEach(item => {
                //     if(!this.usersRange.includes(item.age)){
                //         this.usersRange.push(item.age)
                //     }
                // })
                // this.usersRange.forEach(item =>{
                //     this.connections.push({range: item, connections: 0})
                // })
                // res.data.forEach(item => {
                //     const age = item.age;
                //     this.connections.forEach(obj => {
                //         if(obj.range == age){
                //             obj.connections++;
                //         }
                //     })
                    // switch (item.age) {
                    //     case '46-60':
                    //         this.connections[0].connections++;
                    //         break;
                    //     case '26-35':
                    //         this.connections[1].connections++;
                    //         break;
                    //     case '17-25':
                    //         this.connections[2].connections++;
                    //         break;
                    //     case '36-45':
                    //         this.connections[3].connections++;
                    //         break;
                    //     case '0-16':
                    //         this.connections[4].connections++;
                    //         break;
                            

                    // }
                // })
                this.load2 = true;
            })
            .catch(err => {
                console.log(err);
            });
        }
    }
}
</script>

<style lang="scss" scoped>
    .main-content {
        position: relative;
        padding-top: 45px;
        flex-grow: 1;
        color: #666;
        text-align: center;
        background-color: #eee;

        .scroll-part{
            height: calc(100vh - 45px) ;
            padding: 0 20px;
            overflow: auto;
        }

        h2{
            color: #000;
        }
    }
</style>