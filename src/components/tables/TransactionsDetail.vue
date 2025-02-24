<template>
  <Loader :data="transactions">
    <table-component
      v-if="transactions && transactions.length > 0"
      :data="transactions"
      :show-filter="false"
      :show-caption="false"
      sort-by="timestamp.unix"
      sort-order="desc"
      table-class="w-full"
    >
      <table-column
        :label="$t('ID')"
        show="id"
        header-class="left-header-start-cell"
        cell-class="left-start-cell"
      >
        <template slot-scope="row">
          <LinkTransaction
            :id="row.id"
            :smart-bridge="row.vendorField"
            :show-smart-bridge-icon="showSmartBridgeIcon"
          />
        </template>
      </table-column>

      <table-column
        :label="$t('Timestamp')"
        show="timestamp.unix"
        header-class="left-header-cell hidden lg:table-cell"
        cell-class="left-cell hidden lg:table-cell"
      >
        <template slot-scope="row">
          {{ readableTimestamp(row.timestamp) }}
        </template>
      </table-column>

      <table-column
        :label="$t('Sender')"
        show="sender"
        header-class="left-header-cell"
        cell-class="left-cell"
      >
        <template slot-scope="row">
          <LinkWallet :address="row.sender" />
        </template>
      </table-column>

      <table-column
        :label="$t('Recipient')"
        show="recipient"
        header-class="left-header-cell"
        cell-class="left-cell"
      >
        <template slot-scope="row">
          <LinkWallet
            :address="row.recipient"
            :type="row.type"
            :asset="row.asset"
          />
        </template>
      </table-column>

      <table-column
        :label="$t('Amount')"
        show="amount"
        header-class="right-header-cell"
        cell-class="right-cell"
      >
        {{ readableCrypto(100) }}
      </table-column>

      <table-column
        :label="$t('Fee')"
        show="fee"
        header-class="right-header-cell hidden md:table-cell"
        cell-class="right-cell hidden md:table-cell"
      >
        {{ readableCrypto(5) }}
      </table-column>
    </table-component>

    <div
      v-else
      class="px-5 md:px-10"
    >
      <span>{{ $t("No results") }}</span>
    </div>
  </Loader>
</template>

<script type="text/ecmascript-6">
import { mapGetters } from 'vuex'
import CryptoCompareService from '@/services/crypto-compare'

export default {
  name: 'TableTransactionsDetailDesktop',

  props: {
    transactions: {
      validator: value => {
        return Array.isArray(value) || value === null
      },
      required: true
    }
  },

  computed: {
    ...mapGetters('network', ['activeDelegates']),

    showSmartBridgeIcon () {
      if (this.transactions) {
        return this.transactions.some(transaction => {
          return !!transaction.vendorField
        })
      }

      return false
    }
  },

  watch: {
    transactions () {
      this.updatePrices()
    }
  },

  created () {
    this.updatePrices()
  },

  methods: {
    async updatePrices () {
      if (!this.transactions) {
        return
      }

      for (const transaction of this.transactions) {
        transaction.price = await CryptoCompareService.dailyAverage(transaction.timestamp.unix)
      }
    }
  }
}
</script>

<style scoped>
.icon {
  width: 16px;
  height: 16px;
}
</style>
