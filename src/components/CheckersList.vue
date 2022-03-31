<template>
    <div id="hus">
    <div id = "controls-checkout">
        <p>Please enter your details</p>
        <label for="fname">Name</label><br>
        <input v-model="firstName"><br>
        <label for="avail">Phone Number</label><br>
        <input v-model="phoneNo"><br>
        <button @click='placeOrder()'>Place Order</button>
    </div>

  <div id="lessonlst">
        <div v-bind:key="lesson.key" v-for="lesson in getLessons()"> 
            <img v-bind:src="lesson.image"> 
            <h1>{{lesson.topic}}</h1>
            <p>location: {{lesson.location}}</p>
            <p>Price: {{lesson.price}}</p>
            <button @click='removeLesson(lessons._id)'>Remove Lesson</button>
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
