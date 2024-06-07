<template>
  <div class="person">
    <h2>当前水温：{{ temp }}℃</h2>
    <h2>当前水位：{{ height }}cm</h2>
    <button @click="changeTemp">水温+10</button>
    <button @click="changeHeight">水位+10</button>
  </div>
</template>

<!-- <script lang="ts">
export default {
    name: "Person",
};
</script> -->

<script lang="ts" setup name="Person">
import { ref, watch, watchEffect } from "vue";

let temp = ref(10);
let height = ref(0);

function changeTemp() {
  temp.value += 10;
}
function changeHeight() {
  height.value += 10;
}

// watch([temp, height],(value)=>{
//     let [newTemp, newHeight] = value
//     if(newTemp >= 60 || newHeight >= 80)
//     {
//         console.log('发送请求')
//     }
// })

watchEffect(()=>{
    if(temp.value >= 60 || height.value >= 80)
    {
        console.log('发送请求')
    }
})
</script>

<style>
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