<html>
<head>
  <title>Kasus no.2</title>
</head>
<body>
  <div id="app">
    <h1>{{message}}</h1>
    <input v-model="message">
    <br><br>
    <button v-on:click= "reverseMessage">Reverse</button>
    <button @click="undo()" :disabled="!canUndo">undo/redo</button>
  </div>

  <style>
    body{
      text-align: center;
      padding-top: 200px;
    }
  </style>
</body>
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
  new Vue({
    el: '#app',
    data: {
      message: 'Indonesia',
    },
    methods:{
      reverseMessage: function(){
        this.message = this.message.split('').reverse().join('')
      },
      undo: function() {
        if (this.canUndo) {
          this.historyIndex -= 1
          this.todos = this.history[this.historyIndex]
        }
      },
    }
  })
</script>
</html>
