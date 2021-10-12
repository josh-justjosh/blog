---
layout: page
permalink: /phantomradio/graph
---

<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.5.1/chart.js" integrity="sha512-b3xr4frvDIeyC3gqR1/iOi6T+m3pLlQyXNuvn5FiRrrKiMUJK3du2QqZbCywH6JxS5EOfW0DY0M6WwdXFbCBLQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<script src="https://cdn.jsdelivr.net/npm/chartjs-adapter-date-fns/dist/chartjs-adapter-date-fns.bundle.min.js"></script>

<div>
    <canvas id="listenersChart"></canvas>
</div>

<script>
const chartoptions = {
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
            },
            type: 'logarithmic',
        }
    },
    aspectRatio: 1.5,
    spanGaps: true,
}
const listeners = {{ site.data.PhantomListeners | jsonify }}
const listenersconfig = {
    type: 'line',
    data: {
        datasets:[{
            label: 'Listeners',
            backgroundColor: '#7CB342',
            borderColor: '#7CB342',
            data: listeners,
            parsing: {
                yAxisKey: 'listeners',
                xAxisKey: 'time'
            }
        }]
    },
    options: chartoptions
};
var listnersChart = new Chart(
    document.getElementById('listenersChart'),
    listenersconfig
);
</script>