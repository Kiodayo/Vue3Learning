<!-- 编辑器开发 -->
<template>
    <h1 class="title">MarkDownEditor</h1>
    <div class="editor">

        <!-- input后，内容执行update -->

        <textarea class="input" :value="input" @input="update">
                                                                    </textarea>
        <div class="output" v-html="output"></div>
    </div>
</template>

<script setup>
import { marked } from 'marked'
import { debounce } from 'lodash-es'
import { ref, computed } from 'vue'

// ref响应式的内容
const input = ref('# hello')

const output = computed(() => marked(input.value))

const update = debounce((e) => {
    input.value = e.target.value
})
</script>

<!-- 样式 -->
<style>
body {
    margin: 0
}

.editor {
    display: flex;
    height: 100vh;
}

.title {
    display: flex;
    line-height: 30px;
    height: 35px;
    text-align: left;
    width: 100%;
    padding-left: 10px;

}

.input,
.output {
    overflow: auto;
    width: 50%;
    height: 100%;
    border-top: 10px solid #ccc;
    box-sizing: border-box;
    padding: 0 20px;
}

.input {
    border: none;
    border-top: 10px solid #ccc;
    border-right: 4px solid #ccc;
    resize: none;
    outline: none;
    background-color: #f6f6f6;
    font-size: 14px;
    padding: 20px;
}

code {
    color: #f66;
}
</style>