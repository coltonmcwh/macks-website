<template>
  <div ref="embedContainer" v-html="embedCode"></div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const embedContainer = ref(null)

const embedCode = `
  <blockquote class="instagram-media"
    data-instgrm-captioned
    data-instgrm-permalink="https://www.instagram.com/p/DSuu39nE1BJ"
    data-instgrm-version="14"
    style="max-width:540px; width:100%;">
  </blockquote>
`

onMounted(() => {
  // If Instagram's script is already loaded, re-process embeds
  if (window.instgrm) {
    window.instgrm.Embeds.process()
  } else {
    const script = document.createElement('script')
    script.src = '//www.instagram.com/embed.js'
    script.async = true
    document.body.appendChild(script)
  }
})
</script>