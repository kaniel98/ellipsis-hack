<script>
import { h } from 'vue';

import { Doughnut } from 'vue-chartjs';

import { Chart as ChartJS, Title, Tooltip, Legend, ArcElement, CategoryScale } from 'chart.js';

ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale);

export default {
    name: 'PieChart',
    components: {
        Doughnut
    },
    props: {
        chartId: {
            type: String,
            default: 'doughnut-chart'
        },
        width: {
            type: Number,
            default: 400
        },
        height: {
            type: Number,
            default: 400
        },
        cssClasses: {
            default: '',
            type: String
        },
        styles: {
            default: {}
        },
        plugins: {
            default: []
        },
        chartData: {
            type: Object,
            default: () => ({
                labels: [],
                datasets: []
            })
        },
        chartOptions: {
            type: Object,
            default: () => ({
                labels: [],
                datasets: []
            })
        }
    },

    setup(props) {
        return () =>
            h(Doughnut, {
                chartData: props.chartData,
                chartOptions: props.chartOptions,
                chartId: props.chartId,
                width: props.width,
                height: props.height,
                cssClasses: props.cssClasses,
                styles: props.styles,
                plugins: props.plugins
            });
    }
};
</script>
