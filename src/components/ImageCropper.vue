<template>
  <div class="cropper-container">
    <vue-cropper
      ref="cropperRef"
      :src="imageUrl"
      :aspect-ratio="1"
      :view-mode="2"
      :auto-crop-area="0.8"
      :background="true"
      :movable="true"
      :zoomable="true"
      :center="true"
    />
    <q-btn color="primary" @click="getCropData">Crop Image</q-btn>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import VueCropper from 'vue-cropper'
import 'vue-cropper/dist/index.css'

const cropperRef = ref()
const imageUrl = ref('https://placeholder.com/300x300')

const getCropData = () => {
  const cropper = cropperRef.value
  if (cropper) {
    const canvas = cropper.getCroppedCanvas()
    if (canvas) {
      const croppedImage = canvas.toDataURL()
      console.log('Cropped image:', croppedImage)
    }
  }
}
</script>

<style lang="scss" scoped>
.cropper-container {
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
}
</style>