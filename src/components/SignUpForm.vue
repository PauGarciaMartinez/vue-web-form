<template>
  <form>
    <label>Email</label>
    <input type="email" required v-model="email">

    <label>Password</label>
    <input type="password" required v-model="password">

    <label>Role</label>
    <select v-model="role" required>
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

    <div class="languages">
      <input type="checkbox" value="html" v-model="languages">
      <label>HTML5</label>
    
      <input type="checkbox" value="css" v-model="languages">
      <label>CSS3</label>
    
      <input type="checkbox" value="javascript" v-model="languages">
      <label>JavaScript</label>

      <input type="checkbox" value="vue" v-model="languages">
      <label>Vue3</label>
    </div>

    <label>Skills</label>
    <input type="text" v-model="tempSkill" @keydown.enter.prevent="addSkill">
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="removeSkill(skill)">{{ skill }}</span>
    </div>

    <div class="terms">
      <input type="checkbox" v-model="terms" required>
      <label>Accept terms and conditions</label>
    </div>

  </form>
</template>

<script>
export default {
  name: 'SignUpForm',
  data() {
    return {
      email: '',
      password: '',
      role: '',
      terms: false,
      languages: [],
      tempSkill: '',
      skills: []
    }
  },
  methods: {
    addSkill() {
      if (this.tempSkill && !this.skills.includes(this.tempSkill)) {
        this.skills.push(this.tempSkill.trim());
      }
      this.tempSkill = '';
    },
    removeSkill(skill) {
      this.skills = this.skills.filter(item => item !== skill);
    }
  }
}
</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input, select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
  background-color: white;
}
input[type='checkbox'] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}
.languages {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  gap: 5px;
}
.languages input {
  margin: 5px -3px 0px 15px;
}
.languages input:first-child {
  margin-left: 0px;
}
.pill {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background: #eee;
  border-radius: 20px;
  font-size: 12px;
  letter-spacing: 1px;
  font-weight: bold;
  color: #777;
  cursor: pointer;
}
</style>