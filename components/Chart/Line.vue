<script>
import { Line } from 'vue-chartjs'

export default {
  extends: Line,
  props: {
    chartdata: {
      default: () => ({
        labels: [
          'January',
          'February',
          'March',
          'April',
          'May',
          'June',
          'July',
          'August',
          'September',
          'October',
          'November',
          'December',
        ],
        datasets: [
          {
            label: 'Количество платежей',
            data: [
              {
                x: 'Первый платеж',
                y: 32,
              },
              {
                x: 'Второй платеж',
                y: 43,
              },
              {
                x: 'Третий платеж',
                y: 23,
              },
              {
                x: 'Четвертый платеж',
                y: 17,
              },
              {
                x: 'Пятый платеж',
                y: 64,
              },
              {
                x: 'Шестой платеж',
                y: 32,
              },
              {
                x: 'Седьмой платеж',
                y: 54,
              },
              {
                x: 'Восьмой платеж',
                y: 34,
              },
              {
                x: 'Девятый платеж',
                y: 32,
              },
              {
                x: 'Десятый платеж',
                y: 54,
              },
              {
                x: 'Одиннадцатый платеж',
                y: 23,
              },
              {
                x: 'Двенадцатый платеж',
                y: 45,
              },
              {
                x: 'Тринадцатый платеж',
                y: 32,
              },
            ],
            borderWidth: 1,
          },
        ],
      }),
    },
  },
  mounted() {
    this.renderChart(this.chartdata, this.options)
  },
}
</script>
