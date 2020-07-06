<template>
  <fd-table :headers="['name', 'description', 'rating']" :items="products">
    <template #row="{ item }">
      <fd-table-row>
        <template #name>
          <fd-table-cell>{{ item.name }}</fd-table-cell>
        </template>
        <template #description>
          <fd-table-cell>{{ item.description }}</fd-table-cell>
        </template>
        <template #rating>
          <fd-table-cell>{{ item.rating }}</fd-table-cell>
        </template>
      </fd-table-row>
    </template>
  </fd-table>
</template>

<script>
export default {
  name: "ProductTable",
  props:  ['products']
};
</script>

<style scoped>
</style>
