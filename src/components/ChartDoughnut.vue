<script>
import { Doughnut } from 'vue-chartjs'

export default {
  extends: Doughnut,
  name: 'ChartDoughnut',
  props: {
    chartdata: Object,
    options: Object,
  },
  mounted () {
    this.renderChart(this.chartdata, this.options)
  }
}
</script>