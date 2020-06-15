<!--Диалоговое окно формы ввода/корректировки записей-->
<template>
  <div class="modal is-active">
    <div class="modal-background">
      <div class="modal-box">
        <div class="modal-content">
          <button class="modal-close-btn"
                  @click.prevent="dialogClose">
            <img src="../assets/icons/png/close.png"
                 alt="Закрыть">
          </button>
          <form action="#"
                @submit.prevent>
            <div class="field">
              <label class="field__lbl">Буквенный код валюты</label>
              <input type="text"
                     class="field__txt"
                     v-model.trim="item.Cur_Abbreviation"
                     placeholder=""
              >
            </div>
            <div class="field">
              <label class="field__lbl">Наименование валюты</label>
              <input type="text"
                     class="field__txt"
                     v-model.trim="item.Cur_Name"
                     placeholder=""
              >
            </div><div class="field">
              <label class="field__lbl">Количество единиц валюты</label>
              <input type="text"
                     class="field__txt"
                     v-model.number="item.Cur_Scale"
                     placeholder=""
              >
            </div><div class="field">
              <label class="field__lbl">Курс к бел. рублю</label>
              <input type="text"
                     class="field__txt"
                     v-model.number="item.Cur_OfficialRate"
                     placeholder="0.0000"
              >
            </div>
            <div class="buttons-modal">
              <button type="submit"
                      class="btn btn-btn btn-modal"
                      value="Сохранить"
                      @click.prevent="dialogSave">
                Сохранить</button>
              <button type="reset"
                      class="btn btn-btn btn-modal"
                      value="Отмена"
                      @click.prevent="dialogCancel">
                Отмена
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "FormItem",
    props: ['item'],
    data() {
      return {
        isValid: true,
        isNewItem: false
      }
    },
    mounted() {
      document.querySelector(".field__txt").focus();
    },
    methods: {
      dialogSave() {
        this.$emit('dialog-save', this.item);
      }
      ,
      dialogCancel() {
        this.$emit('dialog-cancel');
      }
      ,
      dialogClose() {
        this.$emit('dialog-close');
      }
    }
  }
</script>

<style scoped lang="scss">
  @import "../styles/formItem";
</style>
