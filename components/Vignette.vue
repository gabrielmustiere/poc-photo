<template>
  <div>
    <div class="relative">
      <div class="absolute font-bold top-0 right-0 h-6 w-6 bg-green-300 border-l border-b border-green-500 z-50 cursor-pointer opacity-70" @click="remove()">
        <div class="flex justify-center -mt-1">
          <span class="mr-0">x</span>
        </div>
      </div>
      <div class="absolute w-full h-full hover:bg-green-500 opacity-20" />
      <img :src="getPreview(file)" alt="" class="border border-green-500 border-opacity-25 z-30" data-class="image">
    </div>
    <span class="text-xs font-light">{{ size }}</span>
  </div>
</template>
<script>
export default {
  name: 'Vignette',
  // eslint-disable-next-line vue/require-prop-types
  props: ['file'],
  computed: {
    size () {
      return (Math.round((this.file.size / 1024) * 100) / 100) + 'kb'
    }
  },
  methods: {
    getPreview (file) {
      console.log(file)
      return URL.createObjectURL(file)
    },
    remove () {
      this.$emit('remove-vignette', this.file)
    }
  }
}
</script>

<style scoped lang="scss">
img {
  @apply h-40 w-40 object-cover;
&:hover {
   background-color: rgba(167,243,208,0.2);
 }
}
.close {
  position: absolute;
  right: 32px;
  top: 32px;
  width: 32px;
  height: 32px;
  opacity: 0.3;
}
.close:hover {
  opacity: 1;
}
.close:before, .close:after {
  position: absolute;
  left: 15px;
  content: ' ';
  height: 33px;
  width: 2px;
  background-color: #333;
}
.close:before {
  transform: rotate(45deg);
}
.close:after {
  transform: rotate(-45deg);
}
</style>
