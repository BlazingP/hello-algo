<template>
    <div class="hasChanged">
        <h1>这是一个检测数值是否有变化的页面</h1>
        <h1>{{ msg }}</h1>
        <input v-model="msg">
        <br>
        <input v-model="x"> <!-- 输入 X 的值 -->
        <br>
        <input v-model="y"> <!-- 输入 Y 的值 -->
        <p>值是否改变：{{ hasChanged ? '是' : '否' }}</p> <!-- 显示是否改变 -->
        <br>
        <input v-model="x"> <!-- 输入 X 的值 -->
        <br>
        <input v-model="y"> <!-- 输入 Y 的值 -->
        <p>值是否改变：{{ hasChanged1 ? '是' : '否' }}</p> <!-- 显示是否改变 -->
        <br>
        <input v-model="x"> <!-- 输入 X 的值 -->
        <br>
        <input v-model="y"> <!-- 输入 Y 的值 -->
        <p>值是否改变：{{ hasChanged2 ? '是' : '否' }}</p> <!-- 显示是否改变 -->
    </div>
</template>

<script setup>

import { ref, computed } from 'vue'

const msg = ref('Hello World!')

const x = ref()
const y = ref() // 使用 ref 以便 y 成为响应式数据

const hasChanged = computed(() => {
    if (x.value === y.value) {
        return x.value === 0 && 1 / x.value !== 1 / y.value
    } else {
        return x.value === x.value || y.value === y.value
    }
})

const hasChanged1 = computed(() => {
    return x.value !== y.value;
})


const hasChanged2 = computed(() => {
    if (x.value === y.value) {
        return false
    } else {
        return true
    }
})
// 注意：hasChanged 现在是一个计算属性，它会自动更新
</script>