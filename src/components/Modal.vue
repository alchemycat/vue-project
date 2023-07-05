<script>
    import Form from "./Form.vue";
    export default {
        props: {
            modalActive: Boolean
        },
        watch: {
            modalActive() {
                this.$emit('modalActive', this.modalActive);
            }
        },
        emits: ['modalActive'],
        components: {
            Form
        }
    }
</script>

<template>
    <div class="modal">
        <Form @modalActive="(msg) => modalActive = msg" :modalActive="modalActive"></Form>
    </div>
</template>
<!-- @items="elems => items = elems" -->
<style scoped>
    .modal {
        background-color: #fff;
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 500px;
        height: 500px;
        border-radius: 10px;
        box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
        padding: 20px;
        z-index: 10;

    }
</style>