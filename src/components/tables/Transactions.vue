<template>
  <Loader :data="transactions">
    <table-component
      v-if="transactions && transactions.length > 0"
      :data="transactions"
      :show-filter="false"
      :show-caption="false"
      sort-by="timestamp"
      sort-order="desc"
      table-class="w-full"
    >
      <table-column
        label="ID"
        show="id"
        header-class="left-header-start-cell"
        cell-class="left-start-cell"
      >
        <template slot-scope="row">
          <LinkTransaction
            :id="row.id"
          />
        </template>
      </table-column>

      <table-column
        label="Timestamp"
        show="timestamp.unix"
        header-class="left-header-cell hidden md:table-cell"
        cell-class="left-cell hidden md:table-cell wrap-timestamp"
      >
        <template slot-scope="row">
          {{ readableTimestamp(row.timestamp) }}
        </template>
      </table-column>

      <table-column
        label="Sender"
        show="sender"
        header-class="left-header-cell"
        cell-class="left-cell"
      >
        <template slot-scope="row">
          <LinkWallet :address="row.sender" />
        </template>
      </table-column>

      <table-column
        label="Recipient"
        show="recipient"
        header-class="left-header-cell"
        cell-class="left-cell"
      >
        <template slot-scope="row">
          <LinkWallet
            :address="row.recipient"
          />
        </template>
      </table-column>
      <table-column
        label="Type"
        show="type"
        header-class="left-header-cell"
        cell-class="left-cell"
      >
        <template slot-scope="row">
          <span>{{row.type}}</span>
        </template>
      </table-column>

      <table-column
        label="From Amount"
        show="fromAmount"
        header-class="right-header-end-cell lg:pr-4"
        cell-class="right-end-cell lg:pr-4"
      >
        <template slot-scope="row">
          <span>{{row.fromCurrency}} {{row.fromAmount}}</span>
        </template>
      </table-column>

      <table-column
        label="To Amount"
        show="toAmount"
        header-class="right-header-end-cell lg:pr-4"
        cell-class="right-end-cell lg:pr-4"
      >
        <template slot-scope="row">
          <span>{{row.toCurrency}} {{row.toAmount}}</span>
        </template>
      </table-column>

      <table-column
        :label="$t('Fee (token)', { token: networkToken() })"
        show="fee"
        header-class="right-header-end-cell hidden lg:table-cell"
        cell-class="right-end-cell hidden lg:table-cell"
      >
        <template slot-scope="row">
          <span>{{row.fromCurrency}} {{row.fee}}</span>
        </template>
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
import CryptoCompareService from '@/services/crypto-compare'

export default {
  name: 'TableTransactionsDesktop',

  props: {
    transactions: {
      validator: value => {
        return Array.isArray(value) || value === null
      },
      required: true
    }
  },

  computed: {
  }
}
</script>

<style>
  .wrap-timestamp {
    white-space: normal;
  }

  @media(min-width: 870px) {
    .wrap-timestamp {
      white-space: nowrap;
    }
  }
</style>
