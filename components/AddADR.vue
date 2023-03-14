<template>

<div style="text-align: center; margin-right: auto; margin-left: auto;">
  <input type="text" @focus="$event.target.select()" class="action-input" v-model="adrName">
  <button @click="createADR" class="action-button primary" aria-label="Create Decision Record!">
      Create
  </button>
</div>

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

---
**Instructions**
1. [] Fill in description
2. [] Commit file to a *new* branch
3. [] Create a pull-request and add stakeholders as reviewers
4. [] Merge pull-request once a decision has been made
---

**Status**: [Assess|Trial|Adopt|Hold]

## Description
[TODO: Description of decision to be made]

### Context
[TODO: Scope and context decision applies to]

### Background
[TODO: Reason for wanting a decision]

## Alternatives
[TODO: Description and analysis of alternatives]

### Summary
| #      | Title                                   | Security         | Delivery     | Sustainability |    
| ------ | --------------------------------------- | ------------     | ----------   | ----------     |   
| 1      |                                         | ✅              |              |                |                          
| 2      |                                         | ❌              |              |                |     
| 3      |                                         | ✅              |              |                |     

### Alt 1: [Title]
[Description]

**Risks**  

**Benefits**  


### Alt 2: [Title]
[Description]

**Risks**  

**Benefits**  



### Alt 3: [Title]
[Description]

**Risks**  

**Benefits**  


## Assessment
[TODO: Preliminary assessment based on assessment criteria]


## Trial
[TODO: Document experience after trialing]


## Decision
[TODO: Document final decision and update tech radar]
      
`
    }
  },
  methods: {
    createADR() {
      window.open(this.url, '_blank');
    }
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
    box-sizing: border-box;
    border-top-left-radius: 0;
    border-bottom-left-radius: 0;
}

.action-input {
    display: inline-block;
    font-size: 1.2rem;
    padding: .8rem 1.6rem;
    margin-right: 0;
    border-width: 2px;
    border-style: solid;
    border-radius: 4px;
    border-top-right-radius: 0;
    border-bottom-right-radius: 0;
    transition: background-color var(--t-color);
    box-sizing: border-box;
    border-right: 0;
}


.action-button.primary {
    color: var(--c-bg);
    background-color: var(--c-brand);
    border-color: var(--c-brand);
}

.action-button.primary:hover {
    background-color: var(--c-brand-light);
    text-decoration: none;
}

.action-button.secondary {
    color: var(--c-brand);
    background-color: var(--c-bg);
    border-color: var(--c-brand)
}

.action-button.secondary:hover {
    color: var(--c-bg);
    background-color: var(--c-brand-light);
}
</style>