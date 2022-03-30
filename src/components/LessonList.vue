<template>
    <div id="LessonList">
           <div  id="real">
                   <div id="real1">
            <div v-bind:key="im._id" v-for="im in images" class="lessonlist1">
                <img v-bind:src="im.Image" alt="" width="60px" height="60px">
               </div>
            </div>
            <div id="real2">
        <div v-bind:key="lessons._id" v-for="lessons in lessons" class="lessonlist">
            <div id="sub">
                <h3>Subject: {{ lessons.topic}} </h3>
                <em>Location: {{ lessons.location }}</em><br><br>
                <em>Price: {{ lessons.price }} </em>
                <em><h3>Spaces: {{ lessons.space }} </h3></em>
                <button id="adc" @click='addLesson(lessons)'
                >Add To Cart</button>
                </div><br><br><br>
            </div>
</div>
</div>
</div>
</template>

<script>
export default {
    name: 'LessonList',
    props: ['lessons', 'images'],
    data() {
        return{
        
        }
    },


    methods: {
        addLesson(lessons){
           this.$emit('addLesson', lessons);
        },

}

}
</script>