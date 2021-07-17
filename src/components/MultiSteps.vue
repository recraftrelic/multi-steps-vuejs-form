<template>
    <div class="w-1/2 m-auto">
        <component
          v-bind:is="steps[currentStep].component"
          v-bind:formValue="formValue[steps[currentStep].label]"
        />
        <div class="text-center">
          <button v-if="currentStep !== 0" v-on:click="previous" class="text-center p-5 text-5xl mt-4">
            <i className="ion-arrow-left-c" />
          </button>
          <button v-if="currentStep < steps.length - 1" v-on:click="next" class="text-center p-5 text-5xl mt-4">
            <i className="ion-arrow-right-c" />
          </button>
          <button v-else class="text-2xl bg-green-300 text-white p-5 rounded" v-on:click="next">
            Submit
          </button>
        </div>
    </div>
</template>

<script>
import Information from './Steps/Information.vue';
import About from './Steps/About.vue';
import Profile from './Steps/Profile.vue';

export default {
  name: 'MultiSteps',
  data () {
    return {
      currentStep: 0,
      formValue: {
        information: {
          name: 'Manoj',
          age: 0,
          dob: '',
          email: 'justanothermanoj@gmail.com'
        },
        about: {
          address: '',
          gender: ''
        },
        profile: {
          profilePicture: '',
          bio: ''
        },
      },
      steps: [
        {
          component: Information,
          label: 'information'
        },
        {
          component: About,
          label: 'about'
        },
        {
          component: Profile,
          label: 'profile'
        }
      ]
    }
  },
  methods: {
    next () {
      this.currentStep += 1;
    },
    previous () {
      this.currentStep -= 1;
    }
  },
  components: [
    Information,
    About,
    Profile
  ]
}
</script>
