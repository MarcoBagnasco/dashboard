<script>
import { Line } from 'vue-chartjs'

export default {
  extends: Line,
  name: 'ChartLine',
  props: {
    chartdata: Object,
    options: Object,
  },
  mounted () {
    this.renderChart(this.chartdata, this.options)
  }
}
</script>