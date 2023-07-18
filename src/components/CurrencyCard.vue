<template>
  <div>
    <md-card>
      <md-card-header>
        <div class="md-title">{{ currency.code }} - {{ currency.currency}}</div>
      </md-card-header>
      <md-card-content>
        <div class="md-body-1">Currency name: {{ currency.currency }}</div>
        <div class="md-body-1">Currency code: {{ currency.code }}</div>
        <div class="md-body-1">Ask: {{ currency.ask }}</div>
        <div class="md-body-1">Bid: {{ currency.bid }}</div>
      </md-card-content>
    </md-card>
  </div>
</template>

<script>
export default {
  name: "CurrencyCard",
  props: {
    currency: Object
  }
}
</script>

<style scoped>
.md-card {
  width: 320px;
  margin: 4px;
  display: inline-block;
  vertical-align: top;
}
</style>