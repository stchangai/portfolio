<template>
    <div class="section" :id="title.toLowerCase()">
        <h1>{{ title }}</h1>
        <ProjectsList v-if="title.toLowerCase() == 'projects'" />
        <a v-if="nextpage != undefined" :href="'#'+nextpage"><img class="downArrowIcon" src="@/assets/icons/down_arrow.svg" alt="down arrow to swipe to the next section"><img class="downArrowIcon" src="@/assets/icons/down_arrow.svg" alt="down arrow to swipe to the next section"></a>
    </div>
</template>
<script>
import ProjectsList from "./ProjectsList.vue"
export default{
    name : 'MainSection',
    components:{
        ProjectsList
    },
    props:{
        title :String,
        nextpage: String
    },
    mounted(){
        console.log(this.nextpage)
    },
}
</script>
<style scoped>
.section{
    height: 100vh;
    /* min-height: 100vh; */
    /* height:fit-content; */
    max-width:100%;
    width: 100vw;
    background-color : black;
    font-size: 5rem;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    color:white;
    
    margin: 0;
    padding: 0;
    border: 0;

    display: flex;
    flex-direction: column;
    align-items: flex-start;

    position:relative;
    overflow-x: hidden;
}

h1{
    color:transparent;
    -webkit-text-stroke: 1px white;
}

a{
    height: fit-content;
    width: fit-content;
}

.downArrowIcon{
    position :absolute;
    bottom: 5vh;
    left:50%;
    height: 40px;
    width: 40px;
    filter: invert(100%) sepia(1%) saturate(622%) hue-rotate(210deg) brightness(119%) contrast(100%);
}

.downArrowIcon + img {
    bottom: 4vh;
}
</style>