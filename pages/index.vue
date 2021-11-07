<template>
  <div class="bg-white py-16 px-4 overflow-hidden sm:px-6 lg:px-8 lg:py-24">
    <div class="relative max-w-xl mx-auto">
      <svg
        class="absolute left-full transform translate-x-1/2"
        width="404"
        height="404"
        fill="none"
        viewBox="0 0 404 404"
        aria-hidden="true"
      >
        <defs>
          <pattern
            id="85737c0e-0916-41d7-917f-596dc7edfa27"
            x="0"
            y="0"
            width="20"
            height="20"
            patternUnits="userSpaceOnUse"
          >
            <rect
              x="0"
              y="0"
              width="4"
              height="4"
              class="text-gray-200"
              fill="currentColor"
            />
          </pattern>
        </defs>
        <rect
          width="404"
          height="404"
          fill="url(#85737c0e-0916-41d7-917f-596dc7edfa27)"
        />
      </svg>
      <svg
        class="absolute right-full bottom-0 transform -translate-x-1/2"
        width="404"
        height="404"
        fill="none"
        viewBox="0 0 404 404"
        aria-hidden="true"
      >
        <defs>
          <pattern
            id="85737c0e-0916-41d7-917f-596dc7edfa27"
            x="0"
            y="0"
            width="20"
            height="20"
            patternUnits="userSpaceOnUse"
          >
            <rect
              x="0"
              y="0"
              width="4"
              height="4"
              class="text-gray-200"
              fill="currentColor"
            />
          </pattern>
        </defs>
        <rect
          width="404"
          height="404"
          fill="url(#85737c0e-0916-41d7-917f-596dc7edfa27)"
        />
      </svg>
      <div class="text-center">
        <h2
          class="
            text-3xl
            font-extrabold
            tracking-tight
            text-gray-900
            sm:text-4xl
          "
        >
          NuxtJs Video Trimmer
        </h2>
        <p class="mt-4 text-lg leading-6 text-gray-500">
          This service enables us to upload videos for trimming. Upload video in
          the form below to proceed.
        </p>
      </div>
      <upload v-if="!uploadVideo" />
    </div>
  </div>
</template>

<script>
import Upload from "../components/Upload.vue";
export default {
  components: {
    Upload,
  },
  data() {
    return {
      uploadVideo: {
        asset_id: "c082672c81c99157fbfaa87ed0345fae",
        public_id: "nuxtjs-video-trimmer/uocakxjs3ddthxiegoku",
        version: 1636256516,
        version_id: "35217d98cebcbbd1523211b529828ddf",
        signature: "10b53246bc211008b08252d8b5e42525c9883635",
        width: 3840,
        height: 2160,
        format: "mp4",
        resource_type: "video",
        created_at: "2021-11-07T03:41:56Z",
        tags: [],
        pages: 0,
        bytes: 22687114,
        type: "upload",
        etag: "e34d8ff931cb4864b23d797a78c77d59",
        placeholder: false,
        url: "http://res.cloudinary.com/hackit-africa/video/upload/v1636256516/nuxtjs-video-trimmer/uocakxjs3ddthxiegoku.mp4",
        secure_url:
          "https://res.cloudinary.com/hackit-africa/video/upload/v1636256516/nuxtjs-video-trimmer/uocakxjs3ddthxiegoku.mp4",
        access_mode: "public",
        audio: {
          codec: "aac",
          bit_rate: "253375",
          frequency: 48000,
          channels: 2,
          channel_layout: "stereo",
        },
        video: {
          pix_format: "yuv420p",
          codec: "h264",
          level: 52,
          profile: "High",
          bit_rate: "22006365",
          time_base: "1/60",
        },
        is_audio: false,
        frame_rate: 60,
        bit_rate: 22215044,
        duration: 8.17,
        rotation: 0,
        nb_frames: 489,
      },
    };
  },
};
</script>