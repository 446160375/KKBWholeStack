<template>
  <div>
    <span @click="cli">点我</span>
  </div>
</template>

<script>
export default {
  methods: {
    cli() {
        this.$emit('childBtn');
    },
  },
};
</script>