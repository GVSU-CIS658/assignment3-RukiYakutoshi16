<template>
  <div>
    <Beverage :isIced="currentTemp === 'Cold'"
              :baseType="currentBase"
              :syrupType="currentSyrup"
              :creamerType="currentCream" />
    <ul>
      <li>
        <template v-for="temp in temps" :key="temp">
          <label>
            <input
              type="radio"
              name="temperature"
              :id="`r${temp}`"
              :value="temp"
              v-model="currentTemp"
            />
            {{ temp }}
          </label>
        </template>
      </li>
       <li>
        <template v-for="base in bases" :key="base.id">
          <label>
            <input
              type="radio"
              name="base"
              :id="`r${base.id}`"
              :value="base"
              v-model="currentBase"
            />
            {{ base.name}}
          </label>
        </template>
      </li>
       <li>
        <template v-for="syrup in syrups" :key="syrup.id">
          <label>
            <input
              type="radio"
              name="syrup"
              :id="`r${syrup.id}`"
              :value="syrup"
              v-model="currentSyrup"
            />
            {{ syrup.name}}
          </label>
        </template>
      </li>
      <li>
        <template v-for="creamer in creamers" :key="creamer.id">
          <label>
            <input
              type="radio"
              name="creamer"
              :id="`r${creamer.id}`"
              :value="creamer"
              v-model="currentCream"
            />
            {{ creamer.name}}
          </label>
        </template>
      </li>
    </ul>
<h1>{{ currentCream }}</h1>

  </div>
</template>

<script setup lang="ts">
import Beverage from "./components/Beverage.vue";
import {bases, syrups, creamers, temps, currentTemp, defaultBase, defaultCreamer, defaultSyrup} from "./stores/beverage";

const currentCream = defaultCreamer;
const currentSyrup = defaultSyrup;
const currentBase = defaultBase;

</script>
<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}
ul {
  list-style: none;
}
</style>
