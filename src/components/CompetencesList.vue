<template>
    <div class="skills" v-on:mouseenter="TimerSkills()"> 
        <div class="skill">
            <span class="skillIntro">En développement web, j'aime travailler avec et aimerais devenir une experte de ...</span>
            <!-- <h2 :style="{animationDelay: 2  * index + 's', animationDuration: 1.5 * (skills['dev'].length - index) + 's'}" class="rotatingText-adjective" v-for="(skilldev, index) in skills['dev']" :key="index">{{ skilldev }}</h2> -->
            <h2 class="skillName">{{ skills['dev'][counter] }}</h2>
        </div>
        <div class="skill">
            <span class="skillIntro">Je sais aussi utiliser ces languages...</span>
            <ul class="skillList">
                <li v-for="(skill, index) in skills['prog']" :key="index">{{ skill }}</li>
            </ul>
        </div>
        <div class="skill">
            <span class="skillIntro">Et je développe mes projets en utilisant :</span>
            <ul class="skillList">
                <li v-for="(skill, index) in skills['proj']" :key="index">{{ skill }}</li>
            </ul>
        </div>
        <!-- <div class="skillsContainer">
            <div id="skillsTable">
                <div class="skillContainer" id="skill1" v-on:mouseenter="SkillsAppearing('dev')" v-on:mouseleave="SkillsDisappearing()">
                    <h3 v-show="skillsVisible[0]">Développement web</h3>
                    <ul class="skills">
                            <li :style="{opacity :randomPositions[0][index][2],  top: randomPositions[0][index][0] + '%', left: randomPositions[0][index][1] + '%',transition: 'top 1s ease, left 1.5s ease, opacity 3s ease' }" class="skill" v-for="(skill, index) in skills['dev']" :key="index">{{skill}}</li>
                    </ul>
                </div>

                <div class="skillContainer" id="skill2" v-on:mouseenter="SkillsAppearing('proj')" v-on:mouseleave="SkillsDisappearing()">
                    <h3 v-show="skillsVisible[1]">Gestion de Projet</h3>
                    <ul v-show="showSkills && indexSkill == 1" class="skills">
                        <li :style="{top: randomPositions[1][index][0] + '%', left: randomPositions[1][index][1] + '%'}" class="skill" v-for="(skill, index) in skills['proj']" :key="index">{{skill}}</li>
                    </ul>
                </div>

                <div class="skillContainer" id="skill3" v-on:mouseenter="SkillsAppearing('prog')" v-on:mouseleave="SkillsDisappearing()">
                    <h3 v-show="skillsVisible[2]">Programmation</h3>
                    <ul v-show="showSkills && indexSkill == 2" class="skills">
                        <li :style="{top: randomPositions[2][index][0] + '%', left: randomPositions[2][index][1] + '%'}" class="skill" v-for="(skill, index) in skills['prog']" :key="index">{{skill}}</li>
                    </ul>
                </div>
            </div>
        </div> -->
        <img class="background" src="@/assets/bg.png" alt="background">
    </div>
  </template>
  
  <script>
  export default {
    name: 'CompetencesList',
    data(){
        return{
            skills:{'dev' : ["VueJS","NuxtJS", "Javascript", "SQL", "ThreeJS", "NodeJS"], 'proj' : ["git (Github)", "AGILE"], 'prog' : ["Python", "C++", "OpenGL"]}, //, "Javascript", "SQL", "ThreeJS", "NodeJS"], ["git (Github)", "AGILE"],["Python", "C++", "OpenGL"]],
            indexSkill : null,
            showSkills : false,
            randomPositions:[[[0,0,0,0], [0,0,0,0], [0,0,0,0],[0,0,0,0], [0,0,0], [0,0,0]], [[0,0,0],[0,0,0]], [[0,0,0], [0,0,0], [0,0,0]]],
            skillsVisible : [true, true, true],
            counter :  0,
            counterProg : 0, 
            counterProj : 0,
            
        }
    },
    created: function(){
        this.counter = this.skills['dev'].length;
        this.counterProg = this.skills['prog'].length;
        this.counterProj = this.skills['proj'].length
    },
    methods:{
        MakeOtherSkillsInvisible: function(index){
            this.skillsVisible = [false, false, false]
            this.skillsVisible[index] = true
        }, 
        SkillsAppearing : function(categorie){
            
            console.log(this.skills[categorie][0])
            let convertTab=["dev", 'proj', 'prog'];
            this.indexSkill = convertTab.findIndex(element => element == categorie);
            this.MakeOtherSkillsInvisible(this.indexSkill)
            this.showSkills = true;
            this.randomPositions = [[[-250, 10, 1], [0,-100, 1], [150,100, 1],[-200,-35, 1], [-180,80, 1], [220,-70, 1]], [[150,100, 1],[-200,-35, 1]], [[-250, 10, 1], [0,-100, 1], [150,100, 1]]];

        },
        SkillsDisappearing : function(){
            // this.index = null;
            // this.showSkills = false;
            // this.skillsVisible = [true, true, true]
            //this.randomPositions = [[[0,0,0], [0,0,0], [0,0,0],[0,0,0], [0,0,0], [0,0,0]], [[0,0,0],[0,0,0]], [[0,0,0], [0,0,0], [0,0,0]]];

        },
        timerDev : function(){
            if (this.counter >= 0) {
                    setTimeout(() => {
                        this.counter -= 1
                        // console.log(this.counter)
                        this.timerDev();
                        
                    }, 1000)
                    
                }else{
                    this.counter = this.skills["dev"].length;
                    this.timerDev()
                }
        },
        TimerSkills: function(){
                this.timerDev();
        },
    }
  }
  </script>
  
  <style scoped>
  .background{
    position: absolute;
    top: -80vh;
    left: -10vw;
    height: 120%;
    transform: rotate(35deg);
}
.skills{
    display:flex;
    flex-wrap: wrap;
    justify-content: center;
}
.skill{
    position:relative;
    display:flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin: 0 2vw;
}

