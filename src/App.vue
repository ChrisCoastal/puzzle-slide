<template>
  <div
    ref="pixiContainer"
    class="pixi-container"
    @click.alt="handleClick"
    @mousedown="handleMousedown"
  />
</template>

<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue'
import * as PIXI from 'pixi.js'

const pixiContainer = ref<HTMLElement | null>(null)
let pixiApp: PIXI.Application<PIXI.ICanvas> | null = null
function handleClick() {
  console.log('click')
}
function handleMousedown() {
  console.log('mousedown')
}
onMounted(() => {
  pixiApp = new PIXI.Application({ width: 800, height: 600, background: '#1099BB' })
  // @ts-ignore
  pixiContainer.value.appendChild(pixiApp.view)
  // TODO: pixi setup
})
onBeforeUnmount(() => {
  if (pixiApp) {
    pixiApp.destroy()
    pixiApp = null
  }
})
</script>
