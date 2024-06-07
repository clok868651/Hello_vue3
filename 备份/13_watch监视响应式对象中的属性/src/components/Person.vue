<template>
    <div class="person">
        <h2>姓名：{{ person.name }}</h2>
        <h2>年龄：{{ person.age }}</h2>
        <h2>汽车：{{ person.car.c1 }}、{{ person.car.c2 }}</h2>
        <button @click="changeName">修改名字</button>
        <button @click="changeAge">修改年龄</button>
        <button @click="changeFirstCar">修改第一辆汽车</button>
        <button @click="changeSecondCar">修改第二辆汽车</button>
        <button @click="changeAllCar">修改所有车</button>
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
    age: 18,
    car:{
        c1:'奔驰',
        c2:'宝马'
    }
})

function changeName(){
    person.name += '~'
}

function changeAge(){
    person.age += 1
}

function changeFirstCar(){
    person.car.c1 = '奥迪'
}

function changeSecondCar(){
    person.car.c2 = '大众'
}

function changeAllCar(){
    person.car = {c1: '雅迪', c2: '爱玛'}
}
// 监视，情况四：监视响应式对象中的某个属性，且该属性为基本类型，要写成函数式
// watch(()=>person.name, (newValue, oldValue)=>{
//     console.log('person变化', newValue, oldValue)
// })
// 监视，情况四：监视响应式对象中的某个属性，且该属性是对象类型，可以直接写，也能写函数，更推荐函数
watch(()=>person.car, (newValue, oldValue)=>{
    console.log('person的car变化', newValue, oldValue)
}, {deep:true})

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