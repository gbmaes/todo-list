<template>
  <div id="app">
    <div class="container">
      <h1>TODO LIST</h1>
      <input type="text" class="input" v-model="newToDo"/>
    </div>
      <br>
      <button class="add-button button-add" v-on:click="add()">Add</button>
      <ul style="list-style-type: none;">
        <li v-for="(todo,i) in currentToDo">
          <span>
            {{i + 1}}: {{todo.text}} <br>
          </span> 
          <br>
          <button class="delete-button button-x" @click="deleteToDo(i)">X</button>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  name: 'app',
  data () {
    return {
      newToDo: '',
      currentToDo: [
        {text: 'Get Groceries', id:0},
        {text: 'Run Errands', id:1},
        {text: 'Buy Stamps', id:2}
      ]
    }
  },
  methods:{
    add(){
      this.currentToDo.push({
        text: this.newToDo,
        id: new Date().valueOf()
      }),
      this.newToDo = ''
    },
    deleteToDo(i){
      this.currentToDo.splice(i,1)
    }
  }
}
</script>
<style>
body{
  text-align: center;
  font-family: 'Courier New', monospace;
}

h1 { color: black; 
  font-family: 'Droid serif', serif; 
  font-size: 42px; 
  font-weight: 500; 
  font-style: italic; 
  line-height: 50px; 
  margin: 0 0 12px; 
}
/* add button */
.button-add {
  appearance: none;
  background-color: #2ea44f;
  border: 1px solid rgba(27, 31, 35, .15);
  border-radius: 6px;
  box-shadow: rgba(27, 31, 35, .1) 0 1px 0;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  display: inline-block;
  font-family: -apple-system,system-ui,"Segoe UI",Helvetica,Arial,sans-serif,"Apple Color Emoji","Segoe UI Emoji";
  font-size: 14px;
  font-weight: 600;
  line-height: 20px;
  padding: 6px 12px;
  position: relative;
  text-align: center;
  text-decoration: none;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  vertical-align: middle;
  white-space: nowrap;
}

.button-add:focus:not(:focus-visible):not(.focus-visible) {
  box-shadow: none;
  outline: none;
}

.button-add:hover {
background-color: #2c974b;
}

.button-add:focus {
  box-shadow: rgba(46, 164, 79, .4) 0 0 0 3px;
  outline: none;
}

.button-add:disabled {
  background-color: #94d3a2;
  border-color: rgba(27, 31, 35, .1);
  color: rgba(255, 255, 255, .8);
  cursor: default;
}

.button-add:active {
  background-color: #298e46;
  box-shadow: rgba(20, 70, 32, .2) 0 1px 0 inset;
}

/*x button*/
.button-x {
  background: #e62143;
  border-radius: 6px;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  display: flex;
  font-size: 0.5em;
  font-weight: 700;
  justify-content: center;
  padding: .8em 1em;
  text-align: center;
  text-decoration: none;
  text-decoration-skip-ink: auto;
  text-shadow: rgba(0, 0, 0, .3) 1px 1px 1px;
  text-underline-offset: 1px;
  transition: all .2s ease-in-out;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  word-break: break-word;
  border: 0;
}
</style>
