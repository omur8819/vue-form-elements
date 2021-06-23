<template>
  <div class="container">
    <h3>Working with Form Data</h3>
    <hr>
    <div class="row">
      <div class="col-md-6">
        <div class="panel panel-warning">
          <div class="panel-heading">
            <h4>Application Form</h4>
          </div>
          <div class="panel-body">
            <form>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label for="email">Username</label>
                    <input type="text"
                          id="username" 
                          class="form-control" 
                          :value="userData.username" 
                          @input="userData.username = $event.target.value">
                  </div>
                  <div class="form-group">
                    <label for="password">Password</label>
                    <input type="password" id="password" class="form-control" v-model.lazy.trim="userData.password">
                  </div>
                  <div class="form-group">
                    <label for="age">Age</label>
                    <input type="number" id="age" class="form-control" v-model.number.trim="userData.age">
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label for="message">Comments</label><br>
                  <textarea id="message" rows="3" class="form-control" v-model="userData.message"></textarea>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label>
                      <input type="checkbox" value="software" v-model="userData.interests"> Software
                    </label>
                    <label>
                      <input type="checkbox" value="hardware" v-model="userData.interests"> Hardware
                    </label>
                    <label>
                      <input type="checkbox" value="front-end" v-model="userData.interests"> Front-End
                    </label>
                    <label>
                      <input type="checkbox" value="back-end" v-model="userData.interests"> Back-End
                    </label>
                  </div>

                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label>
                    <input v-model="userData.gender" type="radio" value="male"> Male
                  </label>
                  <label>
                    <input v-model="userData.gender" type="radio" value="female"> Female
                  </label>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 from-group">
                  <label>City</label>
                  <select class="form-control" v-model="userData.selectedCity">
                    <option :selected="city == 'London'" v-for="city in userData.cities" v-bind:key="city"> {{ city }} </option>
                  </select>
                </div>
              </div>
              <hr>

              <div class="row">
                <div class="col-md-12 form-group">
                  <app-switch v-model="switched"></app-switch>
                </div>
              </div>

              <div class="row">
                <div class="col-md-12">
                  <button
                    @click.prevent="submit"
                    class="btn btn-primary">Send!
                  </button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
      <div class="col-md-6" v-if="isSubmitted">
          <div class="panel panel-info">
            <div class="panel-heading">
              <h4>Form Data</h4>
            </div>
            <div class="panel-body">
              <p>Username: {{ userData.username }}</p>
              <p>Password:  {{ userData.password }}</p>
              <p>Age: {{ userData.age }}</p>
              <p style="white-space: pre;">Comments: {{ userData.message }} </p>
              <p><strong>Interests</strong></p>
              <ul>
                <li v-for="item in userData.interests" v-bind:key="item"> {{ item }} </li>
              </ul>
              <p>Gender: {{userData.gender}}</p>
              <p>City: {{ userData.selectedCity }} </p>
              <p>Toggle:  {{ switched }}</p>
            </div>
          </div>
      </div>
    </div>

  </div>
</template>

<script>
  import Switch from './Switch.vue';
  export default {
    data(){
      return{
        userData: {
          username: '',
          password: '',
          age: 30,
          message: '',
          interests: [],
          gender: '',
          cities: ["Istanbul", "London", "Paris", "New York", "Athens"],
          selectedCity: '',
        },
        switched: true,
        isSubmitted: false,
      }
    },
    components: {
      appSwitch: Switch,
    },
    methods: {
      submit(){
        this.isSubmitted = true;
      }
    },
  }
</script>

<style>

</style>
