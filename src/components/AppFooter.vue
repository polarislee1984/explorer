<template>
  <footer class="AppFooter px-5 md:px-10 flex-col lg:flex-row">
    <div class="mb-4 lg:mb-0 text-center md:text-left">
      <span class="block md:inline-block mb-4 md:mb-0 text-center">&copy; <a
        href="https://www.bluebarricade.com"
        target="_blank"
      >bluebarricade.com</a> | 2019. {{ $t("All rights reserved") }}</span> <div class="block md:inline-block">
        <span class="hidden md:inline-block"> | </span> <span>{{ $t("Version") }}: <a
          target="_blank"
        >v1.0</a> </span>
      </div>
    </div>
  </footer>
</template>

<script type="text/ecmascript-6">
import moment from 'moment'

export default {
  name: 'AppFooter',

  computed: {
  }
}
</script>

<style>
.AppFooter {
  @apply .flex .flex-wrap .max-w-2xl .mx-auto .py-8 .text-theme-text-tertiary .justify-between .items-center;
}
</style>
