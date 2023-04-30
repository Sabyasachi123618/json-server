<template>
    <div  :key="task.id" v-for="task in tasks">
        <SingleTask @button-clicked = "handleClick" :task="task"/>
    </div>
    
</template>
<script>
import SingleTask from './SingleTask.vue';
export default{
    name:'TasksComp',
    props:{
        tasks:Array
    },
    components:{
    SingleTask
},
methods:{
    handleClick(id)
    {
        this.$emit('button-clicked',id)
    }
},
emits:['button-clicked']
}
</script>