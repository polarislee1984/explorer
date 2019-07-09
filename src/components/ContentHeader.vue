<template>
  <div>
    <div class="flex justify-between flex-wrap px-5 sm:px-10 xl:px-0">
      <h1 class="text-2xl md:text-3xl mb-5 md:mb-6 text-theme-text-primary sm:mr-5">
        <slot />
      </h1>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
import { mapGetters } from 'vuex'

export default {
  name: 'ContentHeader',

  computed: {
    ...mapGetters('network', ['alias', 'supply', 'height']),
    ...mapGetters('currency', ['name', 'rate', 'symbol']),

    isMain () {
      return this.alias === 'Main'
    }
  }
}
</script>
