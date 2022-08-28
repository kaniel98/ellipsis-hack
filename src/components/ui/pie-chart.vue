<script>
import { Doughnut } from 'vue-chartjs';

import { Chart as ChartJS, Title, Tooltip, Legend, ArcElement, CategoryScale, Plugin } from 'chart.js';

ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale);

export default {
    name: 'PieChart',
    components: {
        Doughnut
    },
    props: ['data', 'options'],
    mounted() {
        // this.chartData is created in the mixin.
        // If you want to pass options please create a local options object
        this.renderChart(
            this.data,
            {
                borderWidth: '10px',
                hoverBackgroundColor: 'red',
                hoverBorderWidth: '10px'
            },
            this.options,
            {
                hoverBorderWidth: 20
            }
        );
    }
};
</script>
