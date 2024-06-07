<template>
    <div class="person">
        <h2>一辆{{ car.brand }}车，价值{{ car.price }}万</h2>
        <button @click="changeBrand">修改汽车的品牌</button>
        <button @click="changePrice">修改汽车的价格</button>
        <button @click="changeCar">修改汽车</button>
        <hr/>
        <h2>当前sum为{{ sum }}</h2>
        <button @click="changeSum">点我sum+1</button>
    </div>
</template>

<!-- <script lang="ts">
export default {
    name: "Person",
};
</script> -->

<script lang="ts" setup name="Person">
import { ref,reactive } from 'vue';

let sum = ref(0)
let car = ref({brand: '奔驰', price: 100})
function changeBrand(){
    car.value.brand = '宝马'
}
function changePrice(){
    car.value.price += 10
}
function changeCar(){
    // car = {brand: '雅迪', price: 0.2} // 会导致失去响应式
    // car = reactive({brand: '雅迪', price: 0.2}) // 会导致原来的绑定关系断开
    // Object.assign(car, {brand: '雅迪', price: 0.2}) // reactive可用此方法更新整个对象
    car.value = {brand: '雅迪', price: 0.2}
}
function changeSum(){
    sum.value += 1
    // sum = ref(9) // 不可行
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