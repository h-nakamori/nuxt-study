<template>
  <div class="container">
    <NuxtLogo />

    <persons />
  </div>
</template>
<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Persons from '@/components/Persons.vue';
@Component({
  components: {
    Persons
  },
})
export default class PersonsView extends Vue {
}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-content: center;
}
</style>