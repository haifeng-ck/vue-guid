<template>
    <div id="app">
        <img alt="Vue logo" src="./assets/logo.png" style="width: 100px;height: 100px;">
        <h4>单文件组件</h4>
        <hr>
        <todo-list>
            <todo-item
                    v-for="item in list"
                    :key="item.id"
                    :title="item.title"
                    :del="item.del"
                    @delete="handleDelete(item.id)"
                    @reset="handleReset(item.id)"
            >
                <template #pre-icon>
                    <span>🚅</span>
                </template>
                <template #sub-icon>
                    <span>🚀</span>
                </template>
                <template #last-icon="{ value: val }">
                    <span>🛸</span>
                    <span>{{ val }}</span>
                </template>
            </todo-item>
        </todo-list>
        <h4>数据双向绑定 v-model</h4>
        <hr>
        <p>双向绑定：{{ message }}</p>
        <!-- v-model 是一个语法糖 -->
        <input type="text" v-model="message" style="width: 500px; margin-bottom: 15px">
        <!-- 去除 v-model 的语法糖 -->
        <input type="text" :value="message" @input="handelChange" style="width: 500px;">
    </div>
</template>

<script>
    import TodoList from "./components/TodoList";
    import TodoItem from "./components/TodoItem";

    export default {
        name: 'app',

        components: {
            TodoList,
            TodoItem
        },

        data() {
            return {
                list: [
                    {
                        id: '00',
                        title: 'love vue',
                        del: false
                    },
                    {
                        id: '01',
                        title: 'love javaScript',
                        del: false
                    },
                    {
                        id: '02',
                        title: 'do you love vue ?',
                        del: false
                    },
                    {
                        id: '03',
                        title: 'give up',
                        del: false
                    }
                ],
                message: 'v-model 只是一个语法糖'
            }
        },

        methods: {
            handleDelete(id) {
                this.list.map(item => {
                    if (item.id === id) item.del = true
                })
            },

            handleReset(id) {
                this.list.map(item => {
                    if (item.id === id) item.del = false
                })
            },

            handelChange(e) {
                this.message = e.target.value
            }
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
