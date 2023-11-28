<!-- 编辑器开发 -->
<template>
    <div class="editor">
        <!-- input后，内容执行update -->
        <textarea class="input" :value="input" @input="update">
                    <div class="output" v-html="output"></div>
                    </textarea>
    </div>
</template>

<script setup>
import { marked } from 'marked'
import { debounce } from 'lodash-es'
import { ref, computed } from 'vue'

// ref响应式的内容
const input = ref('#hello')

const output = computed(() => marked(input.value))

const update = debounce((e) => {
    input.value = e.target.value
})
</script>

<!-- 样式 -->
<style></style>