<template>
  <footer>
    <template v-for="l in licences" :key="l.component">
      <p><a :href="l.url">{{l.component}} por {{l.author}}</a></p>
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
