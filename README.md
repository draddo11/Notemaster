# Notemaster
A Note taking vue.js project 
<!DOCTYPE html>
<html>
<head>
  <title>Notemaster</title>
  <script src="https://cdn.jsdelivr.net/npm/vue"></script>
  <script src="https://unpkg.com/vue"></script>
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
  <link rel="stylesheet" href='http://davidtkatz.com/public_css/noteMaster.css'>
  <link href='css/bootstrap.min.css' rel='stylesheet'>
</head>
<body>
<div id='app'>
<h3>  {{title}} </h3>
<div class='form'>
<div class='form-group'>
  <label>Note Title</label>
  <input class='form-control'input='text' v-model='note.title'></input>
  <div class='form-group'>
    <label>Note Text</label>
    <textarea class='form-control' v-model='note.text'></textarea>
  </div>
  <button class='btn btn-primary' @click='addNote'>Submit</button>
  </div>
  <div class = 'col-sm-12'>
  <div class ='col-sm-4 note'v-for='(note,index) in notes'>

  <div class='card'>
<button class='close'@click='removeNote(index)'>&times</button>
  <div class='card-block'>
  <h4 class='card-title'>{{note.title}}</h4>
  <h6 class='card-subtitle mb-2 text-muted '>{{note.date}}</h6>
  <p class='card-text'>{{note.text}}</p>

</div>

</div>
</div>
</div>
 </div>
</div>

<script>
var app = new Vue({
  el:'#app',
  data:{
    title:'Notemaster',
    note :{
      title:'',
      text:''
    },
    notes:[
      {
        title:'Hawaii visit Highlights' ,
        text:'loved the fresh COCONUTS and beautiful beaches',
        date: new Date(Date.now()).toLocaleString()
      }
    ]
  },
  methods:{
    addNote(){
      let{title,text}=this.note
      this.notes.push({
        title,
        text,
        date:new Date(Date.now()).toLocaleString()
      })
    },
    removeNote(index){
      this.notes.splice(index,1)
    }
  }
})
</script>
</body>
</html>
