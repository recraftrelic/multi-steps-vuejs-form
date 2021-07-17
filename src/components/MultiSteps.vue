<template>
    <div class="w-1/2 m-auto">
      <div v-if="!submitted">
        <component
          v-bind:is="steps[currentStep].component"
          v-bind:formValue="formValue[steps[currentStep].label]"
          @formValueChange="updateFormValue"
        />
        <div class="text-center">
          <button v-if="currentStep !== 0" v-on:click="previous" class="text-center p-5 text-5xl mt-4">
            <i className="ion-arrow-left-c" />
          </button>
          <button v-if="currentStep < steps.length - 1" v-on:click="next" class="text-center p-5 text-5xl mt-4">
            <i className="ion-arrow-right-c" />
          </button>
          <button v-else class="text-2xl bg-green-300 text-white p-5 rounded" v-on:click="submit">
            Submit
          </button>
        </div>
      </div>
      <div v-else class="text-5xl font-bold text-center shadow-lg p-10">
        <span><span class="text-green-500">Thank you for submitting the form.</span> <br/><br/> We will get back to you soon.</span>
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
      submitted: false,
      formValue: {
        information: {
          name: '',
          age: 0,
          dob: '',
          email: ''
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
    },
    updateFormValue (payload) {
      this.formValue = {
        ...this.formValue,
        [payload.label]: payload.data
      }
    },
    submit () {
      this.submitted = true;
      console.log(this.formValue)
    }
  },
  components: [
    Information,
    About,
    Profile
  ]
}
</script>
