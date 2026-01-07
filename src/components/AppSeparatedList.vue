<template>
  <div class="flex items-center gap-1">
    <template v-for="(item, index) in items" :key="index">
      <slot name="item" :item="item">
        <span>
          {{ item }}
        </span>
      </slot>

      <slot v-if="index < items.length - 1" name="separator">
        <span>
          {{ separator }}
        </span>
      </slot>
    </template>
  </div>
</template>

<script lang="ts" setup generic="T">
withDefaults(
  defineProps<{
    items: T[]
    separator?: string
  }>(),
  {
    separator: '•'
  }
)
</script>

