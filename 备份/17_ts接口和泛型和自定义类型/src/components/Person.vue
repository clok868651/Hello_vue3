<template>
  <div class="person">

  </div>
</template>

<script lang="ts" setup name="Person">
import { type PersonInter, type Persons} from '@/types'

// let person: PersonInter = { id: 'asdwaascxa01', name: '张三', age: 60 }
let personList:Persons = [
  {id: 'asdwaascxa01', name: '张一', age: 40},
  {id: 'asdwaascxa02', name: '张二', age: 50},
  {id: 'asdwaascxa03', name: '张三', age: 60}
]
</script>

<style scoped>
.person {
  background-color: skyblue;
  box-shadow: 0 0 10px;
  border-radius: 10px;
  padding: 20px;
}

button {
  margin: 0 5px;
}

li {
  font-size: 20px;
}
</style>