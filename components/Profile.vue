<template>
  <div class="">
    <img
      class="rounded-full h-48"
      :src="userdetails.avatar_url"
      alt=""
      @load="getRepos"
    />
    <Repos :repodetails="repodetails" />
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
      repodetails: [],
    }
  },
  methods: {
    async getRepos() {
      const repoUrl = this.userdetails.repos_url
      const data = await fetch(repoUrl)
      data.json().then((response) => {
        this.repodetails = response.sort(
          (a, b) => new Date(a.created_at) - new Date(b.created_at)
        )
        this.repodetails.reverse()
        console.log(this.repodetails)
        // console.log(response)
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
