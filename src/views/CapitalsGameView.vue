<script>
import countries from "/src/datasets/countries.json";
import CountryComponent from "../components/CountryComponent.vue";

export default {
  name: "CapitalsGameView",
  components: {
    CountryComponent,
  },
  data() {
    return {
      country: {},
      capital: "",
      puntaje: 0,
    };
  },
  created() {
    this.country = countries[Math.floor(Math.random() * countries.length)];
  },
  methods: {
    setCapital(e) {
      this.capital = e.target.value;
    },
      //TODO: implementar. fija la capital del input.
    },
    adivinarCapital() {
      if (this.capital.toLowerCase() === this.country.capital.toLowerCase()) {
        this.puntaje++;
        this.country = countries[Math.floor(Math.random() * countries.length)];
        this.capital = "";
      } else {
        this.puntaje--;
        this.country = countries[Math.floor(Math.random() * countries.length)];
        this.capital = "";
      }
      //TODO: implementar. verifica se la adivinanza es correcta. 
      //Si es correcta, aumenta el puntaje y cambia el pais.
    },
  };
  
</script>

<template>
  <h1>Puntaje: {{ puntaje }}</h1>
  <div class="city">
    <CityComponent
      :name="country.capital"
      :country_name="country.name"
      :state_name="country.region"
      :state_code="country.iso2"
      :latitude="country.latitude"
      :longitude="country.longitude"
      ></CityComponent>
    
    <!-- TODO: usar los metodos definidos arriba dentro del input para llenar el estado de la capital a adivinar-->
    <input
      placeholder="Adivina la capital"
      v-model="capital"
      @input="setCapital"

    />
    <button @click="adivinarCapital">Adivina!</button>
    <div class="countries-container">
      
      <!--TODO: CREAR EL COMPONENTE PARA VISUALIZAR EL PAIS-->
      <CountryComponent
        :name="country.name"
        :currency_name="country.currency_name"
        :currency="country.currency"
        :region="country.region"
        :code="country.iso2"></CountryComponent>

    </div>
  </div>
</template>

<style scoped>
@media (min-width: 1024px) {
  .countries {
    align-items: center;
  }

  input {
    line-height: 2em;
  }

  .countries-container {
    margin-left: 35%;
    align-items: center;
    overflow-y: auto;
    vertical-align: middle;
    padding: 10px;
  }
}
</style>
