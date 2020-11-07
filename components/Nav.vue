<template>
  <div class="md:px-32 lg:px-64 sticky top-0 z-50 nav">
    <div class="grid grid-cols-4 justify-items-auto py-5">
      <div
        class="flex justify-center items-center"
        @click="$colorMode.preference = 'system'"
      >
        <IconSystem />
      </div>
      <div
        class="flex justify-center items-center"
        @click="$colorMode.preference = 'light'"
      >
        <IconLight />
      </div>
      <div
        class="flex justify-center items-center"
        @click="$colorMode.preference = 'dark'"
      >
        <IconDark />
      </div>
      <div
        class="flex justify-center items-center"
        @click="$colorMode.preference = 'sepia'"
      >
        <IconSepia />
      </div>
    </div>
  </div>
</template>

<script>
import IconSystem from '@/assets/icons/system.svg?inline'
import IconLight from '@/assets/icons/light.svg?inline'
import IconDark from '@/assets/icons/dark.svg?inline'
import IconSepia from '@/assets/icons/sepia.svg?inline'

export default {
  components: {
    IconSystem,
    IconLight,
    IconDark,
    IconSepia,
  },
  data() {
    return {
      colors: ['system', 'light', 'dark', 'sepia'],
    }
  },
}
</script>

<style>
.nav {
  background-color: var(--bg);
}
</style>
