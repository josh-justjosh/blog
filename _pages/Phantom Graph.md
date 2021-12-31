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
<script src="https://cdnjs.cloudflare.com/ajax/libs/hammer.js/2.0.8/hammer.min.js" integrity="sha512-UXumZrZNiOwnTcZSHLOfcTs0aos2MzBWHXOHOuB0J/R44QB0dwY5JgfbvljXcklVf65Gc4El6RjZ+lnwd2az2g==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/chartjs-plugin-zoom/1.2.0/chartjs-plugin-zoom.min.js" integrity="sha512-TT0wAMqqtjXVzpc48sI0G84rBP+oTkBZPgeRYIOVRGUdwJsyS3WPipsNh///ay2LJ+onCM23tipnz6EvEy2/UA==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>

<script>
var chart = new Chart(document.getElementById('myChart'), {
    type: 'line',
    data: {
        datasets: [{
            label: 'Listeners',
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
            zoom: {
                pan: {
                    enabled: true,
                    mode: 'xy',
                },
                zoom: {
                    mode: 'xy',
                    wheel: {
                        enabled: true
                    },
                    pinch: {
                        enabled: true
                    },
                    drag: {
                        enabled: true
                    }
                }
            },
            legend: {
                display: false
            }, 
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