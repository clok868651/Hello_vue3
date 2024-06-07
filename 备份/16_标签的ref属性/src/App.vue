<template>
<div class="app">
    <h2 ref="title2">你好</h2>
    <button @click="showLog">点我输出h2</button>
    <Person ref="ren"/>
</div>
</template>

<script lang="ts" setup name="App">
import Person from './components/Person.vue'
import {ref} from 'vue'

let title2 = ref()
let ren = ref()
function showLog(){
    console.log(ren.value)
}
</script>

<style>

</style>