.skill:first-child{
    flex-basis: 100%;
}

.skillIntro{
    font-family: 'Questrial';
    font-size: 1.5rem;
    text-transform: uppercase;
    text-align: center;
    margin-top: 5vh;
}

.skillName{
    min-height: 100px;
    font-size: 4rem;
}

.skillList{
    font-size: 1.2rem;
    list-style: none;
    display: flex;
}

.skillList li{
    margin: 0 2vw;
}

.rotatingText-adjective { 
  left: 0;
  margin-bottom: 0;
  margin-top: 30px;
  opacity: 0;
  position: absolute;
  right: 0;
  text-align: center;
  text-transform: uppercase;
  top: 40vh;
  animation : rotate-text-up 1.5s linear forwards;
  /* animation-iteration-count: infinite; */
}

@keyframes rotate-text-up { 
  0% {
    transform: translate3d(0, 80px, 0);
    opacity: 0;
  }
  
  20%, 80% {
    transform: translate3d(0, 0, 0);
    opacity: 1;
  }
  
  80% {
    transform: translate3d(0, -40px, 0);
    opacity: 0;
  }
  100%{
    transform: translate3d(0, 80px, 0);
    opacity: 0;
  }
}

/*
p, li{
    font-size: 1rem;
    width: 65vw;
    margin-left: 5vw;
    
}
h2{
    margin: 1vh 10vw;
    font-size: 5rem;
}

h3{
    margin:1vh 1vw;
    font-size: 2rem;
    background-color: black;
}

ul{
    margin:1vh 1vw;
    list-style: none;
}

.aProposDeMoi{
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    height: 100vh;
    justify-content: flex-start;
    width: 100vw;
    margin-top:5vh;

}
.skillsContainer{
    height: 100%;
    width:100%;
}

.skillsContainer li{
    text-transform: uppercase;
}

#skillsTable{
    display:grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(3, 1fr);
    grid-template-areas: 
    "skill2 . ."
    ". skill1 ."
    ". . skill3";
    justify-items: center;
    align-items: center;
    height:100%;
    width: 100%;
}

#skill1{
    grid-area: skill1;
}

#skill2{
    grid-area: skill2;
}

#skill3{
    grid-area: skill3;
}

.skillContainer{
    position:relative;
}
.aProposDeMoi div{
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    margin: 1vh 2vw;
    text-align: justify;
}

.skills{
    position: absolute;
    height: 100%;
    width: 100%;
}
.skill{
    position:absolute;
    top:0;
    left:0;
    z-index: 10;
    opacity:0;
    transition: top 2s ease, left 2.5s ease, opacity 2s ease 3s;
}


.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
*/
  </style>