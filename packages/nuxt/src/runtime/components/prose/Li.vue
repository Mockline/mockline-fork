<script setup lang="ts">
import type { ProseLiProps } from '@mockline/themes'
import { useComponent } from '../../utils'

const props = defineProps<ProseLiProps>()

const { getClasses } = useComponent('proseLi')
</script>

<template>
  <li :class="getClasses('default', props.class)">
    <slot />
  </li>
</template>
