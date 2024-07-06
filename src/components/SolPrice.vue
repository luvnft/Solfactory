<template>
  <div class="solana-price">
    <p>Solana Price: {{ price !== null ? `$${price}` : 'Loading...' }}</p>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';

const price = ref<number | null>(null);

const fetchPrice = async () => {
  try {
    const response = await fetch('https://api.coingecko.com/api/v3/simple/price?ids=solana&vs_currencies=usd');
    const data = await response.json();
    price.value = data.solana.usd;
    console.log('Fetched price:', price.value); // Debug log to ensure fetch is working
  } catch (error) {
    console.error('Error fetching the price:', error);
  }
};

onMounted(() => {
  fetchPrice();
  setInterval(fetchPrice, 60000); // Update every minute
});
</script>

<style scoped>
.solana-price {
  color: white;
    font-family: monospace;
    font-weight: 100;
    position: absolute;
    top: 0;
    left: 0;
}
</style>