<script>
import Vue from 'vue'

// Đoạn code này là một component Vue có tên là "Table"
// Chứa 2 thuộc tính là headers và data
export default Vue.extend({
  name: 'Table',
  props: {
    headers: {
      type: Array,
      required: true,
    },
    data: {
      type: Array,
      required: true,
    }
  }
})
</script>

<!-- Đoạn này là một cái bảng -->
<template>
  <div>
    <table>
      <tr>
        <th 
          v-for="(header, i) in headers"
          :key="`${header}${i}`"
          class="header-item"
        >
          {{ header }}
        </th>
      </tr>
      <tr
        v-for="entity in data"
        :key="`entity-${entity.name}`"
        class="table-rows"
      >
        <td
          v-for="(header, i) in headers"
          :key="`${header}${i}`"
        >
        <slot :name="`column${i}`" :entity="entity"></slot>
      </td>
      </tr>
    </table>
  </div>
</template>

