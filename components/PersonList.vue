<template>
  <div>
    <li v-for="person in persons" :key="person.id" class="person-list">
      <span>{{ person.name }}: </span>
      <span>age: {{ person.age }}</span>
      <button class="del" @click="del(person.id)">DELETE</button>
    </li>
  </div>
</template>

<script lang="ts">
import { Component, Emit, Prop, Vue } from 'vue-property-decorator';
import { personInterface } from '@/components/Persons.vue'

@Component
export default class PersonsView extends Vue {
  @Prop() persons!: personInterface[]
  @Emit()
  del(id: number) {
    return id
  }
}
</script>

<style scoped>
.person-list {
  list-style: none;
  margin-bottom: 12px;
  border-radius: 4px;
  font-size: 20px;
  display: flex;
  justify-content: space-between;
  background-color: #f7f7ac;
  padding: 8px 20px;
  width: 300px;
  font-weight: bold;
}
</style>