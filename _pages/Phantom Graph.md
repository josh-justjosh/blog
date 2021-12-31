---
layout: page
permalink: /phantomradio/graph
title: Phantom Radio Listeners Graph
---

<div>
  <canvas id="Chart24h"></canvas>
</div>
<div>
  <canvas id="Chart7d"></canvas>
</div>
<div>
  <canvas id="Chart28d"></canvas>
</div>
<div>
  <canvas id="Chartall"></canvas>
</div>

<script src="https://cdn.jsdelivr.net/npm/chart.js/dist/chart.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/chartjs-adapter-date-fns/dist/chartjs-adapter-date-fns.bundle.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/hammer.js/2.0.8/hammer.min.js" integrity="sha512-UXumZrZNiOwnTcZSHLOfcTs0aos2MzBWHXOHOuB0J/R44QB0dwY5JgfbvljXcklVf65Gc4El6RjZ+lnwd2az2g==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/chartjs-plugin-zoom/1.2.0/chartjs-plugin-zoom.min.js" integrity="sha512-TT0wAMqqtjXVzpc48sI0G84rBP+oTkBZPgeRYIOVRGUdwJsyS3WPipsNh///ay2LJ+onCM23tipnz6EvEy2/UA==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>

<script>
let hours24 = new Date();
let days7 = new Date();
let days28 = new Date();

hours24.setDate(hours24.getDate() - 1); // set to 'now' minus 1 days.

days7.setDate(days7.getDate() - 7); // set to 'now' minus 7 days.
days7.setHours(0, 0, 0, 0); // set to midnight.

days28.setDate(days28.getDate() - 28); // set to 'now' minus 7 days.
days28.setHours(0, 0, 0, 0); // set to midnight.

var chart24h = new Chart(document.getElementById('Chart24h'), {
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
            title: {
                display: true,
                text: 'Last 24 hours',
                font: {
                        size: 20
                    }
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
                },
                min: hours24,
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

var chart7d = new Chart(document.getElementById('Chart7d'), {
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
            title: {
                display: true,
                text: 'Last 7 days',
                font: {
                        size: 20
                    }
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
                },
                min: days7,
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

var chart28d = new Chart(document.getElementById('Chart28d'), {
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
            title: {
                display: true,
                text: 'Last 28 days',
                font: {
                        size: 20
                    }
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
                },
                min: days28,
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
var chartall = new Chart(document.getElementById('Chartall'), {
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
            title: {
                display: true,
                text: 'All Time',
                font: {
                        size: 20
                    }
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
                    minUnit: 'week',
                },
                ticks: {
                    major: {
                        enabled: true,
                    },
                },
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
