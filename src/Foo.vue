<script lang="ts" setup>
import { ref } from 'vue';

const arr = ref(new Array(20000000).fill(1))
</script>

<template>
  <div class="link" @click="$emit('change', 'Bar')">Go to Bar{{ arr.length }}</div>
</template>