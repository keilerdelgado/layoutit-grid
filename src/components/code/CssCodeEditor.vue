<template>
  <CodeEditor type="css" :get-code="getCode"
    ><CssCodeArea :area="area" :options="options" /><template v-if="options.oldSpec"
      >{{ '\n\n@media all and (-ms-high-contrast:none) {\n\n' }}<CssCodeAreaOldSpec :area="area" :options="options" />{{
        '\n\n}'
      }}</template
    ></CodeEditor
  >
</template>

<script setup>
import { defineProps } from 'vue'
import { areaToCSS } from '../../generateCode.js'

const props = defineProps({
  area: { type: Object, default: null },
  options: { type: Object, default: null },
})

function getCode() {
  return areaToCSS(props.area, props.options)
}
</script>

<style scoped>
::v-deep(.token.punctuation) {
  color: var(--color-gray-light);
}

::v-deep(.token.string) {
  color: var(--color-orange);
}

::v-deep(.token.property) {
  color: var(--color-blue-lightest);
}

::v-deep(.token.selector) {
  color: var(--color-golden);
}

::v-deep(.token.tag) {
  color: var(--color-blue-light);
}

::v-deep(.token.attr-name) {
  color: var(--color-blue-lightest);
}

::v-deep(.token.attr-value) {
  color: var(--color-orange);
}
</style>
