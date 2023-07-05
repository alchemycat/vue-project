<script>
  import Modal from "./components/Modal.vue";
  export default {
    data() {
      return {
        items: [
          {name: "item", price: 1000, percent: 10, count: 1},
          {name: "item", price: 1000, percent: 10, count: 1},
          {name: "item", price: 1000, percent: 10, count: 1},
          {name: "item", price: 1000, percent: 10, count: 1},
          {name: "item", price: 1000, percent: 10, count: 1},
          {name: "item", price: 1000, percent: 10, count: 1},
          {name: "item", price: 1000, percent: 10, count: 1},
        ],
        modalActive: false,
        modalClass: "hide"
      }
    },
    methods: {
      toggleModal() {
        this.modalActive = !this.modalActive;
      }
    },
    computed: {
      changeModalClass() {
        if (this.modalActive) {
          this.modalClass = "";
        } else {
          this.modalClass = "hide";
        }
        return this.modalClass;
      }
    },
    components: {
      Modal
    }
  }
</script>

<template>
  <h1 class="text-2xl font-bold">
    Список заказов
  </h1>

  <p v-if="!items.length" class="font-medium underline mt-3">Пока нету заказов</p>

  <ul class="divide-y divide-gray-100 text-sm pt-1">
    <li v-for="item of items" :key="item.id">
      <div >
        <span>
          <span class="font-medium">Название:</span>&nbsp;<span>{{ item.name }}</span>
        </span>
        &nbsp;
        <span>
          <span class="font-medium">Цена:</span>&nbsp;<span class="text-green-500">${{ item.price }}</span>
        </span>
      </div>
    </li>
  </ul>
  <button class="mt-3 bg-indigo-500/100 hover:bg-indigo-500/75 text-white border-0 btn__modal" @click="toggleModal">Создать заказ</button>

  <Modal @modalActive="(msg) => modalActive = msg" :modalActive="modalActive" :class="changeModalClass"></Modal>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
.hide {
    display: none;
}
</style>
