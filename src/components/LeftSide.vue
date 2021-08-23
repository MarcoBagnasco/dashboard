<template>
    <div class="left-side">
        <h1 class="main-title">- Dashbool -</h1>

        <!-- Profile -->
        <div class="flex ai-center">
            <img src="../assets/avatar_8.jpg" alt="avatar">
            <div>
                <div>Welcome</div>
                <div class="bold">Marco Bagnasco</div>
            </div>
        </div>
        
        <!-- Menu -->
        <h4 class="menu-title bold">general</h4>
        <MenuItem :icon="'fas fa-home'" :title="'Home'">
            <div class="content">Dashboard</div>
            <div class="content">Dashboard 1</div>
            <div class="content">Dashboard 2</div>
        </MenuItem>

        <MenuItem :icon="'fas fa-map-marked-alt'" :title="'Maps'">
            <div class="content">Show Map</div>
        </MenuItem>

        <MenuItem :icon="'fas fa-cog'" :title="'Config'">
            <div class="content">Config 1</div>
            <div class="content">Config 2</div>
            <div class="content">Config 3</div>
            <div class="content">Config 4</div>
        </MenuItem>

        <MenuItem :icon="'fas fa-envelope'" :title="'Contacts'">
            <div class="content">My Contacts</div>
            <div class="content">VIP Contatcs</div>
        </MenuItem>
    </div>
</template>

<script>
import MenuItem from './MenuItem.vue';

export default {
    name: 'LeftSide',
    components:{
        MenuItem,
    },
}
</script>

<style lang="scss" scoped>
    .left-side{
        width: 250px;
        padding: 20px 10px;
        flex-shrink: 0;
        color: #fff;
        background-color: #2a4054;

        .main-title{
            font-size: 1.2rem;
            margin-bottom: 20px;
        }

        img{
            width: 50px;
            margin-right: 20px;
            border-radius: 50%;
            border: 3px solid #fff;
        }

        .menu-title{
            padding: 15px 0;
            margin-top: 10px;
            margin-bottom: 20px;
            font-size: 0.9rem;
            text-transform: uppercase;
            border-bottom: 2px solid #fff;
        }

        .content{
            padding: 7px 35px;
            &:hover{
                background-color: #354b60;
            }
        }
    }
</style>