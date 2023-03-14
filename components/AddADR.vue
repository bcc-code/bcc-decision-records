<template>

<input type="text" v-model="adrName">
<a :href="url" class="action-button primary" aria-label="Create Decision Record!">
    Create Decision Record
</a>

<textarea ref="adrTemplate">
# [TITLE]

### Test

### Test2

</textarea>


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
    adrTemplate() {
      
      console.log(this.$refs.adrTemplate);
      return this.$refs.adrTemplate ? this.$refs.adrTemplate.value : "[TITLE]";
    },
    url() {
        let name = this.adrName;
        let urlName = this.adrName.replace(' ','-').toLowerCase();
        var encodedContent = encodeURIComponent(this.adrTemplate.replace('[TITLE]', name))
        return `https://github.com/bcc-code/bcc-decision-records/new/main?filename=docs/Current/${urlName}.md&value=${encodedContent}`
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
textarea {

}
</style>