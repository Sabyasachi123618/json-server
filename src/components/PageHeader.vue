<template>
    <h1>{{title}}</h1>
    <ButtonComp @button-clicked="handleClick"/>
</template>
<script>
import ButtonComp from './ButtonComp.vue';
export default{
    name:'PageHeader',
    components:{
    ButtonComp,
},
    props:{
        title:String
    },
    methods:{
        handleClick()
        {
            this.$emit("button-clicked")
        }
    }
}
</script>