<template>
  <div class="row justify-between">
    <div class="col-10">
      <b>Atual <b v-if="projectionStatus == 1">vs Projeção</b></b>
      <span class="q-ml-md bg-negative-light q-pa-xs tag-warning-light"> Atual </span>
      <span
        class="q-ml-md bg-positive-light q-pa-xs tag-positive-light"
        v-if="projectionStatus == 1"
      >
        Projeção
      </span>
    </div>
    <div class="col text-end" style="text-align-last: end">
      <q-btn
        size="xs"
        :icon="$filtersString.resolveUrl('img:icons/layout-list.svg')"
        padding="4px"
        class="q-mx-xs"
        :outline="projectionStatus !== 1"
        :flat="projectionStatus == 1"
        @click="storeLayout.setProjectionStatus(2)"
        v-if="projection"
      />
      <q-btn
        :outline="projectionStatus == 1"
        :flat="projectionStatus !== 1"
        color="primary"
        padding="4px"
        size="xs"
        class="q-mx-sm"
        :icon="$filtersString.resolveUrl('img:icons/layout-columns.svg')"
        @click="storeLayout.setProjectionStatus(1)"
        v-if="projection"
      />
      <slot></slot>
    </div>
  </div>
</template>
<script setup>
import { defineComponent } from 'vue'
import { useLayoutStore } from 'src/stores/layout'
import { storeToRefs } from 'pinia'
const storeLayout = useLayoutStore()
defineComponent({
  name: 'ProjectionControlTable',
})
const { projectionStatus, projection } = storeToRefs(storeLayout)
</script>
