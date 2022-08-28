<script>
import { h } from 'vue';

import { Line } from 'vue-chartjs';

import { Chart as ChartJS, Title, Tooltip, Legend, LineElement, LinearScale, PointElement, CategoryScale } from 'chart.js';

ChartJS.register(Title, Tooltip, Legend, LineElement, LinearScale, PointElement, CategoryScale);

export default {
    name: 'LineChart',
    components: {
        Line
    },
    props: {
        chartId: {
            type: String,
            default: 'line-chart'
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
        lineData: {
            type: Object,
            default: () => ({
                labels: [],
                datasets: []
            })
        },
        lineOptions: {
            type: Object,
            default: () => ({
                labels: [],
                datasets: []
            })
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
            h(Line, {
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
