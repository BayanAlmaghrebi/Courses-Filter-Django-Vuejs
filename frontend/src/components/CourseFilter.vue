<template>
    <h3> Courses Filter </h3>
    <form class="card ">

        <div class="flex align-items-center mycheckbox" v-for="cat in category" :key="cat.id">
            <Checkbox v-model="selectedCategory" :inputId="cat.id" :name="cat.name" :value="cat.id" />
            <label :for="cat.id" class="ml-2"> {{cat.name}} </label>
        </div>

    </form>
</template>

<script>
    export default{
        name: 'CourseFilter',
        data(){
            return {
                category : [
                    {id:1 , name:"Web Development"},
                    {id:2 , name:'Mobile Development'},
                    {id:3 , name:'AI Development'},
                    {id:4 , name:'Game Development'},
                    {id:5 , name:'Deep Learning'}
                ],
                selectedCategory: []
            }
        },
        watch:{
            selectedCategory(){
                this.$emit('category-updated',this.selectedCategory)
            }
        }             // watch يعني حدثين مرتبطين ببعض 
                    //   emit يعني ارسل اشارة لها اسم وبتاخد معها داتا
    }
</script>

<style>
    .mycheckbox{
        margin:10px 0px;
    }
</style>