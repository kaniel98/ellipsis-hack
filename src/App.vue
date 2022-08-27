<template>
    <div>
        <navigation-bar></navigation-bar>
    </div>
</template>

<script>
import NavigationBar from './components/layouts/TheNavigationBar.vue';

export default {
    name: 'App',
    components: {
        'navigation-bar': NavigationBar
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
