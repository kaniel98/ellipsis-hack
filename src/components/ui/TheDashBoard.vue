<template>
    <box-container :columnLength="3">
        <template v-slot:GraphContent>
            <div id="pie-chart" class="base-bg">
                <pie-chart :chartData="chartData" :options="chartOptions"></pie-chart>
            </div>
        </template>
    </box-container>
</template>

<script>
import { reactive, toRefs } from '@vue/reactivity';
import PieChart from './pie-chart.vue';
import BoxContainer from './BoxContainer.vue';

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
            }
        });

        return { ...toRefs(state) };
    },

    components: {
        'pie-chart': PieChart,
        'box-container': BoxContainer
    },

    name: 'DashBoard'
};
</script>
