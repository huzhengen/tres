<!-- eslint-disable no-console -->
<script setup lang="ts">
import { useFBO } from '../composables/useFBO'

const fboTarget = useFBO({
  depth: true,
  width: 512,
  height: 512,
  settings: {
    samples: 1,
  },
})

watchEffect(() => {
  console.log('Target', fboTarget.value)
})
</script>

<template>
  <TresMesh>
    <TresBoxGeometry :args="[1, 1, 1]" />
    <TresMeshBasicMaterial
      :color="0xFF8833"
      :map="fboTarget.texture ?? null"
    />
  </TresMesh>
</template>
