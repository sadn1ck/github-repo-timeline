<template>
  <section class="text-gray-700 body-font py-16 md:pl-32">
    <div
      v-for="(repo, i) in repodetails"
      :key="i"
      class="container sm:px-0 md:px-5 mx-auto flex flex-wrap"
    >
      <div class="flex relative pb-10 sm:items-center">
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
          <div class="flex-grow sm:pl-6 mt-6 sm:mt-0">
            <h2 class="font-medium title-font text-gray-900 mb-1 text-xl">
              <a :href="repodetails[i].html_url" target="_blank">
                {{ repodetails[i].name }}
              </a>
              <small v-if="repodetails[i].fork"> (fork) </small>
            </h2>
            <p class="leading-relaxed">
              {{ repodetails[i].description }}
            </p>
            <p class="py-2">
              <b>Created on:</b>
              {{ new Date(repodetails[i].created_at).toDateString() }}
            </p>
            <p class="py-2">
              <b>Updated on:</b>
              {{ new Date(repodetails[i].updated_at).toDateString() }}
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
  mounted() {
    console.log(this.repodetails)
  },
}
</script>

<style></style>
