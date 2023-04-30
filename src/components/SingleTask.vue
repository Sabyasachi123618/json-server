<template> 
    <h3 v-bind:class="[task.reminder ? 'reminder' : 'nothing']" >{{task.text}} <i class="fa-thin fa-check fa-beat fas"></i></h3>
</template>
<script>
export default{
    name:'SingleTask',
    props:{
        task:Object
    },
    methods:{
        onclick(id,reminder){
            console.log(reminder);
            this.$emit('button-clicked',id)
        }
    },
    emits:['button-clicked']
}
</script>
<style scoped>
.reminder{
    border-left: 5px solid green;
}
.nothing{
    border-left: 5px solid red;
}
.fas{
    color:green;
}
</style>