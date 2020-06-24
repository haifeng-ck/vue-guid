<template>
    <li>
        <slot name="pre-icon">😀</slot>
        <span v-if="!del">{{ title }}</span>
        <span v-else style="text-decoration: line-through">{{ title }}</span>
        <slot name="sub-icon">🆒</slot>
        <button v-if="!del" @click="$emit('delete')">删除</button>
        <slot name="last-icon" :value="value">🐕</slot>
        <button v-if="del" @click="$emit('reset')">恢复</button>
    </li>
</template>

<script>
    export default {
        name: "TodoItem",

        props: {
            title: String,
            del: {
                type: Boolean,
                default: false
            }
        },

        data() {
            return {
                value: Math.random()
            }
        }
    }
</script>

<style scoped>

</style>
