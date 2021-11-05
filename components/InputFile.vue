<template>
  <div class="relative w-64 flex justify-center items-center rounded bg-green-500 border border-green-600 hover:bg-green-600 hover:border-green-700">
    <div class="absolute">
      <div class="flex flex-col items-center">
        <span class="block font-normal">Selectionner des photos</span>
      </div>
    </div>
    <input
      id="multiples"
      type="file"
      class="opacity-0"
      multiple
      name="multiples"
      @change="uploadFiles($event)"
    >
  </div>
</template>
<script>
export default {
  name: 'InputFile',
  props: {
    label: {
      type: String,
      default () {
        return ''
      }
    },
    propsFiles: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      files: []
    }
  },
  methods: {
    uploadFiles (event) {
      this.files = Array.from(event.target.files)
      this.$emit('change-file-list', this.files)
    }
  }
}
</script>
<style lang="scss" scoped>
input {
  @apply bg-green-200 py-2 px-4 rounded cursor-pointer
}

</style>
