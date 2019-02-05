<template>
  <div id="app">
    <section class="hero is-large">
    <div class="hero-head">
      <nav class="navbar">
        <div class="container">
          <div class="navbar-brand">
            <a class="navbar-item">
              <h3 class="logo">MagicFormatter</h3>
            </a>
            <span class="navbar-burger burger" data-target="navbarMenuHeroB">
              <span></span>
              <span></span>
              <span></span>
            </span>
          </div>
          <div id="navbarMenuHeroB" class="navbar-menu">
            <div class="navbar-end">
              
              <span class="navbar-item">
                <a class="button is-link is-inverted" target="_blank"  href="https://github.com/cleidimarviana/magicformatter" >
                  <span class="icon">
                    <i  class="fa fa-github fa-2x" aria-hidden="true"></i>
                  </span>
                </a>
              </span>
            </div>
          </div>
        </div>
      </nav>
    </div>
  </section>

  <section class="section">
    <div class="container">
      <span style="font-size: 12px"> Enter your JSON here to see the magic happen: (Your code will NOT be posted anywhere because the program will run in client mode).</span>
      <textarea v-model="inputDate" class="textarea" id="input" style="width:100%;" placeholder="Enter the content here..."></textarea>

      <div class="actions">

        <button v-on:click="jsonSubmit()" class="button is-link is-small" id="jsonSubmit">
          Make a magic
        </button>

        <button id="input-clear" class="button is-small">
          Clear
        </button>
      </div>

      <!-- <div style="position:fixed; bottom: 10px; right: 10px; float:right;">
        <a href="#header">BACK TO TOP</a>
      </div> -->
      <div id="magicWarning"></div>

      <div v-bind:class="{ hidden: isHidden }" style="overflow: auto;" id="outputResult">
        <pre class="tabSpace2" id="output"></pre>

        <div class="actions-pre">
          <button class="button is-link output is-small" id="btn-copyclipboard">
            Copy to clipboard
          </button>
          <button class="button output is-small" id="btn-clear-output">
            Clear
          </button>
          <div class="select is-small">
            <select id="select-convert">
              <option value="1">JSON to JSON</option>
              <option value="2">JSON to XML</option>
            </select>
          </div>

          <div class="select is-small">
            <select id="select-tab-space">
              <option value="2">2 Tab Space</option>
              <option value="3">3 Tab Space</option>
              <option value="4">4 Tab Space</option>
            </select>
          </div>
          <button class="button is-small" id="btn-minify">
            Minify/Compress
          </button>
        </div>
      </div>
    </div>
  </section>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      inputDate: '',
      isHidden: true
    }
  },
  methods:{
    jsonSubmit(){
      var input = this.inputDate;
      if(input){
        try {
          var c = $.parseJSON(input);
          var formattedJSONString = JSONFormat(input.replace(/[\s\n]+/g, ' '));

          this.isHidden = false;

          
        } catch (err){
          
        }
      }
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

#output, .textarea{
  font-size: 0.85rem;
}

pre{
  padding: 0.8em 0.8em;
  max-height: calc(100vh - 4em - 280px);
}

.section {
    padding: 1rem 1rem;
}
.actions, .actions-pre {
  padding-bottom: 8px;
  padding-top: 8px;
}
button{
  margin-left: 4px;
}

.tabSpace2{
  tab-size: 2;
}
.tabSpace3{
  tab-size: 3;
}
.tabSpace4{
  tab-size: 4;
}

#magicWarning .json-warning{
  border: 1px solid #ff0e0c;
  color: #ff0e0c;
  padding: 4px;
  border-radius: 4px;
}

.hidden { display: none; }

.logo{
  margin-bottom: 0;
    font-size: 26px;
    /* text-transform: uppercase; */
    font-family: inherit;
    font-weight: bold;
}


summary::-webkit-details-marker {
  display: none
}
summary:after {
  background: black; 
  content: "+"; 
  color: #fff; 
  float: left;  
  font-weight: bold; 
  padding: 0; 
  text-align: center; 
  width: 20px;
  left: 20px;
  margin-right: 10px;
}
details[open] summary:after {
  content: "-";
}
</style>
