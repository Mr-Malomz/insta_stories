<template>
  <div
    class="relative flex items-top justify-center min-h-screen bg-gray-100 sm:items-center sm:pt-0"
  >
    <div class="max-w-4xl mx-auto sm:px-6 lg:px-8">
      <div
        class="flex flex-col lg:flex-row items-center mt-8 bg-white overflow-hidden shadow sm:rounded-lg p-6"
      >
        <div
          class="w-44 h-44 flex items-center justify-center border-indigo-400 border-4 mr-4 rounded-full cursor-pointer"
          role="button"
          @click="toggleStory"
        >
          <cld-image
            :public-id="images[0]"
            class="rounded-full w-40 h-40"
          ></cld-image>
        </div>
        <Info />
      </div>
    </div>
    <div
      v-if="showStory"
      class="absolute h-screen w-screen bg-black bg-opacity-70 top-0 h-100vh"
    >
      <section class="flex justify-end p-4">
        <button
          @click="toggleStory"
          class="px-4 py-2 rounded-lg shadow-md bg-indigo-700 font-semibold text-white capitalize"
        >
          close
        </button>
      </section>
      <section class="flex items-center justify-center">
        <Stories
          v-if="showStory"
          :stories="images"
          class="absolute top-10 left h-4/5 w-2/4"
        />
      </section>
    </div>
  </div>
</template>

<script>
import { Stories } from 'vue-insta-stories'
import images from '@/utils/stories.json'

export default {
  components: { Stories },
  data() {
    return {
      images,
      showStory: false,
    }
  },

  methods: {
    toggleStory() {
      this.showStory = !this.showStory
    },
  },
}
</script>
