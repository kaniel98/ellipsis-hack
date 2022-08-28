<template>
    <div id="pie-chart">
        <pie-chart :data="chartData" :options="chartOptions"></pie-chart>
    </div>
</template>

<script>
import { reactive, toRefs } from '@vue/reactivity';
import PieChart from './pie-chart.vue';


export default {
    setup() {
        const state = reactive({
            chartOptions: {
                hoverBorderWidth: 20
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
            }
        });

        return { ...toRefs(state) };
    },

    components: {
        "pie-chart": PieChart
    },

    name: "DashBoard"
};
</script>
