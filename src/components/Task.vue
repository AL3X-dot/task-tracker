<template>
    <div class="row scale-transition">
        <div :class="classes" @dblclick="completeTask">
            <span class="left" >{{task.content}}</span>
            <i id='delIcon' class="material-icons right" @click="deleteme(task.id)">delete</i>
        </div>
    </div>  
</template>
<script>
export default {
    name:'Task',
    props:{
        task:Object, 
    },
    methods:{
        deleteme(id){
            this.$emit('deleteme',id)
        },
        completeTask(){
            this.classes = 'col s8 offset-s2 flow-text green lighten-3'
        }
    },
    data(){
        return{
            classes:'col s8 offset-s2 flow-text red lighten-3'
        }
    }
}
</script>
<style scoped>
    #delIcon{
        margin-top:6px;
        cursor: pointer;
    }
</style>