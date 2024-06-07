<template>
    <div class="person">
        <h2>一辆{{ car.brand }}车，价值{{ car.price }}万</h2>
        <button @click="changePrice">修改汽车的价格</button>
        <ul>
            <li v-for="g in games" :key="g.id">{{ g.name }}</li>
        </ul>
        <button @click="changeFirstName">修改第一个游戏的名字</button>
    </div>
</template>

<!-- <script lang="ts">
export default {
    name: "Person",
};
</script> -->

<script lang="ts" setup name="Person">
import { ref } from 'vue';
import {reactive} from 'vue'
let name = ref('张三')
let car = reactive({brand: '奔驰', price: 100})
let games = reactive([
    {id:'aystudy01', name: '王者'},
    {id:'aystudy02', name:'原神'},
    {id:'aystudy03',name:'三国'}
])
function changeName(){
    name.value = 'zhagn-san'
}
function changePrice(){
    car.price += 10
}
function changeFirstName(){
    games[0].name = '王者荣耀'
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