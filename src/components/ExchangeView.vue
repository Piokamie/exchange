<template>
  <div class="exchange-container">
    <h1>Exchange</h1>
    <multiselect v-model="selected" :options="currencies" label="currency" track-by="code" :searchable="true"
                 :multiple="true"></multiselect>
    <div class="carousel" v-if="selected">
      <carousel :autoplay="true" :perPage="3">
        <slide v-for="currency in selected" :key="currency.code">
          <currency-card :currency="currency"></currency-card>
        </slide>
      </carousel>
    </div>
    <div v-if="selected">

      <div width="100%" class="container-currency">
        <currency-card v-for="currency in selected" :key="currency.code" :currency="currency"></currency-card>
      </div>

    </div>
  </div>

</template>

<script>
import Multiselect from 'vue-multiselect'
import axios from "axios";
import CurrencyCard from "@/components/CurrencyCard.vue";
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'
import {Carousel, Slide} from 'vue-carousel';

export default {
  data() {
    return {
      currencies: [],
      selected: null,
      names: [],
    }
  },
  async mounted() {
    await this.getNames();
  },
  components: {
    Multiselect,
    CurrencyCard,
    Carousel,
    Slide
  },
  name: "ExchangeView",
  methods: {
    async getNames() {
      const response = await axios.get('http://api.nbp.pl/api/exchangerates/tables/C/?format=json');
      const data = response.data;
      console.log(data);
      data[0].rates.forEach(element => {
        this.currencies.push(element);
        this.names.push(element.currency + ' ' + element.code);
      });
    }
  },
}
</script>
<style src="vue-multiselect/dist/vue-multiselect.min.css"></style>
<style scoped>
.container-currency {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}

.carousel {
  color: magenta;
}
.exchange-container {
  width: 960px;
  justify-self: center;
}
</style>