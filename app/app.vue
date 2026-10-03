<script setup lang="ts">
import InputBox from './components/InputBox.vue'
import BaseLayout from './layouts/BaseLayout.vue'
import "@catppuccin/palette/css/catppuccin.css"
import { computed, ref } from 'vue'

const grantRate = ref(0)
const grantHours = ref(0)

const grants = ref(0)
const price = ref(0)
const hours = ref(0)

function updateGrantRate(value: number) {
  grantRate.value = value
  recalculateFromGrants()
}

function updateGrantHours(value: number) {
  grantHours.value = value
  recalculateFromGrants()
}

function updateGrants(value: number) {
  grants.value = value
  recalculateFromGrants()
}

function updatePrice(value: number) {
  price.value = value
  recalculateFromPrice()
}

function updateHours(value: number) {
  hours.value = value
  recalculateFromHours()
}

function recalculateFromGrants() {
  if (grantRate.value > 0 && grantHours.value > 0) {
    price.value = grants.value * grantRate.value
    hours.value = grants.value * grantHours.value
  }
}

function recalculateFromPrice() {
  if (grantRate.value > 0 && grantHours.value > 0) {
    grants.value = price.value / grantRate.value
    hours.value = grants.value * grantHours.value
  }
}

function recalculateFromHours() {
  if (grantHours.value > 0 && grantRate.value > 0) {
    grants.value = hours.value / grantHours.value
    price.value = grants.value * grantRate.value
  }
}
</script>

<template>
  <div>
    <NuxtRouteAnnouncer />
    <BaseLayout>
      <p>$</p>
      <InputBox 
        type="number" 
        id="grandRate" 
        :model-value="grantRate" 
        @update:model-value="updateGrantRate(Number($event))"
        label="the grant's rate:"
      />
      <p>/</p>
      <InputBox
        type="number"
        id="grantHours"
        :model-value="grantHours"
        @update:model-value="updateGrantHours(Number($event))"
        label="per how many hours:"
      />
      <p>h</p>
      <p>/</p>
      <InputBox 
        type="number" 
        id="price" 
        :model-value="price" 
        @update:model-value="updatePrice(Number($event))"
        label="your target price:"
      />
      <p>=</p>
      <InputBox 
        type="number" 
        id="hours" 
        :model-value="hours" 
        @update:model-value="updateHours(Number($event))"
        label="your needed hours:"
      />
      <p>or</p>
      <InputBox 
        type="number" 
        id="grants" 
        :model-value="grants" 
        @update:model-value="updateGrants(Number($event))"
        label="your stacks of grants:"
      />
    </BaseLayout>
  </div>
</template>

<style>
* {
  font-family: "Comic Neue";
}
</style>