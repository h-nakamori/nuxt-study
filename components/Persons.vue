<template>
  <div class="container">
    <h1>Regist Person Data</h1>
    <div class="link"><router-link to="/">Top</router-link></div>
    <person-post-form @define-emits="receiveRegist" />
    <div class="list-container">
      <ul>
        <person-list :persons="persons" @del="receiveDelete" />
      </ul>
      <p v-if="persons.length < 1">No Person-data has been registerd</p>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import PersonList from '@/components/PersonList.vue';
import PersonPostForm from '@/components/PersonPostForm.vue'

//インターフェースってここに書けばよかったのね@@
export interface personInterface {
  id: number,
  name: string,
  age: number
}

@Component({
  components: {
    PersonList,
    PersonPostForm,
  },
})
export default class Persons extends Vue {
  //メモ帳アプリもこうすればよかったのね…
  public persons: personInterface[] = [];

  receiveRegist(e: personInterface) {
    this.persons.push(e);
  }
  receiveDelete(id: number) {
    if (confirm("Are you sure you want to delete this?")) {
      this.persons = this.persons.filter(p => p.id !== id)
    }
  }
}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

p {
  font-weight: bold;
  color: #2c3e508f;
}

.link {
  text-align: center;
  margin-bottom: 25px;
}
</style>