<template>
    <div class="person">
        <h2>姓名：{{ person.name }}</h2>
        <h2>年龄：{{ person.age }},{{ nl }}</h2>
        <button @click="changeName">点击修改名字</button>
        <button @click="changeAge">点击修改年龄</button>
    </div>
</template>

<!-- <script lang="ts">
export default {
    name: "Person",
};
</script> -->

<script lang="ts" setup name="Person">
import { toRefs,reactive, toRef } from 'vue';

let person = reactive({
    name:'张三',
    age:18
})
let {name, age} = toRefs(person)
let nl = toRef(person, 'age')
function changeName(){
    name.value += '~'
}
function changeAge(){
    age.value += 1
}

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
li{
    font-size: 20px;
}
</style>