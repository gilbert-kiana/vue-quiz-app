<template>
<div class="app">
  <div class="container-app">
    <div class="container-quiz">
      <div class="quiz-header">
           <h1>QUIZ APP</h1>
      </div>
      <div class="quiz-main" v-for="(element,index) in questions.slice(a,b)" :key="index" v-show="quiz">
          <div class="the-questions">
           <h1>Question :{{b}}/{{questions.length}}</h1>
           <p>{{element.question}}</p>
          </div>
          <div class="answers">
            <ul>
              <li v-for="(item,index) in element.options" :key="index" :class="select ? check(item):''" @click="selectAnswer(item)">
                {{item.option}}
              </li>
            </ul>
          </div>
      </div>
      <div class="score" v-if="score_show">
        <h2>Your score is</h2>
        <h2>{{score}}/{{questions.length}}</h2>
        <div class="restart">
          <button @click="restartQuiz">Restart</button>
        </div>
      </div>
      <div class="quiz-footer">
        <div class="button">
          <button @click="skipQuestion">Skip</button>
          <button @click="nextQuestion">Next</button>
          
        </div>
      </div>
    </div>
  </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      questions:[
        {
          question:'Whose the writer of this program.',
          options:[
            {option:'kaiser',correct:true},
            {option:'kiana'},
            {option:'gilbert'},
            {option:'intabo'} 
          ]
        },
        {
          question:'Which is my favorite school',
          options:[
            {option:'maseno',correct:true},
            {option:'alliance'},
            {option:'lenana'},
            {option:'orero'} 
          ]
        }
        
      ],
      a:0,
      b:1,
      select:false,
      score:0,
      quiz:true,
      score_show:false,
      next:false
    }
  },
  methods:{

   selectAnswer(e){
     this.select=true;
     this.next=true;

     if (e.correct){
       this.score++;
     }
   },

    check(status){
      if(status.correct){
        return 'correct'
      }
      else{
        return 'incorrect'
      }
    },

    nextQuestion(){

      if (this.questions.length -1 ==this.a){
        this.score_show=true;
        this.quiz =false;
      }
      else{
    this.a++;
    this.b++;
    this.select =false;
      }
    },

    skipQuestion(){
      if (this.questions.length -1 ==this.a){
        this.score_show=true;
        this.quiz =false;
      }
      else{
    this.a++;
    this.b++;
    
      }
    },
    restartQuiz(){
      Object.assign(this.$data, this.$options.data());
    }
    
  }
  
}
</script>

<style>
.app{
  font-family:sans-serif;
  margin: 0;
  letter-spacing: 2px;
}

.container-app{
  display:flex;
  width:100%;
  height:100%;
  justify-content: center;
}

.container-quiz{
  display: flex;
  width: 40%;
  height: 85%;
  position: absolute;
  top: 0pc;
  bottom: 0pc;
  margin: auto;
  flex-flow: column;
  text-align: center;
  border: 1px solid #e7e7e7;
  border-radius: 10px;
  background-color: white;
 box-shadow: 0 10px 20px rgba(0,0,0, 0.19), 0 6px rgba(0,0, 0, 1.23);

}

.quiz-header{
 display:flex;
 width:100%;
 height:20%;
 border-bottom: 1px solid #e7e7e7;
 justify-content: center;
 align-items: center;
 background-color:royalblue;
 border-radius: 10px 10px 0px 0px;

}

.quiz-main{
  display: flex;
  width:100%;
  height: 70%;
  flex-flow: column;
  margin: auto;
}

.quiz-footer{
  display: flex;
  width:100%;
  height: 10%;
  border-top: 1px solid #e7e7e7;
  justify-content: center;
  background-color: #e7e7e7;
  border-radius: 0px 0px 10px 10px;

}

.the-questions{
 margin-top: 20px;

}

.the-questions p{
  margin-top:20px;
}

.answers{
 display: flex;
 width:100%;
justify-content: center;
margin:auto;
}

ul{
 display: flex;
 width: 80%;
 margin: 0%;
 padding: 0%;
 flex-flow: column;
}

ul li{
  list-style: none;
  line-height: 2;
  border:1px solid #cdd2d2;
  margin-top: 20px;
  border-radius:15px;
  cursor:pointer;
}

li:hover{
  background-color: silver ;
}

li.correct{
border:1px solid rgb(74, 219 ,74);
background-color:  rgb(74, 219 ,74);
color:white;
font-weight: 600;
}

li.incorrect{
  border: 1px solid rgb(240, 117, 100);
  background-color: rgb(240, 117, 100);
  color:whitesmoke;
  font-weight: 600;

}


.button{
display: flex;
width: 100%;
}

.button button{
  width: 150px;
  height: 35px;
  outline: none;
  border: 0;
  color:black; 
  font-size: 10px;
  cursor: pointer;
  border-radius: 15px;
  margin: auto;
  background-color: darkgray;

}

button:hover{
  background-color:dimgray ;
}

.score{
  display:flex;
  width:100%;
  height: 70%;
  flex-flow:column;
}

.score h2{
  margin-top:40px;

}

.restart button{
 width: 150px;
  height: 35px;
  outline: none;
  border: 0;
  color:white; 
  font-size: 10px;
  cursor: pointer;
  border-radius: 15px;
  margin: auto;
  background-color: rgb(100,128, 202);


}


</style>
