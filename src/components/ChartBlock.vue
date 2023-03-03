<template>
  <div class="chart-block">
    <div class="chart-block__title">
      <span>Sales</span>
      <span class="chart-block__info"></span>
    </div>
    <div class="chart-block__line">
      <Line id="my-chart-id" :options="chartOptions" :data="chartData" />
    </div>
  </div>
</template>

<script>
import { Line } from "vue-chartjs";
import { Chart as ChartJS, CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend, Filler } from "chart.js";

ChartJS.register(CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend, Filler);

export default {
  name: "ChartBlock",
  components: {
    Line,
  },
  data() {
    return {
      showY: true,
      chartData: {
        labels: [],
        datasets: [
          {
            data: [120, 100, 50, 150, 110, 90, 160],
            backgroundColor: (ctx) => {
              const canvas = ctx.chart.ctx;
              const gradient = canvas.createLinearGradient(0, 0, 0, 450);

              gradient.addColorStop(0, "rgba(28, 100, 242, 0.9)");
              gradient.addColorStop(0.5, "rgba(28, 100, 242, 0.08)");
              gradient.addColorStop(1, "rgba(28, 100, 242, 0)");

              return gradient;
            },
            borderColor: "rgba(28, 100, 242, 1)",
            cubicInterpolationMode: "monotone",
            fill: true,
            pointBackgroundColor: "rgba(28, 100, 242, 0)",
            pointBorderWidth: 3,
            pointBorderColor: "rgba(255, 255, 255, 0)",
            pointHoverBackgroundColor: "rgba(28, 100, 242, 1)",
            pointHoverBorderColor: "rgba(255, 255, 255, 1)",
            pointHoverBorderWidth: 3,
          },
        ],
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false,
        layout: {
          padding: {
            left: -50,
            right: 25,
          },
        },
        scales: {
          y: {
            display: () => {
              return this.showY;
            },
            max: 240,
            min: 0,
            border: {
              color: "rgba(243, 244, 246, 0)",
            },
            ticks: {
              padding: 50,
              font: {
                size: 14,
                weight: "600",
              },
              callback: (i) => i + "K",
            },
            afterFit: (axis) => {
              axis.paddingTop = 0;
              axis.paddingBottom = 0;
            },
          },
          x: {
            ticks: {
              padding: () => {
                if (this.showY) {
                  return 32;
                } else {
                  return 0;
                }
              },
              font: {
                size: 14,
                weight: "600",
              },
            },
            afterFit: (axis) => {
              if (this.showY) {
                axis.paddingRight = 0;
                axis.paddingLeft = 0;
              }
            },
          },
        },
        plugins: {
          legend: {
            display: false,
          },
          title: {
            text: "Custom Chart Title",
          },
          tooltip: {
            enabled: false,
            external: (context) => {
              let tooltipEl = document.getElementById("chartjs-tooltip");

              if (!tooltipEl) {
                tooltipEl = document.createElement("div");
                tooltipEl.id = "chartjs-tooltip";
                tooltipEl.innerHTML = "<table></table>";
                document.body.appendChild(tooltipEl);
              }

              const tooltipModel = context.tooltip;
              if (tooltipModel.opacity === 0) {
                tooltipEl.style.opacity = 0;
                return;
              }

              tooltipEl.classList.remove("above", "below", "no-transform");
              if (tooltipModel.yAlign) {
                tooltipEl.classList.add(tooltipModel.yAlign);
              } else {
                tooltipEl.classList.add("no-transform");
              }

              function getBody(bodyItem) {
                return bodyItem.lines;
              }

              if (tooltipModel.body) {
                const titleLines = tooltipModel.title || [];
                const bodyLines = tooltipModel.body.map(getBody);

                let innerHtml = "<thead>";

                titleLines.forEach(function (title) {
                  innerHtml += "<tr><th class='tooltip-title'>" + title + " 2021</th></tr>";
                });
                innerHtml += "</thead><tbody>";

                bodyLines.forEach(function (body, i) {
                  const span = "<span>" + body + "</span>";
                  innerHtml += "<tr class='tr-tooltip'><td><span class='type-tooltip'></span></td><td class='price-tooltip'>$" + span + "k</td></tr>";
                });
                innerHtml += "</tbody>";

                let tableRoot = tooltipEl.querySelector("table");
                tableRoot.innerHTML = innerHtml;
              }

              const position = context.chart.canvas.getBoundingClientRect();

              tooltipEl.style.opacity = 1;
              tooltipEl.style.background = "#fff";
              tooltipEl.style.width = "148px";
              tooltipEl.style.height = "94px";
              tooltipEl.style.boxShadow = "0px 1px 2px rgba(0, 0, 0, 0.06), 0px 1px 3px rgba(0, 0, 0, 0.1)";
              tooltipEl.style.position = "absolute";
              tooltipEl.style.borderRadius = "15px";
              tooltipEl.style.left = position.left + window.pageXOffset + tooltipModel.caretX - 70 + "px";
              tooltipEl.style.top = position.top + window.pageYOffset + tooltipModel.caretY - 140 + "px";
              tooltipEl.style.padding = "11px";
              tooltipEl.style.pointerEvents = "none";
            },
          },
        },
      },
    };
  },
  mounted() {},
  created() {
    let widthScreen = document.querySelector("#app").clientWidth;

    if (widthScreen >= 768) {
      this.showY = true;
    } else {
      this.showY = false;
    }

    for (let i = 1; i < 8; i++) {
      this.chartData.labels.push(`0${i} Apr`);
    }
  },
};
</script>

<style lang="scss">
.chart-block {
  width: 100%;
  height: 570px;
  padding: 62px 32px 32px;
  background: #fff;
  box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.06), 0px 1px 3px rgba(0, 0, 0, 0.1);
  border-radius: 16px;

  &__title {
    display: flex;
    align-items: center;

    span {
      font-weight: 700;
      font-size: 20px;
    }
  }

  &__info {
    width: 24px;
    height: 24px;
    margin-left: 13px;
    background: url("@/assets/img/exclamation-circle.svg") no-repeat;
  }

  &__line {
    height: 411px;
    margin-top: 55px;
  }
}

.tooltip-title {
  font-size: 11px;
  font-weight: 500;
  color: #4b5563;
}

.price-tooltip {
  display: inline-block;
  font-weight: 600;
  font-size: 16px;
  margin-left: 5px;
}

.type-tooltip {
  display: block;
  width: 10px;
  height: 10px;
  background: #1c64f2;
  border-radius: 100%;
}

.tr-tooltip {
  display: flex;
  align-items: center;
}

#chartjs-tooltip {
  background: #000;
}
</style>
