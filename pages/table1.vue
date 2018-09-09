<template>
<div>
  <v-data-table
    :headers="headers"
    :items="desserts"
    class="elevation-1"
  >
    <template slot="items" slot-scope="props">
      <td>{{ props.item.c_id }}</td>
      <td class="text-xs-center">{{ props.item.c_name }}</td>
      <td class="text-xs-center">{{ props.item.c_number }}</td>
      <td class="text-xs-center">{{ props.item.c_price }}</td>
      
    </template>
    <template slot="pageText" slot-scope="props">
    Lignes {{ props.pageStart }} - {{ props.pageStop }} de {{ props.itemsLength }}
    </template>
  </v-data-table>
  <div>
    <v-btn color="brown lighten-1">แก้ไขข้อมูล</v-btn>
    <v-btn color="brown lighten-1">เพิ่มข้อมูล</v-btn>
  </div>
  </div>
</template>
<script>
  export default {
    data () {
      return {
        headers: [
          {
            text: 'C_ID',
            align: 'left',
            sortable: false,
            value: 'name'
          },
          { text: 'C_Name', value: 'C_Name', align: 'center' },
          { text: 'C_Number', value: 'C_Number', align: 'center' },
          { text: 'C_Price', value: 'C_Price', align: 'center' },
        ],
        desserts: [],
      }
    },
    async created() {
    this.getstudent()
  }, 
methods: {
    async getstudent() {
      let res = await this.$http.get('http://127.0.0.1/php-test/list-student.php')
      this.desserts = res.data.student
    },
},
  }
</script>
