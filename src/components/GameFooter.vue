<template>
  <footer>
    <p>boreal games</p>
    <template v-for="l in licences" :key="l.component">
      <p><a :href="l.url">{{l.component}} by {{l.author}}</a></p>
    </template>
  </footer>
</template>

<script>
export default {
  props: {
    licences: {
      type: Array,
      required: true
    }
  }
}
</script>
