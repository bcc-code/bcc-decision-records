<template>

<input type="text" v-model="adrName">
<a :href="url" class="action-button primary" aria-label="Create Decision Record!">
    Create
</a>


</template>

<script>
export default {
  name: 'addADR',
  data: function () {
    return {
      adrName: 'Enter name',
      adrTemplate: 
` 
# [TITLE]

## Test

### Test2
      
`
    }
  },
  methods: {
    
  },
  computed: {
    url() {
        let name = this.adrName;
        const regex = /[a-zA-Z0-9\\-]/ig;
        let urlName = this.adrName.replaceAll(regex,'-').toLowerCase();
        var encodedContent = encodeURIComponent(this.adrTemplate.replace('[TITLE]', name))
        return `https://github.com/bcc-code/bcc-decision-records/new/main?filename=docs/Current/${urlName}.md&value=${encodedContent}`
    }
  }
}
</script>

<style lang="scss" scoped>

</style>