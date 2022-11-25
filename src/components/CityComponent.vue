<template>
    <div class="country" @click="clickeable ? $emit('click') : null">
        <img
          width="200"
          height="200"
          :src="'../assets/city.png'"
        />
        <h1>{{ name }}</h1>
        <h2>{{ country_name }}</h2>
        <h3>{{ state_name }}</h3>
        <h3>{{ latitude }}</h3>
        <h3>{{ longitude }}</h3>
    </div>
        
</template>


<script>
export default {
  name: "CityComponent",
  props: [
    "name",
    "country_name",
    "state_name",
    "latitude",
    "longitude",
  ],
};


<style scoped>
.city {
    padding: 2px;
    white-space: nowrap;
    width: 350px;
    height: 350px;
    border-style: solid;
    border-radius: 5px;
    border-color: grey;
    }
h1 {
    overflow: hidden;
    text
    }
</style>