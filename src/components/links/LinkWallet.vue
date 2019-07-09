<template>
  <span class="block md:inline-block">
    <RouterLink
      :to="{ name: 'wallet', params: { address: address } }"
    >
      <span>
        <span class="hidden md:inline-block">{{ trunc ? truncate(address) : address }}</span>
        <span class="md:hidden">{{ truncate(address) }}</span>
      </span>
    </RouterLink>
  </span>
</template>

<script type="text/ecmascript-6">
import { mapGetters } from 'vuex'

export default {
  name: 'LinkWallet',

  props: {
    address: {
      type: String,
      required: false,
      default: ''
    },
    asset: {
      type: Object,
      required: false,
      default: null
    },
    type: {
      type: Number,
      required: false,
      default: 0
    },
    trunc: {
      type: Boolean,
      default: true
    }
  },

  computed: {
    ...mapGetters('delegates', ['delegates']),
    ...mapGetters('network', ['knownWallets'])
  }
}
</script>
