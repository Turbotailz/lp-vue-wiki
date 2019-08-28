<template>
  <div class="wiki">
    <h1>Wiki</h1>
    <component :is="html"></component>
  </div>
</template>

<script>
  export default {
    components: {
      // 'wiki-page': resolve => require(['@/wiki/' + this.$route.params.page + '.md'], resolve),
    },
    data() {
      return {
        html: null,
      }
    },
    created() {
      const page = this.$route.params.page;
      this.html = require('@/wiki/'+page+'.md').default;
    }
  }
</script>