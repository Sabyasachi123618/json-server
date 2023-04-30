<template>
    <form @submit="handleSubmit">
        <div class="form-group">
          <label for="text" >Text:</label>
          <input type="text" v-model="text" class="form-control" id="text">
          Reminder<input type="checkbox" v-model="reminder">
        </div>
    </form>
</template>
<script>
export default {
    name:'AddTask',
    data(){
        return{
            text:'',
            reminder:false
        }
    },
    methods:{
        handleSubmit(e)
        {
            console.log(this.reminder);
            e.preventDefault();
            if(!this.text){
            alert('Please add something');
            return;
            }
            const newTask={
                text:this.text
            };
            this.$emit("Add-Task",newTask);
            this.text='';
        }
    },
    emits:['Add-Task']
}
</script>