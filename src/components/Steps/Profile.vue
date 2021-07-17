<template>
  <p class="text-5xl font-bold mb-9 text-center">Customize your profile</p>
  <div class="shadow-lg p-10 rounded">
    <div>
      <label class="font-bold text-2xl" for="fileUploader">Upload your profile picture</label>
      <input
        type="file"
        name="fileUploader"
        id="fileUploader"
        class="hidden"
        ref="fileUploader"
        @change="uploadFile"
      />
      <div v-on:click="$refs.fileUploader.click()" class="cursor-pointer flex justify-center items-center flex-col border-green-300 border-2 w-full h-72 mt-4 mb-4 rounded">
        <img v-if="formValue.profilePicture" class="h-40 rounded mb-4" v-bind:src="formValue.profilePicture" />
        <i v-else class="ion-upload text-5xl" />
        <p>Click here to upload</p>
      </div>
    </div>
    <div>
      <label class="font-bold text-2xl" for="bio">Describe yourself</label>
      <br />
      <textarea
        name="bio"
        id="bio"
        class="w-full text-2xl p-2 border-2 rounded border-green-300 mt-4 mb-4"
        v-bind:value="formValue.bio"
        @input="onChange"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'Profile',
  props: {
    formValue: {
      profilePicture: String,
      bio: String,
    }
  },
  emits: ['formValueChange'],
  methods: {
    uploadFile (e) {
      const file = e.target.files[0];

      if (!file) {
        return;
      }

      const fileReader = new FileReader();

      fileReader.onload = () => {
        this.$emit('formValueChange', {
          label: 'profile',
          data: {
            ...this.formValue,
            profilePicture: fileReader.result
          }
        })
      }

      fileReader.readAsDataURL(file)
    },
    onChange (e) {
      this.$emit('formValueChange', {
        label: 'profile',
        data: {
          ...this.formValue,
          [e.target.name]: e.target.value
        }
      })
    }
  }
}
</script>
