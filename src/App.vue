<template>
  <div>
	<!--Форма списка-->
    <h1 >Список дел</h1>
    <p>Добавьте в список новые значения</p>
    <form @submit.prevent="createPost">
      <input v-model.trim="userTextInput" type="text" name="list" id="list" placeholder="Введите текст">
      <button class="btn btn-dark" id="add">Добавить дело</button>
    </form>
    <ul>
		<!--Вывод списка дел через массив-->
      <li v-for="el in tasks" :key="el.id">
       <span>{{ el.text }}</span>
        <button @click="deletePost(el.id)" class="btn btn-dark" id="delet">Удалить</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
      return {
        userTextInput: "",
        tasks: [],
      };
  },
  methods: {
	<!--Удаление дела-->
    deletePost(id) {
      this.tasks = this.tasks.filter((el) => el.id !== id);
    },
	<!--Добавление дела-->
    createPost() {
      if(this.userTextInput !== "") {
        this.tasks.push({
          id: this.tasks.length - 1,
          text: this.userTextInput
        });
		<!--Возвращение пустой формы после добавления дела-->
        this.userTextInput = "";
      }
    },
  },
};
</script>
<!--Описание CSS-->
<style>
div {
  text-align: center;
  margin-top: 50px;
}

h1 {font-weight: bold}

p{font-size: 21px}

form {
  position: relative;
  top: -10px;
}

input {
  width: 230px;
  height: 40px;
  border-radius: 5px;
  border: 1px solid #b9b9b9;
}

#add {
  position: relative;
  top: -3px;
  margin-left: 5px;
  height: 43px;
}

li {
  list-style-type: none;
  margin-top: 10px;
  margin-bottom: 10px;
}

span {font-size: 21px}

#delet {margin-left: 5px}
</style>