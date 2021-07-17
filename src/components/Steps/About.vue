<template>
  <p class="text-5xl font-bold mb-9 text-center">Tell us about yourself</p>
  <div class="shadow-lg p-10 rounded">
    <div>
      <label class="font-bold text-2xl" for="address">Where do you live?</label>
      <br />
      <textarea
        name="address"
        id="address"
        class="w-full text-2xl p-2 border-2 rounded border-green-300 mt-4 mb-4"
        v-bind:value="formValue.address"
        @input="onChange"
      />
    </div>
    <div>
      <label class="font-bold text-2xl" for="dob">Are you a ...</label>
      <br />
      <div>
        <input
          type="radio"
          name="gender"
          id="dob"
          value="Female"
          class="text-2xl p-2 border-2 rounded border-green-300 mt-4 mb-4"
          @change="onChange"
        />
        <label class="text-lg font-bold ml-2">Female</label>
      </div>
      <div>
        <input
          type="radio"
          name="gender"
          id="dob"
          value="Male"
          class="text-2xl p-2 border-2 rounded border-green-300 mt-4 mb-4"
          @change="onChange"
        />
        <label class="text-lg font-bold ml-2">Male</label>
      </div>
      <div>
        <input
          type="radio"
          name="gender"
          id="dob"
          value="Other"
          class="text-2xl p-2 border-2 rounded border-green-300 mt-4 mb-4"
          @change="onChange"
        />
        <label class="text-lg font-bold ml-2">Other</label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'About',
  props: {
    formValue: {
      address: String,
      gender: String,
    }
  },
  emits: ['formValueChange'],
  methods: {
    onChange (e) {
      this.$emit('formValueChange', {
        label: 'about',
        data: {
          ...this.formValue,
          [e.target.name]: e.target.value
        }
      })
    }
  }
}
</script>
