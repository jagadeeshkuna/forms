<template>
  <form @submit.prevent="submitForm">
    <div class="form-control" :class="{invalid: userNameValidity === 'invalid'}">
      <label for="user-name">Your Name</label>
      <input id="user-name" name="user-name" type="text" 
       v-model.trim="userName" @blur="validateInput"/>
       <p v-if="userNameValidity === 'inValid'"> Enter a valid username </P>
    </div>
    <div class="form-control">
      <label for="age"> Age </label>
      <input id="age" name="age" type="number"
      v-model="userAge" ref="ageInput"> 
    </div>
    <div class="form-control">
      <label for="referrer">How did you hear about us?</label>
      <select id="referrer" name="referrer" v-model="referrer">
        <option value="google">Google</option>
        <option value="social media">Social Media</option>
        <option value="newspaper">Newspaper</option>
      </select>
    </div>
    <div class="form-control">
      <h2> you interested in</h2>
      <div>
        <input id="interest-news" name="interest" type="checkbox" value="news"
        v-model="interest" />
        <label for="interest-news">News</label>
      </div>
      <div>
        <input id="interest-tutorials" name="interest" type="checkbox" value="turorials"
        v-model="interest"/>
        <label for="interest-tutorials">Tutorials</label>
      </div>
      <div>
        <input id="interest-nothing" name="interest" type="checkbox" value="nothing"
        v-model="interest"/>
        <label for="interest-nothing">Other</label>
      </div>
    </div>
    <div class="form-control">
      <h2> way you want to learn</h2>
      <div>
        <input id="how-video" name="how" type="radio" value="video"
        v-model="how"/>
        <label for="how-video">Video Courses</label>
      </div>
      <div>
        <input id="how-blogs" name="how" type="radio" value="how"
        v-model="how"/>
        <label for="how-blogs">Blogs</label>
      </div>
      <div>
        <input id="how-other" name="how" type="radio" value="other"
        v-model="how"/>
        <label for="how-other">Other</label>
      </div>
    </div>
    <div class="form-control">
      <rating-control v-model="rating"></rating-control>
    </div>
    <div class="form-control">
        <input type="checkbox"  id="confirm-terms"  name="confirm-terms" v-model="confirm"/>
        <label for="confirm-terms">Agree for terms and conditions</label>
    </div>
    <div>
      <button>Save</button>
    </div>
  </form>
</template>
<script>
import RatingControl from './RatingControl.vue';
export default {
  
  components: {
    RatingControl
},
    data () {
        return{
            userName: '',
            userAge: null,
            referrer:'social media',
            interest: [],
            how: null,
            confirm: false,
            rating: null,
            userNameValidity: 'pending',
        };
    },
    methods: {
        submitForm(){
            console.log('username:' + this.userName);
            this.userName = '';
            console.log('User age:');
            console.log(this.userAge);
            this.userAge = null;
            console.log('Referrer: ' + this.referrer);
            this.referrer = 'social media'
            console.log('Checkboxes');
            console.log(this.interest);
            console.log('Radio buttons');
            console.log(this.how);
            this.interest = [];
            this.how = null;
            console.log('Confirm');
            console.log(this.confirm);
            this.confirm = false;
            console.log('Rating');
            console.log(this.rating);
            this.rating = null;
        },
        validateInput (){
            if(this.userName === '') {
                this.userNameValidity = 'inValid';
            }else{
                this.userNameValidity = 'Valid';
            }
        }
    },
};
</script>
<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background-color: #ffffff;
}
.form-control {
  margin: 0.5rem 0;
}
label {
  font-weight: bold;
}
h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}
input,
select {
  display: block;
  width: 50%;
  font: inherit;
  margin-top: 0.5rem;
}
select {
  width: auto;
}
input[type='checkbox'],
input[type='radio'] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}
input[type='checkbox'] + label,
input[type='radio'] + label {
  font-weight: normal;
}
button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}
button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}
</style>