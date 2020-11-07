<template>
  <div class="px-8 md:px-32 lg:px-64 pt-8 md:pt-16 mx-auto">
    <div class="mb-4">
      <div class="force-center">
        <label
          class="block text-4xl font-bold mb-2 p-5 text-center"
          for="username"
        >
          GitHub Repo Timeline
        </label>
      </div>
      <form action="" @submit.prevent="submit">
        <div class="force-center p-5">
          <input
            v-model="username"
            type="text"
            class="relative outline-none text-gray-900 py-5 px-5 rounded-xl w-full md:w-2/3 shadow focus:shadow-2xl text-base focus:outline-none transition duration-200"
            placeholder="GitHub username, for eg., torvalds"
          />
        </div>
        <div class="text-lg w-full flex justify-center">
          <div class="flex">
            <div
              class="mr-4 bg-white border-2 rounded border-gray-400 w-6 h-6 flex flex-shrink-0 justify-center items-center focus-within:border-blue-500"
            >
              <input
                type="checkbox"
                class="opacity-0 absolute"
                v-model="showForks"
              />
              <svg
                class="fill-current hidden w-4 h-4 text-green-500 pointer-events-none"
                viewBox="0 0 20 20"
              >
                <path d="M0 11l2-2 5 5L18 3l2 2L7 18z" />
              </svg>
            </div>
            <span class=""> Display forks </span>
          </div>
        </div>
        <div class="force-center p-5">
          <button
            type="submit"
            class="px-10 py-3 bg-gray-700 text-white hover:bg-green-500 rounded transition duration-200 focus:outline-none shadow hover:shadow-2xl"
          >
            Submit
          </button>
        </div>
      </form>

      <div v-if="invaliduser" class="force-center">
        <label
          class="block text-1xl font-bold mb-2 p-5 text-red-600"
          for="username"
        >
          No such username!
        </label>
      </div>
    </div>
    <div v-if="receiveddata">
      <Profile :userdetails="userdetails" :show-forks="showForks" />
    </div>
  </div>
</template>

<script>
import Profile from '~/components/Profile'
export default {
  components: {
    Profile,
  },
  data() {
    return {
      valid: null,
      receiveddata: false,
      invaliduser: false,
      username: '',
      userdetails: {},
      showForks: true,
    }
  },
  methods: {
    async submit() {
      // resetting before sending request so as not to pollute incoming data
      this.valid = null
      this.receiveddata = false
      this.invaliduser = false
      this.userdetails = {}
      const data = await fetch(`https://api.github.com/users/${this.username}`)
      data.json().then((response) => {
        if (!(response.message === 'Not Found')) {
          this.receiveddata = true
          this.userdetails = response
        } else {
          this.invaliduser = true
        }
      })
    },
  },
  head() {
    return {
      title: 'GitHub Repo Timeline',
    }
  },
}
</script>

<style>
.force-center {
  display: grid;
  place-items: center;
}
input:checked + svg {
  display: block;
}
</style>
