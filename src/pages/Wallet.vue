<template>
  <div class="max-w-2xl mx-auto md:pt-5">
    <ContentHeader>{{ $t("Wallet summary") }}</ContentHeader>

    <WalletDetails :wallet="wallet" />

    <WalletTransactions
      :wallet="wallet"
    />
  </div>
</template>

<script type="text/ecmascript-6">
import {
  WalletDetails,
  WalletTransactions
} from '@/components/wallet'
import WalletService from '@/services/wallet'

export default {
  components: {
    WalletDetails,
    WalletTransactions
  },

  data: () => ({
    wallet: {},
    activeTab: 'all',
    username: ''
  }),

  computed: {
  },

  async beforeRouteEnter (to, from, next) {
    try {
      const response = await WalletService.find(to.params.address)
      next(vm => vm.setWallet(response))
    } catch (e) { next({ name: '404' }) }
  },

  async beforeRouteUpdate (to, from, next) {
    this.wallet = {}

    try {
      const response = await WalletService.find(to.params.address)
      this.setWallet(response)
      next()
    } catch (e) { next({ name: '404' }) }
  },

  methods: {
    async setWallet (wallet) {
      this.wallet = wallet
    }
  }
}
</script>
