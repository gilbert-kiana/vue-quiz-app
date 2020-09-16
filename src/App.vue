<template>
  <div class="container-app">
    <div class="container-quiz">
      <div class="quiz-header">
           <h1>QUIZ APP</h1>
      </div>
      <div class="quiz-main" v-for="(element,index) in questions" :key="index">
          <div class="the-questions">
           <h1>Questions</h1>
           <p>{{element.question}}</p>
          </div>
          <div class="answers">
            <ul>
              <li v-for="(item,index) in element.options" :key="index">
                {{item.option}}
              </li>
            </ul>
          </div>
      </div>
      <div class="quiz-footer">
        
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
        },
        {
          question:'',
          options:[
            {option:''},
            {option:''},
            {option:''},
            {option:''} 
          ]
        }
      ]
    }
  }
  
}
</script>

<style>

</style>
