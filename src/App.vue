<template>
  <div id="app">
    <section class="seleccion">
      <form>
        <div class="box">
          <label for="">Titulo:</label>
          <input type="text" v-model="titulo">
        </div>
        <hr>
        <div class="box">
          <label for="emoji">Emoji:</label>
          <select name="emoji" id="emoji" v-model="emoji">
            <option v-for="(emoji, index) in emotes" :key="index" :value="emoji.path">{{ emoji.path }}</option>
          </select>
        </div>
        <hr>
        <div class="box apreciacion">
          <label for="">Apreciación: </label>
          <div>
            <input type="radio" value="Regular" v-model="apreciacion">Regular
            <input type="radio" value="Bien" v-model="apreciacion">Bien
            <input type="radio" value="Muy bien" v-model="apreciacion">Muy bien
            <input type="radio" value="Incrible" v-model="apreciacion">Increible
          </div>

        </div>
        <hr>
        <div class="box competencias">
          <label for="">Competencias aprendidas:</label>
          <div class="checked">
            <li>
              <input type="checkbox" value="Morfología de un componente" v-model="competencias">Morfología de un componente
            </li>
            <li>
              <input type="checkbox" value="Directivas" v-model="competencias">Directivas
            </li>
            <li>
              <input type="checkbox" value="One-Way y Two-Way data binding" v-model="competencias">One-Way y Two-Way data binding
            </li>
            <li>
              <input type="checkbox" value="Estado" v-model="competencias">Estado
            </li>
            <li>
              <input type="checkbox" value="El patrón de diseño MVVM" v-model="competencias">El patrón de diseño MVVM
            </li>
          </div>
        </div>
        <hr>
        <div class="box opinion">
          <label for="">Opinión:</label>
          <textarea v-model="opinion"></textarea>
        </div>
      </form>
    </section>
    <section class="informacion">
      <h2>{{ emoji }}</h2>
      <h2>{{ titulo }}</h2>
      <h3>Y mi parece <span>{{ apreciacion }}</span></h3>
      <p>He aprendido:</p>
      <span> {{ competencias.join(' - ') }} </span>
      <p>Mi opinion hasta ahora del framework es:</p>
      <p><em>{{ opinion }}</em></p>
    </section>
  </div>
</template>

<script>


export default {
  name: 'App',
  components: {

  },
  data() {
    return {
      titulo: '',
      apreciacion: '',
      opinion: '',
      emoji: '',
      competencias: [],
      emotes: [
        { path: "💻" },
        { path: "😍" },
        { path: "😎" },
        { path: "🖥️" }
      ]

    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  display: flex;
  margin: 30vh 10%;
  gap: 90px;
}

label,
input,
select {
  font-size: 25px;
}

li {
  font-size: 20px;
}

.seleccion {
  width: 800px;
  height: 450px;
  border-radius: 20px;
  padding: 20px;
  color: white;
  background-color: rgb(45, 42, 42);
}

.box {
  padding: 10px;
  gap: 10px;
}

.competencias {
  display: flex;
  gap: 90px;

  & label {
    width: 60px;
  }

  & .checked li {
    display: flex;
    align-items: center;
    margin: 10px;
  }

}

input[type="radio"] {
  margin: 0 5px;
  font-size: 20px
}

.opinion {
  display: flex;
  gap: 10px;
}

.informacion {
  text-align: center;
  border: 1px solid black;
  border-radius: 20px;
  width: 800px;
  height: 450px;
  padding: 20px;
  font-size: 1.2em;
}

h2 {
  font-size: 2.5em;
  height: 55px;
  padding: 5px 0;
}

h3 {
  padding: 20px 0;
}

span {
  height: 30px;
  padding: 10px 0;
}

p {
  padding: 20px 0;
}

@media (max-width: 768px) {
  #app {
    display: block;
  }

  .seleccion,
  .informacion {
    max-width: 500px;
    margin: 20px 10%;
  }

}

@media (max-width:400px) {

  .seleccion,
  .informacion {
    max-width: 300px;
    height: 450px;
    margin: 20px 0;
  }

  label,
  input,
  select,
  li {
    font-size: 0.9em;
  }

  .apreciacion label {
    width: 250px;
  }

  .competencias {
    display: inline-block;
  }

  h2{
    font-size: 1.6em
  }

}
</style>
