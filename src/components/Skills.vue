<template>
  <div class="hello">
    <div class="holder">
    
    <form @submit.prevent="addSkill">
      <span class="visibleInput"> {{skill}} </span>
      <input type="text" placeholder="Enter a skill you have.." v-model="skill" v-validate="'min:5'" name="skill">
      
      <transition name="alert">
        <p class="alert" v-if="errors.has('skill')"> {{errors.first('skill')}} </p>
       </transition>

    </form>

      <ul>
       <transition-group name="list">
          <li v-for="(data, index) in skills" :key='index + 0'>  
            {{ data.skill}} 
            <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>

          </li>
       </transition-group>
      </ul>
      <p>These are the skills that you possess</p>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Skills",
    data() {
      return {
        skill: '',
        skills: [
          {"skill": "JavaScript"},
          {"skill": "Python"}
        ]
      };
    },
    methods: {
      addSkill() {
        this.$validator.validateAll().then((result) => {
          if(result) {
            this.skills.push({skill: this.skill})
            this.skill = '';
          }
        })
      },
      remove(id){
        this.skills.splice(id,1)
      }
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>