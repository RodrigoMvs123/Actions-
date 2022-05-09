https://www.youtube.com/watch?v=COPS4VMfaUc

https://raw.githubusercontent.com/RodrigoMvs123/Actions-/main/README.md



# Actions-

Node js ( Download ) 

To Clone the Pull Request " Actions on Github " ( Pull Request Name ) 
On Code
https://github.com/RodrigoMvs123/Actions-.git ( To copy repositorie address ) 

Terminal 
~cd development/
development git clone https://github.com/RodrigoMvs123/Actions-.git
development cd my Actions-on-Github
Actions-on-Github git:(master) npm init -y 
touch action.yml 
code. 

//
Explorer 
action.yml ( MVSC File ) 

name: 'Hello World'
description: 'Greet someone and record the time'
inputs:
  who-to-greet:  # id of input
    description: 'Who to greet'
    required: true
    default: 'World'
outputs:
  time: # id of output
    description: 'The time we greeted you'
runs:
  using: 'node16'
  main: 'index.js'

https://docs.github.com/pt/actions/creating-actions/creating-a-javascript-action
//

Terminal 
Actions-on-Github git:(master) npm install @actions/core 
Actions-on-Github git:(master) npm install @actions/github 

Explorer 
index.js ( MVSC File ) 
// 

const core = require('@actions/core')
const github = require('@actions/github')

try {
     `who-to-greet` input defined in action metadata file
  const nameToGreet = core.getInput('who-to-greet');
  console.log(`Hello ${nameToGreet}!`);
  const time = (new Date()).toTimeString();
  core.setOutput("time", time);
  // Get the JSON webhook payload for the event that triggered the workflow
  const payload = JSON.stringify(github.context.payload, undefined, 2)
  console.log(`The event payload: ${payload}`);
} catch (error) {
  core.setFailed(error.message);
}
https://docs.github.com/pt/actions/creating-actions/creating-a-javascript-action


//

Terminal 



Actions-on-Github git:(master) git add action.yml index.js node_modules/
* package.json package-lock.json README.md 
Actions-on-Github git:(master) git add action.yml index.js node_modules/
* package.json package-lock.json README.md -f 
Actions-on-Github git:(master) git commit -m"my github action"
Actions-on-Github git:(master) git tag -a -m "my github action" v1
Actions-on-Github git:(master) git push - - follow-tags 


//
Explorer 
.github/workflows/main.yml

on: [push]

jobs:
  hello_world_job:
    runs-on: ubuntu-latest
    name: A job to say hello
    steps:
      - name: Hello world action step
        id: hello
        uses: Rodrigo/ActionsonGithub@v1
        with:
          who-to-greet: 'Rodrigo'
      # Use the output from the `hello` step
      - name: Get the output time
        run: echo "The time was ${{ steps.hello.outputs.time }}"
        
        
 https://docs.github.com/pt/actions/creating-actions/creating-a-javascript-action
        
//

Terminal 

Actions-on-Github git:(master) git add .
Actions-on-Github git:(master) git commit -m"add main.yml"
Actions-on-Github git:(master) git push origin HEAD 

Go to Actions Tab ( On Github ) 
- workflow 

