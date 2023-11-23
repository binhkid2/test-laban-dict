<script lang="ts">
    
    import axios from "axios"
    let aiGene:string = ""
    let prompt =  "Write a story about a magic backpack"
function sendApi(){
    axios.post("https://generativelanguage.googleapis.com/v1beta3/models/text-bison-001:generateText?key=AIzaSyCV0ZdEJwEZdPbRhgEQ_ja8UheaoOfTVTA", {
        "prompt": { "text": prompt} 
  })
  .then(function (response) {
    aiGene = response.data.candidates[0].output
    console.log(response.data.candidates)
  })
  .catch(function (error) {
    console.log(error);
  });
}
</script>
<form on:submit|preventDefault={sendApi}>

<input bind:value={prompt} />
<button type="submit">Send</button>
</form>
<p>{aiGene}</p>