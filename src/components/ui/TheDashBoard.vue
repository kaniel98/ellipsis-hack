<template>
    <div class="container-fluid base-bg">
        <div class="row">
            <box-container :columnLength="3">
                <template v-slot:GraphContent>
                    <div id="pie-chart">
                        <pie-chart :chartData="chartData" :options="chartOptions"></pie-chart>
                    </div>
                </template>
            </box-container>
            <box-container :columnLength="3">
                <template v-slot:GraphContent>
                    <line-chart :chartData="lineData" :options="lineOptions"></line-chart>
                </template>
            </box-container>
        </div>
    </div>
</template>

<script>
import { reactive, toRefs } from '@vue/reactivity';
import PieChart from './PieChart.vue';
import BoxContainer from './BoxContainer.vue';
import LineChart from './LineGraph.vue';

export default {
    setup() {
        const state = reactive({
            chartOptions: {
                hoverBorderWidth: 20,
                responsive: true,
                maintainAspectRatio: false
            },
            chartData: {
                hoverBackgroundColor: 'red',
                hoverBorderWidth: 10,
                labels: ['Green', 'Red', 'Blue'],
                datasets: [
                    {
                        label: 'Data One',
                        backgroundColor: ['#41B883', '#E46651', '#00D8FF'],
                        data: [1, 10, 5]
                    }
                ]
            },
            lineOptions: {
                responsive: true,
                maintainAspectRatio: false
            },
            lineData: {
                labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July'],
                datasets: [
                    {
                        label: 'Data One',
                        backgroundColor: '#f87979',
                        data: [40, 39, 10, 40, 39, 80, 40]
                    }
                ]
            }
        });

        return { ...toRefs(state) };
    },

    components: {
        'pie-chart': PieChart,
        'box-container': BoxContainer,
        'line-chart': LineChart
    },

    name: 'DashBoard'
};
</script>
