<template>
    <div id="hus">


  <div id="lessonlst">
        <div v-bind:key="lesson.key" v-for="lesson in getLessons()"> 
            <img v-bind:src="lesson.image"> 
            <h1>{{lesson.topic}}</h1>
            <p>location: {{lesson.location}}</p>
            <p>Price: {{lesson.price}}</p>
            <button @click='removeLesson(lesson._id)'>Remove Lesson</button>
        </div>
      </div>
 </div> 
</template>

<script>
export default {
    name: 'LessonList',
    props: ['cart', 'lessons'],
    data() {
        return{
        
        }
    },


    methods: {
          removeLesson(lessonid){
            this.$emit('removeItem',lessonid)
        },

            getLessons(){
            //compares IDs in the cart against lessons in array of lessons
            let lessonDetails = []
            for (let id of this.cart){
              for (let _lessons of this.lessons){
                if(id === _lessons._id){
                  lessonDetails.push(_lessons)
                }
              }
            }
            return lessonDetails;
        },
        
}
}

</script>
