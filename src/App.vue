<template>
    <div>
        <navigation-bar></navigation-bar>
        <section>
            <dash-board></dash-board>
        </section>
    </div>
</template>

<script>
// import axios from 'axios';

import NavigationBar from './components/layouts/TheNavigationBar.vue';
import DashBoard from '../src/components/ui/TheDashBoard.vue';

export default {
    name: 'App',
    components: {
        'navigation-bar': NavigationBar,
        'dash-board': DashBoard
    }
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
