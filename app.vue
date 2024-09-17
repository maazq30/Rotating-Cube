<template>
  <TresCanvas window-size clear-color="#82dbc5">
    <TresMesh :rotation="[Math.PI / 4, Math.PI / 6, Math.PI / 6]" ref="boxref">
      <TresBoxGeometry />
      <TresMeshNormalMaterial />
    </TresMesh>
  </TresCanvas>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRenderLoop } from '@tresjs/core'


const boxref = ref(null)


const { onLoop } = useRenderLoop()

onMounted(() => {
 
  onLoop(({ delta, elapsed }) => {
    if (boxref.value) {
      
      boxref.value.rotation.y += delta
      boxref.value.rotation.z = elapsed * 0.2
    }
  })
})
</script>
