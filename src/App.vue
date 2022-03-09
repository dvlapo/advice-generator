<script>
export default {
  data() {
    return {   
      randomAdvice: {
        id: null,
        advice: ''
      }
    }
  },
  created() {
    this.fetchAdvice()
  },
  methods: {
    fetchAdvice() {
      fetch('https://api.adviceslip.com/advice')
        .then(response => response.json())
        .then(quoteObj => this.randomAdvice = quoteObj.slip)
        .catch(err => console.log("Error:", err))
    }
  },
}
</script>

<template>
  <main>
    <h1>advice #{{randomAdvice.id}}</h1>
    <p class="quote">❝{{randomAdvice.advice}}❞</p>
    <div class="pattern-divider">
      <img  src="./assets/images/pattern-divider-mobile.svg" alt="">
    </div>
    
    <button class="dice-holder" aria-label="Generate random advice" @click="fetchAdvice">
      <img class="dice" src="./assets/images/icon-dice.svg" alt="">
    </button>  
  </main>
  <div class="attribution">
    Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>. 
    Coded by <a href="https://github.com/dvlapo">dvlapo</a>.
  </div>
</template>

<style>
@import "./assets/base.css";

main {
  background-color: var(--dark-grayish-blue);
  padding: 1.5rem;
  width: min(500px, 90vw);
  border-radius: .8em;
  position: absolute;
  top: 43%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
}

main h1 {
  text-transform: uppercase;
  color: var(--neon-green);
  font-size: clamp(.7rem, .9vw, .95rem);
  margin-bottom: 1rem;
  letter-spacing: 2px;
}

.quote {
  color: var(--light-cyan);
  font-size: clamp(1.8rem, 1.2vw, 2.2rem);
  margin-bottom: 1.2rem;
}

.pattern-divider {
  margin-bottom: 1.2rem;
}

.dice-holder {
  background-color: var(--neon-green);
  padding: 1.2em;
  border-radius: 50%;
  border: none;
  display: inline-grid;
  place-items: center;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  cursor: pointer;
  transition: 150ms;
}

.dice-holder:hover {
  box-shadow: 0px 0px 27px 0px var(--neon-green);
}

.attribution { 
  font-size: 10px; 
  text-align: center; 
  color: #fff;
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
}
   
.attribution a { 
  color: hsl(228, 45%, 44%); 
}

</style>
