<template>
  <section class="mb-5">
    <!-- Desktop -->
    <div class="py-8 bg-theme-feature-background hidden md:flex xl:rounded-lg items-center">
      <div
        class="ml-10 pr-8 flex-auto min-w-0"
      >
        <div class="flex items-center text-grey mb-2">
          <span>Address</span>
        </div>
        <div class="flex">
          <div class="text-lg text-white semibold truncate">
            <span class="mr-2">{{ wallet.address }}</span>
          </div>
          <Clipboard
            v-if="wallet.address"
            :value="wallet.address"
          />
        </div>
      </div>
      <div
        class="flex-none border-r border-grey-dark px-9"
      >
        <div class="text-grey mb-2">
          Balance (USD)
        </div>
        <div class="text-lg text-white semibold">
          <span v-tooltip="readableCurrency(wallet.balance)">
            {{ readableCrypto(wallet.balance, false) }}
          </span>
        </div>
      </div>

      <div class="flex-none px-8">
      </div>
    </div>
  </section>
</template>

<script type="text/ecmascript-6">
import { mapGetters } from 'vuex'

export default {
  name: 'WalletDetails',

  props: {
    wallet: {
      type: Object,
      required: true
    }
  },

  data: () => ({
    view: 'public',
    showModal: false
  }),

  computed: {
    ...mapGetters('network', ['knownWallets']),

    name () {
      return this.knownWallets[this.wallet.address]
    }
  },

  methods: {
    setView (view) {
      this.view = view
    },

    toggleModal () {
      this.showModal = !this.showModal
    }
  }
}
</script>

<style scoped>
.address-button {
  background-color: #0964e4;
}

.address-button:hover {
  background-color: #0964e4;
  transform: scale(1.1);
}
</style>
