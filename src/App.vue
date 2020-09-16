<template>
<div class="app">
  <div class="container-app">
    <div class="container-quiz">
      <div class="quiz-header">
           <h1>QUIZ APP</h1>
      </div>
      <div class="quiz-main" v-for="(element,index) in questions.slice(a,b)" :key="index">
          <div class="the-questions">
           <h1>Question :{{b}}/{{questions.length}}</h1>
           <p>{{element.question}}</p>
          </div>
          <div class="answers">
            <ul>
              <li v-for="(item,index) in element.options" :key="index" :class="select ? check(item):''" @click="selectAnswer">
                {{item.option}}
              </li>
            </ul>
          </div>
      </div>
      <div class="quiz-footer">
        <div class="box-button">
          <button>Skip</button>
          <button>Next</button>
          <button>Prev</button>
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
    }
  },
  methods:{

   selectAnswer(){
     this.select=true;
   },

    check(status){
      if(status.correct){
        return 'correct'
      }
      else{
        return 'incorrect'
      }
    }

  }
  
}
</script>

<style>
.app{
  font-family:sans-serif;
  margin: auto;
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


</style>
