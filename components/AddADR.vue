<template>

<input type="text" v-model="adrName">
<a :href="url" class="action-button primary" aria-label="Create Decision Record!">
    Create Decision Record
</a>



</template>

<script>
export default {
  name: 'addADR',
  data: function () {
    return {
      adrName: "Enter name"
    }
  },
  methods: {
    
  },
  computed: {
    url() {
        return 
    }
  }
}
</script>

<style lang="scss" scoped>
div {
  width: 100%;
  max-width: 600px;
  margin-bottom: 50px;
}
