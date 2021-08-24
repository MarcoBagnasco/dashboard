<script>
import { Bar } from 'vue-chartjs'

export default {
  extends: Bar,
  name: 'ChartBar',
  props: {
    chartdata: Object,
    options: Object,
  },
  mounted () {
    this.renderChart(this.chartdata, this.options)
  }
}
</script>