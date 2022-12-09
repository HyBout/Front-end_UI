<template>
    <!-- <login></login> -->
    <side-bar/>
    <router-view></router-view>
</template>

<script>
// import Login from './components/Login.vue'
import SideBar from './components/SideBar.vue';
export default { 
    name: 'App',
    components: {
        // Login,
        SideBar,
    },

};
</script>
