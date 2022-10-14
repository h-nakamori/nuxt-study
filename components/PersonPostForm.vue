<template>
  <div class="form-container">
    <div class="input-container">
      <span class="invalid-msg" v-if="!isValidName">
        Please input 15 chars or less
      </span>
      <div class="input-column">
        <span>name:</span>
        <input
          v-model="inputtingName"
          type="text"
          :class="{ notValid: !isValidName }"
          placeholder="*Required"
        />
      </div>
      <span class="invalid-msg" v-if="!isValidAge">error: invalid value</span>
      <div class="input-column">
        <span>age:</span>
        <input
          v-model="inputtingAge"
          type="number"
          class="input"
          :class="{ notValid: !isValidAge }"
        />
      </div>
    </div>
    <button
      @click="defineEmits"
      class="register-button"
      :disabled="!isValidName || !isValidAge || isEmpty"
    >
      POST
    </button>
  </div>
</template>

<script lang="ts">

import { Component, Emit, Vue } from 'vue-property-decorator';
import { personInterface } from '@/components/Persons.vue'
@Component
export default class PersonPostForm extends Vue {
  inputtingName = "";
  inputtingAge = 0;
  register() {
    console.log()
  }
  @Emit()
  defineEmits(): personInterface {
    const person = { id: Math.random(), name: this.inputtingName, age: this.inputtingAge }
    return person
  }
  get isValidName() {
    if (this.inputtingName.length > 15) {
      return false
    }
    return true
  }
  get isValidAge() {
    if (this.inputtingAge < 0 || this.inputtingAge > 99) {
      return false
    }
    return true
  }
  get isEmpty() {
    return this.inputtingName.length == 0;
  }
}
</script>

<style scoped>
.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: azure;
  padding: 24px 0;
  width: 50%;
  margin-bottom: 12px;
  border-radius: 4px;
}

span {
  font-size: 20px;
  font-weight: bold;
}

.input-container {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  height: 50px;
  margin-bottom: 20px;
}

.input-column {
  width: 200px;
  display: flex;
  justify-content: space-between;
}

input {
  width: 120px;
  margin-bottom: 8px;
}

.notValid {
  background-color: rgb(255, 146, 146);
}

.invalid-msg {
  font-size: 12px;
  color: rgb(255, 146, 146);
}
</style>