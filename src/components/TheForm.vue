<template>
  <form @submit.prevent='submitForm'>
    <div class="form-control" :class="{ invalid: userNameValid === 'invalid' }">
      <label for="user-name">Your Name</label>
      <input id="user-name" name="user-name" type="text" v-model.trim='userName' @blur='validateInput' />
      <p v-if="userNameValid === 'invalid'" :class="{ errorValidationMsg: userNameValid === 'invalid' }">Please enter a
        valid name!</p>
    </div>
    <div class="form-control">
      <label for="age">Your Age (Years)</label>
      <input id="age" name="age" type="number" v-model='userAge' />
    </div>
    <div class="form-control">
      <label for="referrer">How did you hear about us?</label>
      <select id="referrer" name="referrer" v-model='referrer'>
        <option value="google">Google</option>
        <option value="wom">Word of mouth</option>
        <option value="newspaper">Newspaper</option>
      </select>
    </div>
    <div class="form-control">
      <h2>What are you interested in?</h2>
      <div>
        <input id="interest-news" name="interest" type="checkbox" value='news' v-model='interest' />
        <label for="interest-news">News</label>
      </div>
      <div>
        <input id="interest-tutorials" name="interest" type="checkbox" value='tutorials' v-model='interest' />
        <label for="interest-tutorials">Tutorials</label>
      </div>
      <div>
        <input id="interest-nothing" name="interest" type="checkbox" value='nothing' v-model='interest' />
        <label for="interest-nothing">Nothing</label>
      </div>
    </div>
    <div class="form-control">
      <h2>How do you learn?</h2>
      <div>
        <input id="how-video" name="how" type="radio" value='video' v-model='how' />
        <label for="how-video">Video Courses</label>
      </div>
      <div>
        <input id="how-blogs" name="how" type="radio" value='blogs' v-model='how' />
        <label for="how-blogs">Blogs</label>
      </div>
      <div>
        <input id="how-other" name="how" type="radio" value='other' v-model='how' />
        <label for="how-other">Other</label>
      </div>
    </div>
    <div class="form-control">
      <RatingControl v-model='rating' />
    </div>
    <div class='form-control'>
      <input type="checkbox" name="confirm-terms" id="confirm-terms" v-model='confirmTerms'>
      <label for="confirm-terms">Do you agree to the terms of use?</label>
    </div>
    <div>
      <button>Save Data</button>
    </div>
  </form>
</template>

<script>
import RatingControl from './RatingControl.vue';

export default {
  components: {
    RatingControl
  },
  data() {
    return {
      userName: '',
      userAge: null,
      referrer: 'wom',
      interest: [],
      how: null,
      confirmTerms: false,
      userNameValid: 'pending',
      rating: null
    }
  },
  methods: {
    submitForm() {
      console.log('Username: ' + this.userName);
      this.userName = '';
      console.log('User Age:');
      console.log(this.userAge);
      console.log(35);
      this.userAge = null;
      console.log('Referrer: ' + this.referrer);
      this.referrer = 'wom';
      console.log('Checkboxes');
      console.log(this.interest);
      console.log('Radio Buttons');
      console.log(this.how);
      this.interest = [];
      this.how = null;
      console.log('Confirm?');
      console.log(this.confirmTerms);
      this.confirmTerms = false;
      console.log('Rating');
      console.log(this.rating);
      this.rating = null;
    },
    validateInput() {
      if (this.userName === '') {
        this.userNameValid = 'invalid'
      } else {
        this.userNameValid = 'valid'
      }
    }
  }
}
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
  margin: 1rem 0;
}

.form-control.invalid input {
  border-color: red;
}

.form-control.invalid label {
  color: red;
}

.form-control.invalid p {
  font-size: .8rem;
  color: red;
  margin-top: .5rem;
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
  width: 100%;
  font: inherit;
  border: 1px solid black;
  margin-top: 0.5rem;
  border-radius: 5px;
  padding: .5rem 1rem;
}

select {
  width: 200px;
  background: url("data:image/svg+xml,<svg height='10px' width='10px' viewBox='0 0 16 16' fill='%23000000' xmlns='http://www.w3.org/2000/svg'><path d='M7.247 11.14 2.451 5.658C1.885 5.013 2.345 4 3.204 4h9.592a1 1 0 0 1 .753 1.659l-4.796 5.48a1 1 0 0 1-1.506 0z'/></svg>") no-repeat;
  background-position: calc(100% - 0.75rem) center !important;
  -moz-appearance: none !important;
  -webkit-appearance: none !important;
  appearance: none !important;
  padding-right: 2rem !important;
  cursor: pointer;
}

input[type='checkbox'],
input[type='radio'] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

input[type='checkbox']+label,
input[type='radio']+label {
  font-weight: normal;
}

button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 10px;
  margin-top: 0.5rem;
}

button:hover,
button:active {
  border-color: #1262cb;
  background-color: #1262cb;
}
</style>