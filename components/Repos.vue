<template>
  <section class="text-gray-700 body-font">
    <div
      v-for="(repo, i) in repodetails"
      :key="i"
      class="container px-5 py-24 mx-auto flex flex-wrap"
    >
      <div class="flex relative pb-10 sm:items-center md:w-2/3 mx-auto">
        <div
          class="h-full w-6 absolute inset-0 flex items-center justify-center"
        >
          <div class="h-full w-1 bg-gray-200 pointer-events-none"></div>
        </div>
        <div
          class="flex-shrink-0 w-6 h-6 rounded-full mt-10 sm:mt-0 inline-flex items-center justify-center bg-indigo-500 text-white relative z-10 title-font font-medium text-sm"
        >
          {{ i + 1 }}
        </div>
        <div
          class="flex-grow md:pl-8 pl-6 flex sm:items-center items-start flex-col sm:flex-row"
        >
          <div
            class="flex-shrink-0 w-24 h-24 bg-indigo-100 text-indigo-500 rounded-full inline-flex items-center justify-center"
          >
            <svg
              fill="none"
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              class="w-12 h-12"
              viewBox="0 0 24 24"
            >
              <path d="M20 21v-2a4 4 0 00-4-4H8a4 4 0 00-4 4v2"></path>
              <circle cx="12" cy="7" r="4"></circle>
            </svg>
          </div>
          <div class="flex-grow sm:pl-6 mt-6 sm:mt-0">
            <h2 class="font-medium title-font text-gray-900 mb-1 text-xl">
              <a :href="repodetails[i].html_url" target="_blank">
                {{ repodetails[i].full_name }}</a
              >
            </h2>
            <p class="leading-relaxed">
              {{ repodetails[i].description }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    repodetails: {
      type: Array,
      default() {
        return []
      },
    },
  },
}
</script>

<style></style>
