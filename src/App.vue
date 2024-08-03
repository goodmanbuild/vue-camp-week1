<script setup>
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'

import { ref } from 'vue';

const source = ref([{
  id: 1,
  name: "珍珠奶茶",
  description: "香濃奶茶搭配QQ珍珠",
  price: 50,
  stock: 20
}, {
  id: 2,
  name: "冬瓜檸檬",
  description: "清新冬瓜配上新鮮檸檬",
  price: 45,
  stock: 15
}, {
  id: 3,
  name: "翡翠檸檬",
  description: "綠茶與檸檬的完美結合",
  price: 55,
  stock: 30
}, {
  id: 4,
  name: "四季春茶",
  description: "香醇四季春茶，回甘無比",
  price: 45,
  stock: 10
}, {
  id: 5,
  name: "阿薩姆奶茶",
  description: "阿薩姆紅茶搭配香醇鮮奶",
  price: 50,
  stock: 25
}, {
  id: 6,
  name: "檸檬冰茶",
  description: "檸檬與冰茶的清新組合",
  price: 45,
  stock: 20
}, {
  id: 7,
  name: "芒果綠茶",
  description: "芒果與綠茶的獨特風味",
  price: 55,
  stock: 18
}, {
  id: 8,
  name: "抹茶拿鐵",
  description: "抹茶與鮮奶的絕配",
  price: 60,
  stock: 20
}]);

const add = (item, index) => {
  item.stock++;
}

const sub = (item, index) => {
  item.stock--;
}

const tempName = ref('');
const edittingIndex = ref(-1);

const edit = (item, index) => {
  tempName.value = item.name;
  edittingIndex.value = index;
}



const cancle = (item, index) => {
  edittingIndex.value = -1;
}

const save = (item, index) => {
  edittingIndex.value = -1;
  item.name = tempName.value;
}



</script>

<template>
  <div>
    <table>
      <thead>
        <tr>
          <th scope="col" style="width:250px">品項</th>
          <th scope="col">描述</th>
          <th scope="col">價格</th>
          <th scope="col">庫存</th>
        </tr>
      </thead>
      <tbody>

        <tr v-for="(item, index) in source" :key="item.id">
          <td @dblclick="edit(item, index)">
            <span v-if="index !== edittingIndex" :data-index="index">{{ item.name }}</span>
            <div v-else>
              <input type="text" v-model="tempName" style="width:118px">
              <input type="button" value="儲存" @click="save(item, index)">
              <input type="button" value="取消" @click="cancle(item, index)">
            </div>

          </td>
          <td><small>{{ item.description }}</small></td>
          <td>{{ item.price }}</td>
          <td><button @click.prevent="sub(item, index)">-</button>{{ item.stock }}<button
              @click.prevent="add(item, index)">+</button></td>
        </tr>
      </tbody>
    </table>
  </div>
  <!-- <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main> -->
</template>

<style scoped>
th {
  border-bottom: 1px solid #000000;
}

td,
tr {
  padding: 8px 20px;
}



/* header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
} */
</style>
