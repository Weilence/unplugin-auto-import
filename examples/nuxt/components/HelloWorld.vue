<script setup lang="ts">
const props = withDefaults(defineProps<{ msg: string; name: string | number }>(), { msg: 'Hello' })
const emit = defineEmits(['update'])

const count = ref(0)
const doubled = computed(() => count.value * 2)

function inc() {
  count.value += 1
}

function dec() {
  count.value += 1
}

const decText = '<b>Dec</b>'

watch(count, value => emit('update', value))
</script>

<script lang="ts">
export default {
  name: 'App',
}
</script>

<template>
  <div>
    <h3>{{ msg }}, {{ name }}</h3>
    <button @click="inc">
      Inc
    </button>
    <div>{{ count }} x 2 = {{ doubled }}</div>
    <button @click="dec()" v-html="decText" />
  </div>
</template>
