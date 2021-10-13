---
layout: page
permalink: /phantomradio/graph
title: Phantom Radio Listeners Graph
---

<div>
  <canvas id="myChart"></canvas>
</div>

<script src="https://cdn.jsdelivr.net/npm/chart.js/dist/chart.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/chartjs-adapter-date-fns/dist/chartjs-adapter-date-fns.bundle.min.js"></script>
<script>
var chart = new Chart(document.getElementById('myChart'), {
    type: 'line',
    data: {
        datasets: [{
            label: 'Data',
            backgroundColor: 'rgb(255, 99, 132)',
            borderColor: 'rgb(255, 99, 132)',
            data: {{ site.data.PhantomListeners | jsonify }},
            parsing: {
                yAxisKey: 'listeners',
                xAxisKey: 'time'
            }
        }],
    },
    options: {
        plugins: {
            legend: {
                display: false
                }
            },
        scales: {
        x: {
            type: 'time',
            title: {
                text: 'Time (UTC)',
                display: false
            },
            time: {
                minUnit: 'hour',
                displayFormats: {
                    hour: 'h aaa',
                    day: 'eee'
                }
            },
            ticks: {
                major: {
                    enabled: true,
                },
            }
        },
        y: {
            beginAtZero: true,
            ticks: {
                precision: 0
            }
        }
    },
    aspectRatio: 2,
    spanGaps: true,
    }
});
</script>