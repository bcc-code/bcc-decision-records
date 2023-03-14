<template>

<input type="text" class="action-input" v-model="adrName">
<a :href="url" class="action-button primary" aria-label="Create Decision Record!">
    Create
</a>


</template>

<script>
export default {
  name: 'addADR',
  data: function () {
    return {
      adrName: 'Enter Decision Name',
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
        const regex = /[^a-zA-Z0-9\\-]/ig;
        let urlName = this.adrName.replaceAll(regex,'-').toLowerCase();
        var encodedContent = encodeURIComponent(this.adrTemplate.replace('[TITLE]', name))
        return `https://github.com/bcc-code/bcc-decision-records/new/main?filename=docs/Current/${urlName}.md&value=${encodedContent}`
    }
  }
}
</script>

<style lang="scss" scoped>

.action-button {
    display: inline-block;
    font-size: 1.2rem;
    padding: .8rem 1.6rem;
    border-width: 2px;
    border-style: solid;
    border-radius: 4px;
    transition: background-color var(--t-color);
    box-sizing: border-box
}

.action-input {
    display: inline-block;
    font-size: 1.2rem;
    padding: .8rem 1.6rem;
    margin-right: 0;
    border-width: 2px;
    border-style: solid;
    border-radius: 4px;
    transition: background-color var(--t-color);
    box-sizing: border-box
}


.action-button.primary {
    color: var(--c-bg);
    background-color: var(--c-brand);
    border-color: var(--c-brand)
}

.action-button.primary:hover {
    background-color: var(--c-brand-light)
}

.action-button.secondary {
    color: var(--c-brand);
    background-color: var(--c-bg);
    border-color: var(--c-brand)
}

.action-button.secondary:hover {
    color: var(--c-bg);
    background-color: var(--c-brand-light)
}
</style>