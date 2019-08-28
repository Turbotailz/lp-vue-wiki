<template>
  <div class="wiki">
    <aside>
      <sidebar />
    </aside>
    <article>
      <component :is="html"></component>
    </article>
  </div>
</template>

<script>
  export default {
    components: {
      'sidebar': resolve => require(['@/wiki/_Sidebar.md'], resolve),
    },
    data() {
      return {
        html: null,
      }
    },
    created() {
      const page = this.$route.params.page;
      this.html = require('@/wiki/'+page+'.md').default;
    },
    mounted() {
      document.addEventListener('click', event => {
        event.preventDefault();
        console.log(event);
      })
    }
  }
</script>

<style lang="scss">
  .wiki {
    display: flex;
    align-items: flex-start;
  }

  aside {
    flex: 0 0 16em;
    position: sticky;
    top: 0;
    background: #EEE;
    padding: 2em;
  }

  article {
    padding: 2em;
    max-width: 800px;
  }
</style>