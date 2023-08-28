<template>
  <div class="text-3xl h-screen flex flex-col">
    <div class="flex">
      Page Header
    </div>
    <div class="text-3xl h-screen flex justify-around">
      <div class="flex bg-blue-400 grow">
        <div class="flex items-start">
          <UButton label="Open" @click="isOpen = true" />
        </div>

        <!-- DOESN'T WORK WHEN STYLED LOCALLY EITHER -->
        <!-- <UModal 
          v-model="isOpen"
          :ui="{
            modal: {
              wrapper: 'z-100'
            },
          }"
        >
          <UCard>
            <template #header>
              This is a header
            </template>
            This is the content area where stuff gets chopped under leaflet.
          </UCard>
        </UModal> -->

        <UModal 
          v-model="isOpen"
        >
          <UCard>
            <template #header>
              This is a header
            </template>
            This is the content area where stuff gets chopped under leaflet.
          </UCard>
        </UModal>
      </div>
      <div class="flex bg-green-400 grow">
        <LMap
          ref="map"
          :zoom="zoom"
          :center="[47.21322, -1.559482]"
        >
          <LTileLayer
            url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
            attribution="&amp;copy; <a href=&quot;https://www.openstreetmap.org/&quot;>OpenStreetMap</a> contributors"
            layer-type="base"
            name="OpenStreetMap"
          />
        </LMap>
      </div>
    </div>
  </div>
  <UModal></UModal>
</template>

<script setup>
const isOpen = ref(false)
const zoom = ref(6)
</script>
