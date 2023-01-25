<template>
    <div class="list">
        <div v-for="project in projectsData" :key="project.id">
            <ProjectCard :title="project.title" :image="project.image" :description="project.description" :video="project.video" />
        </div>
    </div>
</template>
<script>
import ProjectCard from './ProjectCard.vue'
export default{
    name : 'ProjectsList',
    components:{
        ProjectCard
    },
    props:{
        
    },
    data(){
        return{
            projectsData : [
                {id:0, title:"project1", image:require('@/assets/logo.png'), description:"description1blablabla blabla blabla bla", video:require('@/assets/projectsVideos/project1.mp4')},
                {id:1, title:"project2", image:require('@/assets/logo.png'), description:"description1blablabla blabla blabla bla", video:require('@/assets/projectsVideos/project1.mp4')},
                {id:2, title:"project3", image:require('@/assets/logo.png'), description:"description1blablabla blabla blabla bla"},
                {id:3, title:"project4", image:require('@/assets/logo.png'), description:"description1blablabla blabla blabla bla"},
                {id:4, title:"project1", image:require('@/assets/logo.png'), description:"description1blablabla blabla blabla bla"},
                {id:5, title:"project2", image:require('@/assets/logo.png'), description:"description1blablabla blabla blabla bla"},
                {id:6, title:"project3", image:require('@/assets/logo.png'), description:"description1blablabla blabla blabla bla"},
                {id:7, title:"project4", image:require('@/assets/logo.png'), description:"description1blablabla blabla blabla bla"},
                {id:8, title:"project1", image:require('@/assets/logo.png'), description:"description1blablabla blabla blabla bla"},
                {id:9, title:"project2", image:require('@/assets/logo.png'), description:"description1blablabla blabla blabla bla"},
                {id:10, title:"project3", image:require('@/assets/logo.png'), description:"description1blablabla blabla blabla bla"},
                {id:11, title:"project4", image:require('@/assets/logo.png'), description:"description1blablabla blabla blabla bla"},
            ],
        }
    }
}
</script>
<style scoped>
.list{
    width:86%;
    height:fit-content;
    margin:0 7% 3vh 10%;

    display:flex;
    flex-wrap: wrap;
    justify-content: space-around;
    row-gap: 3vh;

    overflow-y: scroll;
    padding-right: 300px;
    box-sizing: content-box;
}

.list>div{
    width:fit-content;
}
</style>