<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="ip1" placeholder="ххх.ххх.ххх.ххх"> -
        <input type="text" v-model="ip2" placeholder="ууу.ууу.ууу.ууу">
        <button type="submit">добавить ip</button>
    </form>
</template>
<script>
    export default {
        data(){
            return {
                ip1: '',
                ip2: ''
            }
        },
        methods:{
            onSubmit(){
                if(this.ip1.trim()&&this.ip2.trim()){
                    const newTodo = {
                        id: Date.now(),
                        ip1: this.ip1,
                        ip2: this.ip2,

                    }

                    this.$emit('add-todo', newTodo)
                    this.ip1 = '',
                    this.ip2 = ''
                }
            }
        }
    }
</script>
<style scoped>
    form{
        display: flex;
    }

    input{
        width: 150px;
    }
</style>