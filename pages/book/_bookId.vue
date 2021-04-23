<template>
  <BookDetailsTemplate />
</template>

<script lang="ts">
import Vue from 'vue'
import { books } from '@/store'

export default Vue.extend({
  layout: 'ibook',
  async asyncData({ params }) {
    if (params.bookId) await books.show({ id: params.bookId as any })
  },
  head() {
    return {
      title: books.$single.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: books.$single.description,
        },
      ],
    }
  },
})
</script>
