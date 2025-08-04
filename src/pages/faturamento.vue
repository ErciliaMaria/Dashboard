<template>
  <v-container>
    <v-card class="pa-4" outlined>
      <v-card-title>
        Vendas Mensais
      </v-card-title>
      <v-card-text>
        <canvas ref="chartCanvas"></canvas>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import Chart from 'chart.js/auto'

// Exemplo de dados (mock)
const vendas = [
  { mes: 'Jan', valor: 1200 },
  { mes: 'Fev', valor: 980 },
  { mes: 'Mar', valor: 1500 },
  { mes: 'Abr', valor: 1700 },
  { mes: 'Mai', valor: 1100 },
  { mes: 'Jun', valor: 1900 },
]

// Referência para o canvas
const chartCanvas = ref(null)

onMounted(() => {
  const ctx = chartCanvas.value.getContext('2d')

  // map para extrair os dados
  const labels = vendas.map(v => v.mes)
  const data = vendas.map(v => v.valor)

  // forEach para exibir no console
  vendas.forEach(v => console.log(`${v.mes}: R$ ${v.valor}`))

  new Chart(ctx, {
    type: 'bar',
    data: {
      labels,
      datasets: [{
        label: 'Vendas em R$',
        data,
        backgroundColor: 'rgba(75, 192, 192, 0.8)',
      }]
    },
    options: {
      responsive: true,
      plugins: {
        title: {
          display: true,
          text: 'Gráfico de Vendas por Mês',
        },
        legend: {
          position: 'top',
        }
      }
    }
  })
})
</script>

<style scoped>
canvas {
  max-width: 100%;
}
</style>