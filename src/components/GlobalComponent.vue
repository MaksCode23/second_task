<script>
import Products from "@/components/Products.vue";
import Time from "@/components/Time.vue";
import Form from "@/components/Form.vue";
import Events from "@/components/Events.vue"
import Table from "@/components/Table.vue";
import ObjectList from "@/components/ObjectList.vue";
import Pagination from "@/components/Pagination.vue";
export default {
  name: "GlobalComponent",
  components: {
    Products,
    Time,
    Form,
    Events,
    Table,
    ObjectList,
    Pagination,

  },
  data(){
    return {
      selectedComponent: 1,
      options: [{ text: "Час кліку", value: 1},
                { text: "Форма", value: 2},
                { text: "Події", value: 3},
                { text: "Рандомний колір та размір шрифту списку елементів",  value: 4},
                { text: "Таблиця", value: 5},
                { text: "Список об'єктів та фільтрація", value: 6},
                { text: "Пагінація", value: 7}
      ],
    }
    },
  methods:{

  },

}
</script>

<template>
  <div class="width">
 <v-select class="select" v-model="selectedComponent" :items="options" item-title="text" label="Виберіть компонент"/>
    <Time v-if="selectedComponent === 1"/>
    <Form v-if="selectedComponent===2"/>
    <Events v-if="selectedComponent===3"/>
    <Products v-if="selectedComponent===4"/>
    <Table v-if="selectedComponent===5"/>
    <Object-List v-if="selectedComponent===6"/>
    <Pagination v-if="selectedComponent===7"/>
  </div>

</template>


<style scoped>
.width{
padding: 2rem;
  text-align: center;
}
.width .select{
  max-width: 400px;
  margin: 0 auto;
}
</style>