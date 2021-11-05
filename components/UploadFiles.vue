<template>
  <div class="flex flex-col mt-4 w-full space-y-16 p-8">
    <div>
      <h1 class="font-medium text-xl mb-2">
        Ajouter des photos au véhicule
      </h1>
      <InputFile @change-file-list="uploadFiles($event)" />
    </div>
    <div class="flex flex-row flex-wrap gap-x-4 gap-y-4">
      <Vignette v-for="(file, index) in files" :key="index" :file="file" @remove-vignette="remove(file)" />
    </div>
  </div>
</template>

<script>
import InputFile from './InputFile.vue'
import Vignette from './Vignette.vue'

export default {
  components: { InputFile, Vignette },
  data () {
    return {
      files: []
    }
  },
  methods: {
    uploadFiles (value) {
      this.files = [...this.files, ...value]
    },
    getPreview (file) {
      return URL.createObjectURL(file)
    },
    remove (file) {
      const index = this.files.indexOf(file)
      if (index !== -1) {
        this.files.splice(index, 1)
      }
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
