<template>
  <div class="container">
    <NuxtLogo />
    <hello-world />
    <router-link to="/PersonsView">Person</router-link>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from '@/components/HelloWorld.vue'
import NuxtLogo from '@/components/NuxtLogo.vue'

@Component
export default class extends Vue {

}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>