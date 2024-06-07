<template>
    <div class="person">
        姓：<input type="text" v-model="firstName" /><br />
        名：<input type="text" v-model="lastName" /><br />
        全名：<span>{{ fullName }}</span><br />
        <button @click="changeFullName">修改全名</button>
    </div>
</template>

<!-- <script lang="ts">
export default {
    name: "Person",
};
</script> -->

<script lang="ts" setup name="Person">
import { ref, computed } from 'vue'

let firstName = ref('张')
let lastName = ref('三')

// 只读的计算属性
// let fullName = computed(() => {
//     return firstName.value.slice(0, 1).toUpperCase() + firstName.value.slice(1) + lastName.value
// })

// 读写的计算属性
let fullName = computed({
    get(){
        console.log(3)
        return firstName.value.slice(0, 1).toUpperCase() + firstName.value.slice(1) + '-' + lastName.value
    },
    set(val){
        console.log(2)
        const [str1, str2] = val.split('-')
        firstName.value = str1
        lastName.value = str2
    }
})

function changeFullName() {
    console.log(1)
    fullName.value = 'li-si'
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

li {
    font-size: 20px;
}
</style>