<template>
    <button type="button"  @click="handleClick" class="btn btn-primary">{{text}}</button>
</template>
<script>
import 'bootstrap/dist/css/bootstrap.min.css'
export default{
    name:'ButtonComp',
    data(){
        return{
            text:'Add A Task',
            buttonClicked:true
        }
    },
    methods:{
        handleClick()
        {
            this.buttonClicked = !this.buttonClicked;
            this.$emit("button-clicked");
            if(!this.buttonClicked)
            this.text='Close';
            else
            this.text='Add A Task';
        }
    }
}
</script>