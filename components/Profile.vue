<template>
  <div class="">
    <img class="rounded-full h-48" :src="userdetails.avatar_url" alt="" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      userdetails: {
        login: 'sadn1ck',
        id: 16396161,
        node_id: 'MDQ6VXNlcjE2Mzk2MTYx',
        avatar_url: 'https://avatars2.githubusercontent.com/u/16396161?v=4',
        gravatar_id: '',
        url: 'https://api.github.com/users/sadn1ck',
        html_url: 'https://github.com/sadn1ck',
        followers_url: 'https://api.github.com/users/sadn1ck/followers',
        following_url:
          'https://api.github.com/users/sadn1ck/following{/other_user}',
        gists_url: 'https://api.github.com/users/sadn1ck/gists{/gist_id}',
        starred_url:
          'https://api.github.com/users/sadn1ck/starred{/owner}{/repo}',
        subscriptions_url: 'https://api.github.com/users/sadn1ck/subscriptions',
        organizations_url: 'https://api.github.com/users/sadn1ck/orgs',
        repos_url: 'https://api.github.com/users/sadn1ck/repos',
        events_url: 'https://api.github.com/users/sadn1ck/events{/privacy}',
        received_events_url:
          'https://api.github.com/users/sadn1ck/received_events',
        type: 'User',
        site_admin: false,
        name: 'Anik Das',
        company: null,
        blog: 'https://www.linkedin.com/in/sadn1ck/',
        location: 'IIEST, Shibpur',
        email: null,
        hireable: true,
        bio: 'Frontend | DevOps | Security @0xw3bs3c ',
        twitter_username: null,
        public_repos: 35,
        public_gists: 3,
        followers: 40,
        following: 62,
        created_at: '2015-12-22T04:54:39Z',
        updated_at: '2020-10-29T17:04:04Z',
      },
    }
  },
}
</script>

<style>
.force-center {
  display: grid;
  place-items: center;
}
</style>
