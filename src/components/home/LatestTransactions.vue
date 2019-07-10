<template>
  <div>
    <Loader :data="transactions">
      <div>
        <TableTransactionsDesktop :transactions="transactions" />
      </div>
      <div class="mx-5 sm:mx-10 mt-5 md:mt-10 flex flex-wrap">
        <RouterLink
          :to="{ name: 'transactions', params: { page: 2 } }"
          tag="button"
          class="show-more-button"
        >
          {{ $t("Show more") }}
        </RouterLink>
      </div>
    </Loader>
  </div>
</template>

<script type="text/ecmascript-6">
//import TransactionService from '@/services/transaction'

export default {
  name: 'LatestTransactions',

  data: () => ({
    transactions: [
      {
        id:'60011bfb5184ec3dcce5cf42df8ab8b1346788fe3355546984eb68ba4ac61d62',
        sender:'AUexKjGtgsSpVzPLs6jNMM6vJ6znEVTQWK',
        recipient:'AJyn2dFkoqBN6dZ1siT9wWaRF2mwcVbcmA',
        fromAmount:100,
        toAmount:95,
        fromCurrency: 'USD',
        toCurrency: 'USD',
        fee:5,
        type:'Transfer',
        timestamp:new Date('2019-07-09 20:11:23').getTime(),
      },
      {
        id:'60011bfb5184ec3dcce5cf42df8ab8b1346788fe3355546984eb68ba4ac61d62',
        sender:'AUexKjGtgsSpVzPLs6jNMM6vJ6znEVTQWK',
        recipient:'AJyn2dFkoqBN6dZ1siT9wWaRF2mwcVbcmA',
        fromAmount:100,
        toAmount:95,
        fromCurrency: 'USD',
        toCurrency: 'USD',
        fee:5,
        type:'Transfer',
        timestamp:new Date('2019-07-09 20:11:23').getTime(),
      },
      {
        id:'60011bfb5184ec3dcce5cf42df8ab8b1346788fe3355546984eb68ba4ac61d62',
        sender:'AUexKjGtgsSpVzPLs6jNMM6vJ6znEVTQWK',
        recipient:'AJyn2dFkoqBN6dZ1siT9wWaRF2mwcVbcmA',
        fromAmount:100,
        toAmount:95,
        fromCurrency: 'USD',
        toCurrency: 'USD',
        fee:5,
        type:'Transfer',
        timestamp:new Date('2019-07-09 20:11:23').getTime(),
      },
      {
        id:'60011bfb5184ec3dcce5cf42df8ab8b1346788fe3355546984eb68ba4ac61d62',
        sender:'AUexKjGtgsSpVzPLs6jNMM6vJ6znEVTQWK',
        recipient:'AJyn2dFkoqBN6dZ1siT9wWaRF2mwcVbcmA',
        fromAmount:100,
        toAmount:95,
        fromCurrency: 'USD',
        toCurrency: 'USD',
        fee:5,
        type:'Transfer',
        timestamp:new Date('2019-07-09 20:11:23').getTime(),
      },
      {
        id:'60011bfb5184ec3dcce5cf42df8ab8b1346788fe3355546984eb68ba4ac61d62',
        sender:'AUexKjGtgsSpVzPLs6jNMM6vJ6znEVTQWK',
        recipient:'AJyn2dFkoqBN6dZ1siT9wWaRF2mwcVbcmA',
        fromAmount:100,
        toAmount:95,
        fromCurrency: 'USD',
        toCurrency: 'USD',
        fee:5,
        type:'Transfer',
        timestamp:new Date('2019-07-09 20:11:23').getTime(),
      }
    ]
  })
}
</script>
