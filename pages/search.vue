<template>
  <v-form v-model="valid">
    <v-text-field
      v-model="member"
      :rules="memberRules"
      label="กรอกข้อมูล"
      required
     ></v-text-field>
     <v-btn color="primary" dark @click="Dosearch">ค้นหา
        <v-icon dark right>label</v-icon>
      </v-btn>
      <v-btn color="success" dark @click="Dosave">ล้างข้อมูล
        <v-icon dark right>label</v-icon>
      </v-btn>
      <div>
  <v-data-table
    :headers="headers"
    :items="desserts"
    class="elevation-1"
  >
    <template slot="items" slot-scope="props">
      <td>{{ props.item.c_id }}</td>
      <td class="text-xs-lelt">{{ props.item.c_name }}</td>
      <td class="text-xs-lelt">{{ props.item.c_number }}</td>
      <td class="text-xs-lelt">{{ props.item.c_price }}</td>
      
    </template>
    
    <template slot="pageText" slot-scope="props">
      Lignes {{ props.pageStart }} - {{ props.pageStop }} de {{ props.itemsLength }}
    
    </template>
  </v-data-table>
   <div>
    <v-btn color="success">เพิ่ม</v-btn>
    <v-btn color="warning">แก้ไข</v-btn>
    <v-btn color="error">ลบ</v-btn>
    </div>
  </div>
  </v-form>
</template>

<script>
export default {
  data () {
  return {
      headers: [
        {
          text: "C_ID",
          align: "left",
          sortable: false,
          value: "name"
        },
        { text: "C_Name ", value: "C_Name" },
        { text: "C_Number ", value: "C_Number" },
        { text: "C_Price ", value: "C_Price" }
      ],
      desserts: [],
      member :'',
    };
  },
  async created() {
   this.getstudent()     
  },
  methods: {
    async Dosearch() {
      console.log(this.member);
      let res = await this.$http.post("http://127.0.0.1/php-test/search.php?name="+this.member)
        this.desserts = res.data.admin
    },
    async getstudent() {
      let res = await this.$http.get('http://127.0.0.1/php-test/list-student.php')
      this.desserts = res.data.student
    },
    async Dosave() {
      let res = await this.$http.get('http://127.0.0.1/php-test/list-student.php')
      this.member ='',
      this.getstudent() 
    },
  }
  
}

</script>
