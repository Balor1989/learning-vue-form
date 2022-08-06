<template>
  <div class="container">
    <form class="card" @submit.prevent="submitHandler">
      <h1>Анкета на Vue разработчика!</h1>
      <AppInput
        label="Как тебя зовут?"
        placeholder="Введите имя"
        :error="error.name"
        v-model="name"
      />

      <div class="form-control">
        <label for="age">Выбери возраст</label>
        <input v-model.number="age" type="number" id="age" min="18" max="99" />
      </div>

      <div class="form-control">
        <label for="city">Твой город</label>
        <select id="city" v-model="city">
          <option value="spb">Санкт-Петербург</option>
          <option value="msk">Москва</option>
          <option value="kzn">Казань</option>
          <option value="nsk">Новосибирск</option>
        </select>
      </div>

      <div class="form-checkbox">
        <span class="label">Готов к переезду в Токио?</span>
        <div class="checkbox">
          <label
            ><input type="radio" name="trip" v-model="relocate" value="yes" />
            Да</label
          >
        </div>

        <div class="checkbox">
          <label
            ><input type="radio" name="trip" v-model="relocate" value="no" />
            Нет</label
          >
        </div>
      </div>

      <div class="form-checkbox">
        <span class="label">Что знаешь во Vue?</span>
        <div class="checkbox">
          <label
            ><input
              type="checkbox"
              v-model="skills"
              name="skills"
              value="Vuex"
            />
            Vuex</label
          >
        </div>
        <div class="checkbox">
          <label
            ><input
              type="checkbox"
              v-model="skills"
              name="skills"
              value="Vue CLI"
            />
            Vue CLI</label
          >
        </div>
        <div class="checkbox">
          <label
            ><input
              type="checkbox"
              v-model="skills"
              name="skills"
              value="Vue Router"
            />
            Vue Router</label
          >
        </div>
      </div>

      <button type="submit" class="btn primary">Отправить</button>
    </form>
  </div>
</template>

<script>
import AppInput from './components/AppInput';
export default {
  data() {
    return {
      name: '',
      age: '33',
      city: 'spb',
      relocate: 'no',
      skills: [],
      error: {
        name: null,
      },
    };
  },
  methods: {
    isFormValid() {
      let valid = true;
      if (this.name.length === 0) {
        this.error.name = 'Поле не может быть пустым';
        valid = false;
      } else {
        this.error.name = null;
      }

      return valid;
    },

    submitHandler() {
      if (this.isFormValid()) {
        console.group('Form data');
        console.log('Name:', this.name);
        console.log('Age:', this.age);
        console.log('City:', this.city);
        console.log('Relocate:', this.relocate);
        console.log('Skills:', this.skills);
        console.groupEnd();
      }
    },
  },
  components: { AppInput },
};
</script>

<style>
.error-name {
  color: rgb(230, 20, 20);
}
.invalid {
  border-color: rgb(230, 20, 20) !important;
}
</style>
