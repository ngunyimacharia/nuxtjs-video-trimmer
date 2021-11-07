<template>
  <div class="mt-12">
    <form
      action="#"
      method="POST"
      class="grid grid-cols-1 gap-y-6 sm:grid-cols-2 sm:gap-x-8"
      @submit.prevent="submit"
    >
      <div class="sm:col-span-2">
        <label for="file" class="block text-sm font-medium text-gray-700"
          >File</label
        >
        <div class="mt-1">
          <input
            accept="video/*"
            @change="handleFile"
            type="file"
            name="file"
            id="file"
            class="
              py-3
              px-4
              block
              w-full
              shadow-sm
              focus:ring-indigo-500 focus:border-indigo-500
              border-gray-300
              rounded-md
            "
          />
        </div>
      </div>
      <div class="sm:col-span-2">
        <p
          v-if="uploading"
          class="text-center text-sm font-semibold text-gray-700"
        >
          Uploading...
        </p>
        <button
          v-else
          type="submit"
          class="
            w-full
            inline-flex
            items-center
            justify-center
            px-6
            py-3
            border border-transparent
            rounded-md
            shadow-sm
            text-base
            font-medium
            text-white
            bg-indigo-600
            hover:bg-indigo-700
            focus:outline-none
            focus:ring-2
            focus:ring-offset-2
            focus:ring-indigo-500
          "
        >
          Upload
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      uploading: false,
      uploadVideo: null,
    };
  },
  methods: {
    async handleFile(e) {
      this.uploadVideo = e.target.files[0];
    },
    async readData(f) {
      return new Promise((resolve) => {
        const reader = new FileReader();
        reader.onloadend = () => resolve(reader.result);
        reader.readAsDataURL(f);
      });
    },
    async submit() {
      this.uploading = true;
      const videoData = await this.readData(this.uploadVideo);
      this.cloudinaryVideo = await this.$cloudinary.upload(videoData, {
        upload_preset: "default-preset",
        folder: "nuxtjs-video-trimmer",
      });
      this.$emit("uploaded", this.cloudinaryVideo);
      this.uploading = false;
    },
  },
};
</script>