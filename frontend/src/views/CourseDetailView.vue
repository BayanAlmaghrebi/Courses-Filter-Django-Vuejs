<template>
    <div class="container my-5">
        <div class="row">
            <div class="col-lg-6">
                <img :src="course.image" class="img-fluid" alt="">
            </div>
            <div class="col-lg-6">
                <h3 class="card-title">{{ course.name }}</h3>
                <p > {{ course.category }}</p>
                <p > {{ course.price }}$</p>
                <form class="row">
                    <div class="col-lg-6"> 
                        <input type="number" value="1" class="form-control">
                    </div>
                    <div class="col-lg-6">
                        <button class="btn btn-info"> Add To Cart </button>
                    </div>
                </form>
            </div>
        </div>


    </div>
</template>

<script>

    import axios from 'axios'

    export default{
        name: 'CourseDetail',
        data(){
            return {
                course: null
            }
        },
        created(){
            this.getCourse()
        },
        methods:{
            getCourse(){
                const courseID =  this.$route.params.courseId
                axios.get(`http://127.0.0.1:8000/api/courses/${courseID}`)
                .then(response => {
                    this.course = response.data
                })
            }
        }
    }
</script>
