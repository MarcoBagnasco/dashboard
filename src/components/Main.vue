<template>
    <div class="main-content">
        <MainHeader/>
        <!-- Chart Area -->
        <div v-if="load" class="scroll-part">
            <Connections :connections="data.MonthlyConnections"/>
            <div class="flex">
                <UsersAge :ages="data.UsersAgeRange"/>
            </div>
        </div>
    </div>
</template>

<script>
import MainHeader from './MainHeader.vue';
import Connections from './Connections.vue';
import UsersAge from './UsersAge.vue';
import axios from 'axios';

export default {
    name: 'Main',
    components:{
        MainHeader,
        Connections,
        UsersAge,
    },
    data(){
        return {
            load: false,
            data: {},
        }
    },
    created(){
        this.getData();
    },
    methods: {
        /**
         * Get Data from server
         */
        getData(){
            let config = {
                headers: {
                    'X-Master-Key': '$2b$10$uF.P5J6WPLO1FKJz.ms4BuEirEJB0LqkQzw4Pfg6U48oBjz2nd21.',
                    'X-Bin-Meta' : false
                }
            }
            axios.get('https://api.jsonbin.io/v3/b/6123d5ab2aa80036126e9315', config)
            .then(res => {
                this.data = res.data;
                this.load = true;
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
        padding: 45px 20px;
        flex-grow: 1;
        color: #666;
        text-align: center;
        background-color: #eee;

        .scroll-part{
            height: calc(100vh - 45px) ;
            overflow: auto;
        }
    }
</style>