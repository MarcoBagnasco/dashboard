<script>
import { Line /*, mixins*/} from 'vue-chartjs';
// const { reactiveProp } = mixins;

export default {
  extends: Line,
  // mixins: [reactiveProp],
  name: 'ChartLine',
  props: {
    chartData: Object,
    options: Object,
  },
  data(){
    return{ 
      dataChange: this.chartData.datasets[0].data,
    }
  },
  mounted () {
    this.render();
  },
  watch:{
    'dataChange' : 'render'
  },
  methods:{
    render(){
      this.renderChart(this.chartData, this.options);
    }
  }
}
</script>