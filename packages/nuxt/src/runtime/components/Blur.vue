<script setup lang="ts">
const { position = 'top', size = 75 } = defineProps<{
  position: 'top' | 'bottom' | 'both'
  size?: number
}>()

const blurLevels = [1, 2, 3, 6, 12]

const positions = {
  top: {
    class: 'top-0',
    gradient: 'gradient-mask-b-0'
  },
  bottom: {
    class: 'bottom-0',
    gradient: 'gradient-mask-t-0'
  }
}
</script>

<template>
  <div>
    <template v-for="pos in ['top', 'bottom']" :key="pos">
      <div
        v-if="position === pos || position === 'both'"
        :class="`fixed w-full ${positions[pos].class} h-24`"
        :style="{ height: `${size}px` }"
      >
        <div
          v-for="blur in blurLevels"
          :key="blur"
          :style="{
            '-webkit-backdrop-filter': `blur(${blur}px)`,
            'backdrop-filter': `blur(${blur}px)`
          }"
          :class="[
            'absolute inset-0',
            positions[pos].gradient,
            `blur-[${blur}px]`
          ]"
        />
      </div>
    </template>
  </div>
</template>

<style scoped>
.gradient-mask-b-0 {
  mask-image: linear-gradient(to bottom, rgba(0, 0, 0, 1) 0%, transparent 100%);
}
.gradient-mask-t-0 {
  mask-image: linear-gradient(to top, rgba(0, 0, 0, 1) 0%, transparent 100%);
}
</style>
