<template>
<div class="app">
    <Person a="哈哈" :list="undefined"/>
</div>
</template>

<script lang="ts" setup name="App">
import Person from './components/Person.vue'
import { reactive } from 'vue';
import { type Persons } from './types';

let personList = reactive<Persons>([
  {id: 'asdwaascxa01', name: '张一', age: 40},
  {id: 'asdwaascxa02', name: '张二', age: 50},
  {id: 'asdwaascxa03', name: '张三', age: 60}
])
</script>

<style>

</style>