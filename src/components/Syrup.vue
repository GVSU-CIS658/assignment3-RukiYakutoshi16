<template>
  <div class="syrup"></div>
</template>

<script setup lang="ts">
import { SyrupType } from '../stores/beverage';
import {watch} from "vue";

type SyrupProp ={
  syrup: SyrupType
}
const props = defineProps<SyrupProp>()
  watch(()=>props.syrup, x => {x.id=="s1"?
  document.documentElement.style.setProperty("--syrup-transparent", "0%" )
  :updateSyrupColor(x.color);})

function updateSyrupColor(color:string){
document.documentElement.style.setProperty("--syrup-color", color );
document.documentElement.style.setProperty("--syrup-transparent", "20%" );
}
</script>

<style lang="scss" scoped>
$transparent: 20% !default;
@mixin syrup-color($color,$transparent){
  background-color: $color;
  height: $transparent;
}

.syrup {
  @include syrup-color(var(--syrup-color),var(--syrup-transparent));
  transform: translateY(400%);
  position: relative;
  width: 100%;
  animation: pour-tea 2s 1s forwards;
  z-index: 2;
}
</style>
