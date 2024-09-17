<template>
  <div id="container"></div>
</template>

<script setup lang="ts">
import { onMounted, watch } from 'vue';
import { Chart } from '@antv/g2';

const colorArr = ['#00cdff', '#ff702c']

interface Props {
  data: Array;
}

const props = withDefaults(defineProps<Props>(), {
  data: () => []
});

const initChart = () => {

  const chart = new Chart({
    container: 'container',
    autoFit: true,
    height: 500,
  });
  const innerView = chart.createView({
    start: { x: 0, y: 0 },
    end: { x: 0.5, y: 0.5 },
    padding: 8,
  });
  const innerView2 = chart.createView({
    start: { x: 0, y: 0 },
    end: { x: 0.5, y: 0.5 },
    padding: 8,
  });
  innerView.data(props.data);
  innerView.scale('score', {
    min: 0,
    // max: 80,
  });
  innerView.coordinate('polar', {
    radius: 0.83,
  });

  innerView.axis('item', {
    line: null,
    tickLine: null,
    grid: {
      line: {
        style: {
          lineDash: null,
        },
      },
    },
    label: {
      formatter: (e, i) => `${e}${JSON.stringify(i)}`,
      offsetY: -15,
      offsetX: -15,
      style: {
        fill: 'green'
      }
    }
  });
  innerView
    .line()
    .position('item*score')
    .color('user', colorArr)
    .size(0);
  innerView.render();

  innerView2.data(props.data);
  innerView2.scale('score', {
    min: 0,
    // max: 80,
  });
  innerView2.coordinate('polar', {
    radius: 0.83,
  });

  innerView2.axis('item', {
    line: null,
    tickLine: null,
    grid: {
      line: {
        style: {
          lineDash: null,
        },
      },
    },
    label: {
      offsetY: -15,
      offsetX: 15,
      style: {
        fill: 'red'
      }
    }
  });
  innerView2
    .line()
    .position('item*score')
    .color('user', colorArr)
    .size(0);
  innerView2.render();

  chart.data(props.data);
  chart.scale('score', {
    min: 0,
    // max: 80,
  });
  chart.coordinate('polar', {
    radius: 0.8,
  });
  chart.tooltip({
    shared: true,
    showCrosshairs: true,
    crosshairs: {
      line: {
        style: {
          lineDash: [4, 4],
          stroke: '#333'
        }
      }
    }
  });
  chart.axis('item', {
    line: null,
    tickLine: null,
    grid: {
      line: {
        style: {
          lineDash: null,
        },
      },
    },
    label: {
      // offset: 20,
      // offsetY: -25,
      // offsetX: -5,
      style: {
        fill: '#e5e5e5'
      }
    }
  });
  chart.axis('score', {
    line: null,
    tickLine: null,
    grid: {
      line: {
        type: 'line',
        style: {
          lineDash: null,
          stroke: 'rgba(0, 232, 255, 0.2)'
        },
      },
    },
    label: null
  });

  // chart.annotation().text({
  //   position: ['0%', '100%'],
  //   content: 'ee'
  // })

  chart
    .line()
    .position('item*score')
    .color('user', colorArr)
    .size(2);
  chart
    .point()
    .position('item*score')
    .color('user', colorArr)
    .shape('circle')
    .size(4)
    .style({
      stroke: '#fff',
      lineWidth: 1,
      fillOpacity: 1,
    });
  chart
    .area()
    .position('item*score')
    .color('user', colorArr);
  chart.render();
}

onMounted(() => {
  initChart()
})
</script>