<script setup lang="ts">
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
import { useMemory } from '@vueuse/core'
import { ref } from 'vue';
import Foo from './Foo.vue'
import Bar from './Bar.vue'

const { memory } = useMemory()
const target = ref('Foo')

const onChange = (t: string) => target.value = t

</script>

<template>
  <p>{{ target }}</p>
  <p>内存：{{ memory?.usedJSHeapSize }}</p>
  <keep-alive include="Foo">
    <component :is="target === 'Foo' ? Foo : Bar" @change="onChange"></component>
  </keep-alive>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
