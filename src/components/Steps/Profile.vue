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
      />
      <div class="cursor-pointer flex justify-center items-center flex-col border-green-300 border-2 w-full h-72 mt-4 mb-4 rounded">
        <i class="ion-upload text-5xl" />
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
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'Profile',
}
</script>
