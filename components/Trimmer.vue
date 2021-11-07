<template>
  <div class="bg-white pt-12">
    <ul
      role="list"
      class="
        space-y-12
        sm:divide-y sm:divide-gray-200 sm:space-y-0 sm:-mt-8
        lg:gap-x-8 lg:space-y-0
      "
    >
      <li class="sm:py-8">
        <div
          class="
            space-y-4
            sm:grid sm:grid-cols-3 sm:items-start sm:gap-6 sm:space-y-0
          "
        >
          <div class="aspect-w-3 aspect-h-2 sm:aspect-w-3 sm:aspect-h-4">
            <cld-video
              class="object-cover shadow-lg rounded-lg"
              alt=""
              :public-id="video.public_id"
            />
          </div>
          <div class="sm:col-span-2">
            <ul>
              <li>Video format: {{ video.format }}</li>
              <li>Duration: {{ video.duration }} Seconds</li>
            </ul>
          </div>
        </div>
      </li>
    </ul>
    <form
      class="space-y-8 divide-y divide-gray-200"
      @submit.prevent="trimmed = true"
    >
      <div class="space-y-8 divide-y divide-gray-200">
        <div class="mt-6 grid grid-cols-3 gap-y-6 gap-x-4">
          <input
            min="0"
            step="0.01"
            :max="stop"
            placeholder="Start"
            type="number"
            name="start"
            v-model="start"
            id="start"
            class="
              shadow-sm
              focus:ring-indigo-500 focus:border-indigo-500
              block
              w-full
              sm:text-sm
              border-gray-300
              rounded-md
            "
          />

          <input
            type="number"
            :min="start"
            step="0.01"
            :max="video.duration + 0.1"
            placeholder="End"
            v-model="stop"
            name="end"
            id="end"
            class="
              shadow-sm
              focus:ring-indigo-500 focus:border-indigo-500
              block
              w-full
              sm:text-sm
              border-gray-300
              rounded-md
            "
          />
          <button
            type="submit"
            class="
              ml-3
              inline-flex
              justify-center
              py-2
              px-4
              border border-transparent
              shadow-sm
              text-sm
              font-medium
              rounded-md
              text-white
              bg-indigo-600
              hover:bg-indigo-700
              focus:outline-none
              focus:ring-2
              focus:ring-offset-2
              focus:ring-indigo-500
            "
          >
            Trim
          </button>
        </div>
      </div>
    </form>
    <cld-video
      class="pt-10"
      autoplay="true"
      v-if="trimmed"
      :public-id="video.public_id"
      controls="true"
    >
      <cld-transformation :end-offset="stop" :start-offset="start" />
    </cld-video>
    <div class="m-5 text-center" v-if="trimmed">
      <a
        target="_blank"
        class="
          mx-auto
          bg-white
          py-2
          px-4
          border border-gray-300
          rounded-md
          shadow-sm
          text-sm
          font-medium
          text-gray-700
          hover:bg-gray-50
          focus:outline-none
          focus:ring-2
          focus:ring-offset-2
          focus:ring-indigo-500
        "
        :href="trimmedUrl"
      >
        Download
      </a>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    video: {
      required: true,
      type: Object,
    },
  },
  data() {
    return {
      start: 0,
      stop: this.video.duration,
      trimmed: false,
    };
  },
  computed: {
    trimmedUrl() {
      return this.$cloudinary.video.url(this.video.public_id, {
        start_offset: this.start,
        end_offset: this.stop,
        format: "mp4",
      });
    },
  },
};
</script>
