<script setup lang="ts">
import { computed, ref } from 'vue'
import { useClipboard } from '@vueuse/core'
import { toast } from 'vue-sonner'
import type { ProsePreProps } from '@mockline/themes'
import { useComponent } from '../../utils'
import CodeIcon from './CodeIcon.vue'
import appConfig from '#build/app.config'

const props = defineProps<ProsePreProps>()

const clipboard = useClipboard()

const copied = ref(false)

function copy(): void {
  clipboard.copy(props.code || '')

  copied.value = true

  toast.success('Copied to clipboard')

  setTimeout(() => {
    copied.value = false
  }, 2000)
}

const componentProps = computed(() => {
  return {
    ...props,
    forceDark: !props.meta?.includes('light') ? appConfig.mockline.darkCode : false,
    transparent: props.meta?.includes('transparent'),
    filename: !!props.filename,
  }
})

const { getClasses } = useComponent('prosePre', componentProps)
</script>

<template>
  <div :class="getClasses('root')">
    <div
      v-if="filename && !hideHeader"
      :class="getClasses('header')"
    >
      <CodeIcon :icon :filename :class="getClasses('icon')" />

      <span :class="getClasses('filename')">{{ filename }}</span>
    </div>

    <MButton
      :icon="copied ? appConfig.mockline.icons.copyCheck : appConfig.mockline.icons.copy"
      :color="copied ? 'primary' : 'neutral'"
      variant="ghost"
      size="sm"
      aria-label="Copy code to clipboard"
      :class="getClasses('copy')"
      tabindex="-1"
      @click="copy"
    />

    <pre :class="getClasses('base', props.class)" v-bind="$attrs"><slot /></pre>
  </div>
</template>
<!--
<style>
.shiki span.line{display:block}.shiki span.line.highlight{margin:0 -16px;padding:0 16px;}
</style>-->
