<template>
    <div class="person">
        <h1>情况一：监视【ref】定义的【基本类型】的数据</h1>
        <h2>当前求和为：{{ sum }}</h2>
        <button @click="changeSum">点我sum+1</button>
        <hr />
        <h1>情况二：监视【ref】定义的【对象类型】的数据</h1>
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
import { ref, watch } from 'vue'

let sum = ref(0)
function changeSum() {
    sum.value += 1
}

const stopWatch = watch(sum, (newValue, oldValue) => {
    console.log('sum变化了', newValue, oldValue)
    if (newValue >= 10) {
        stopWatch()
    }
})

/** ========================= */
let person = ref({
    name: '张三',
    age: 18
})
function changeName() {
    person.value.name += '~'
}

function changeAge() {
    person.value.age += 1
}

function changePerson() {
    person.value = { name: '李四', age: 60 }
}
/** 监视，情况一：监视【ref】定义的【对象类型】数据，监视的是对象的地址值，若想监视对象内部属性变化，需要手动开启深度监视
    watch的第一个参数是：被监视的数据
    watch的第二个参数是：被监视的回调
    watch的第三个参数是：配置对象（deep， immediate） */
watch(person, (newPerson, oldPerson) => {
    console.log("person变了", newPerson, oldPerson)
}, { deep: true })
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