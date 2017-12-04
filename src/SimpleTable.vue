<template>
  <div>
    <table class="table table-bordered table-hover table-striped">
      <thead>
      <tr>
        <th v-for="header in headers">{{ header }}</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="itens in list">
        <td v-for="item in itens">{{ item }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
  export default {
    name: 'SimpleTable',
    props: ['headers', 'list']
  }
</script>
