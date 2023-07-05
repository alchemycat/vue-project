<script>
import Select from "./Select.vue";
    let itemID = 0;
    export default {
        data() {
            return {
                items: [],
                name: "",
                price: 0,
                percent: 0,
                count: 0,
                currency: 'Dollar',
            }
        },
        props: {
          modalActive: Boolean
        },
        methods: {
            addItem() {
                this.items.push({name: this.name, price: this.price, percent: this.percent, count: this.count, id: itemID++});
                this.$emit('items', this.items);
            },
            closeModal() {
              this.$emit('modalActive', !this.modalActive);
            }
        },
        emits: ['items', 'modalActive'],
        components: {
            Select
        }
    }
</script>

<template>
     <form action="#" class="form" @submit.prevent>
    <button class="btn__close" @click="closeModal">&times;</button>
    <div class="form__wrapper text-sm">
      <div class="form__field">
        <label>
          Название
        </label>
        <input v-model="name" class="border-solid border-2 border-gray-300	 rounded-md" type="text" name="name">
      </div>

      <div class="form__field">
        <label>
          Цена товара
        </label>
        <input v-model="price" class="border-solid border-2 border-gray-300	 rounded-md" type="text" name="price">
      </div>

      <div class="form__field">
        <label>
         Наценка в процентах
        </label>
        <input v-model="percent" class="border-solid border-2 border-gray-300	 rounded-md" type="text" name="percent">
      </div>

      <div class="form__field">
        <label>
          Количество
        </label>
        <input v-model="count" class="border-solid border-2 border-gray-300	 rounded-md" type="text" name="count">
      </div>

      <div class="form__field">
        <Select @select="(selected) => currency = selected.value.name"></Select>
      </div>
    </div>
    
    <button @click="addItem" class="mt-3 bg-indigo-500/100 hover:bg-indigo-500/75 text-white border-0">Добавить заказ</button>

  </form>
</template>

<style scoped>
    .form {
      position:relative;
      padding: 20px;
    }
    .btn__close {
      position: absolute;
      right: 20px;
      top: -10px;
      padding: 10px;
      border-radius: 50%;
      font-size: 20px;
      line-height: 20px;
      background-color: transparent;
      outline: none;
      border: none;
    }
    .btn__close:hover {
      outline: none;
      border: none;
      
    }
    .form__wrapper {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    gap: 10px 0px;
    }
    .form__field {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    }
    .form__field input {
    width: 100%;
    padding: 3px 5px;
    }
</style>