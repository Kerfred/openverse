<template>
  <div
    role="alert"
    :class="[
      $style.snackbar,
      $style[size],
      isVisible
        ? 'translate-y-0 opacity-100'
        : 'translate-y-[4rem] opacity-0 motion-reduce:translate-y-0',
    ]"
  >
    <!-- @slot Your message or subcomponent goes passed here. -->
    <slot />
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue"

export default defineComponent({
  name: "VSnackbar",
  props: {
    size: {
      type: String as PropType<"small" | "large">,
      default: "small",
    },
    /**
     * whether the snackbar is visible or hidden
     */
    isVisible: {
      type: Boolean,
      default: true,
    },
  },
})
</script>

<style module>
.snackbar {
  box-shadow: 0px 2px 6px rgba(0, 0, 0, 0.3);
  @apply fixed bottom-4 z-snackbar rounded-sm bg-black text-white transition-[opacity,transform] duration-500 ltr:left-4 rtl:right-4 motion-reduce:transition-opacity;
}

.large {
  @apply w-max max-w-[calc(100%_-_2_*_theme(spacing.4))] flex-row items-center px-6 py-4 text-sm;
}

.small {
  @apply w-2/3 flex-col items-start px-4 py-3 text-sr sm:w-2/5;
}
</style>
