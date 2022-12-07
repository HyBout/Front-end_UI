<template>
    <side-bar />
    <router-view></router-view>
    <!-- <login></login> -->
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
