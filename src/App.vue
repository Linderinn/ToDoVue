<template>
  <div class="container">
   <div class="form">
    <h1>Moja lista zadań</h1>
    <input v-model="newTask" placeholder="Dodaj nowe zadanie" />
    <button class="add-btn" @click="addTask">Dodaj</button>
    <ul>
      <li v-for="task in tasks" :key="task.id">
        <div class="img">
          {{ task.title }}
           <img src="./assets/images/pngok.png" alt="Przycisk" @click="clearTask">
        </div>
      </li>
      
    </ul>
    <button class="delete-btn" @click="clearTask">Usuń wszystkie zadania</button>
   </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [],
      newTask: '',
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== '') {
        const newTask = {
          id: Date.now(),
          title: this.newTask.trim(),
        };
        this.tasks.push(newTask);
        this.newTask = '';
      }
    },
    clearTask(index) {
  this.tasks.splice(index, 1);
},
    clearTasks() {
      this.tasks = [];
    },
  },
};
</script>
  
  <style>
body {
  font-family: Arial, sans-serif;
  background-color: #f8f8f8;
}

.container {
  display: flex;
  justify-content: center;
  max-width: 400px;
  margin: 20px auto;
  padding: 20px;
  background-color: #fff;
  border-radius: 5px;
  box-shadow: 1px 5px 10px rgba(0, 0.1, 0.1, 0.1);

}

h1 {
  
  font-weight:bold;
  font-size: 24px;
  color: #333;
  margin-bottom: 20px;

}

input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 10px;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #4caf50;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

ul {
  color:#333;
  padding: 0;
  list-style-type: circle;
  list-style-position: inside;
}

li {
  align-items: center;
  justify-content: right;
  padding: 10px;
  background-color: #f8f8f8;
  border-radius: 5px;
  margin-bottom: 5px;
}


li:hover {
  background-color: #e9e9e9;
}

button.delete-btn {
  padding: 5px 10px;
  font-size: 12px;
  background-color: #347C36;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 10px;
  
}

button.add-btn {
  /* pozostałe właściwości */
  margin-bottom: 10px;
}

button.delete-btn:hover {
  background-color: #347C36;
}



.img {
  display: inline-flex;
  height: 25px;
  width: 92%;
 justify-content: space-between;
}

</style>
