<template>
  <header
    v-click-outside="closeHeader"
    class="AppHeader min-h-50px md:min-h-80px mb-5 sm:mb-10 xl:rounded-md"
  >
    <RouterLink
      :to="{ name: 'home' }"
      class="logo-container w-50px md:w-80px h-50px md:h-80px flex-none text-2xl xl:rounded-l-md flex justify-center items-center"
    >
      <img
        class="logo max-w-25px md:max-w-38px"
        src="@/assets/images/bluebarry-logo.png"
      >
    </RouterLink>

    <div class="w-full relative hidden xl:flex">
      <HeaderSearch v-if="headerType === 'search'" />
      <HeaderDefault v-else />
      <HeaderMenuDesktop v-if="menuVisible" />
    </div>

  </header>
</template>

<script type="text/ecmascript-6">
import {
  HeaderDefault,
  HeaderSearch,
  HeaderCurrenciesDesktop,
  HeaderCurrenciesMobile,
  HeaderLanguagesDesktop,
  HeaderLanguagesMobile,
  HeaderMenuDesktop,
  HeaderMenuMobile
} from '@/components/header'
import { mapGetters } from 'vuex'

export default {
  name: 'AppHeader',

  components: {
    HeaderDefault,
    HeaderSearch,
    HeaderCurrenciesDesktop,
    HeaderCurrenciesMobile,
    HeaderLanguagesDesktop,
    HeaderLanguagesMobile,
    HeaderMenuDesktop,
    HeaderMenuMobile
  },

  computed: {
    ...mapGetters('ui', ['headerType', 'menuVisible'])
  },

  methods: {
    closeHeader () {
      this.$store.dispatch('ui/setHeaderType', null)
    }
  }
}
</script>

<style scoped>
.AppHeader {
  @apply .flex .sticky .top-0 .z-50 .max-w-2xl .mx-auto .bg-theme-nav-background .shadow-theme;
}
</style>
