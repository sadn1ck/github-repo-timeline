<template>
  <div class="">
    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
      <div class="mx-auto">
        <img
          class="rounded-full h-48"
          :src="userdetails.avatar_url"
          alt=""
          @load="getRepos"
        />
      </div>
      <div class="p-5 grid grid-cols-1 text-center" v-if="showdetails">
        <a class="my-auto" target="_blank" :href="userdetails.html_url">
          <span class="font-bold text-2xl"> {{ userdetails.login }}</span>
          <div class="text-md">({{ userdetails.name }})</div>
        </a>
        <div class="my-auto text-xl"></div>
        <div class="my-auto text-xl">
          Public Repos: {{ repoDetails.length }}
        </div>
        <div class="my-auto text-xl">Followers: {{ followerDetails }}</div>
      </div>
    </div>
    <Repos :repodetails="repoDetails" />
  </div>
</template>

<script>
import Repos from '~/components/Repos'
export default {
  components: { Repos },
  props: {
    userdetails: {
      type: Object,
      default() {
        return {}
      },
    },
  },
  data() {
    return {
      repoDetails: [],
      followerDetails: 0,
      showdetails: false,
    }
  },
  methods: {
    async getRepos() {
      const repoUrl = this.userdetails.repos_url
      const data = await fetch(repoUrl)
      data.json().then((response) => {
        this.repoDetails = response.sort(
          (a, b) => new Date(a.created_at) - new Date(b.created_at)
        )
        this.repoDetails.reverse()
        console.log(this.repoDetails)
        this.showdetails = true
        // console.log(response)
        this.getFollowers()
      })
    },
    async getFollowers() {
      const followersUrl = this.userdetails.followers_url
      const data = await fetch(followersUrl)
      data.json().then((response) => {
        this.followerDetails = response.length
        // console.log(this.followerDetails)
        this.showdetails = true
      })
    },
  },
}
</script>

<style>
.force-center {
  display: grid;
  place-items: center;
}
</style>
