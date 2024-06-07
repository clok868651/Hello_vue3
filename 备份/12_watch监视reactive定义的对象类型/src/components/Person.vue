<template>
    <div class="person">
        <h1>情况三：监视【reactive】定义的【对象类型】的数据</h1>
        <h2>姓名：{{ person.name }}</h2>
        <h2>年龄：{{ person.age }}</h2>
        <button @click="changeName">修改名字</button>
        <button @click="changeAge">修改年龄</button>
        <button @click="changePerson">修改个人信息</button>
    </div>
</template>

<!-- <script lang="ts">
export default {
    name: "Person",
};
</script> -->

<script lang="ts" setup name="Person">
import { reactive, watch } from 'vue'

let person = reactive({
    name: '张三',
    age: 18
})
function changeName() {
    person.name += '~'
}

function changeAge() {
    person.age += 1
}

function changePerson() {
    Object.assign(person, { name: '李四', age: 60 })
}
// 监视，情况三：监视【reactive】定义的【对象类型】数据，默认开启深度监视，无法关闭(不监视地址修改)
watch(person, (newPerson, oldPerson) => {
    console.log("person变了", newPerson, oldPerson)
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