<template>
    <div>
        <navigation-bar></navigation-bar>
    </div>
    <div id="pie-chart">
        <pie-chart :data="chartData" :options="chartOptions"></pie-chart>
    </div>
</template>

<script>
// import axios from 'axios';

import NavigationBar from './components/layouts/TheNavigationBar.vue';
import PieChart from './pages/pie-chart';

export default {
    name: 'App',
    components: {
        'navigation-bar': NavigationBar,
        'pie-chart': PieChart
    },
    
    data() {
        return {
            chartOptions: {
                hoverBorderWidth: 20
            },
            chartData: {
                hoverBackgroundColor: "red",
                hoverBorderWidth: 10,
                labels: ["Green", "Red", "Blue"],
                datasets: [
                {
                    label: "Data One",
                    backgroundColor: ["#41B883", "#E46651", "#00D8FF"],
                    data: [1, 10, 5]
                }
                ]
            }
        };
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
