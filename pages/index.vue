<template>
  <div class="container">
    <div class="upper">
      <div class="row">
        <div class="col-lg-6 relative">
          <h1>Hi, I'm Kaiwen!</h1>
          <p>I'm a junior compsci + math major and have done <a href="https://gotechnica.org/">Technica</a> for the past couple of years (last yr's co-lead). I play club ultimate frisbee. Currently I'm abroad in Italy, and have traveled all around Europe. I'm interested in full-stack development, with a particular interest in learning more about back-end architectural design.</p>
          <p id="align-btm">Check out where I've <a v-on:click="showImg" id="been-btn" href="#low-section">been!</a> ⬇️</p>
        </div>
        <div class="col-lg-6">
          <img src="/kaiwen_images/kaiwen.jpg" class="img-fluid" id="profile-pic">
        </div>
      </div>
    </div>
    <div class="low" id="low-section">
        <div class="row">
          <div class="col-md-4">
            <div class="overlay" v-on:mouseover="displayOverlay" v-on:mouseleave="hideOverlay">
              <p class="overlay-text">Rome, Italy</p>
              <img src="/kaiwen_images/rome.jpg">
            </div>
          </div>
          <div class="col-md-4">
            <div class="overlay" v-on:mouseover="displayOverlay" v-on:mouseleave="hideOverlay">
              <p class="overlay-text">Naples, Italy</p>
              <img src="/kaiwen_images/naples.jpg">
            </div>
          </div>
          <div class="col-md-4">
            <div class="overlay" v-on:mouseover="displayOverlay" v-on:mouseleave="hideOverlay">
              <p class="overlay-text">Positano, Italy</p>
              <img src="/kaiwen_images/positano.jpg">
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-md-4">
            <div class="overlay" v-on:mouseover="displayOverlay" v-on:mouseleave="hideOverlay">
              <p class="overlay-text">Prague, Czech Republic</p>
              <img src="/kaiwen_images/prague.jpg">
            </div>
          </div>
          <div class="col-md-4">
            <div class="overlay" v-on:mouseover="displayOverlay" v-on:mouseleave="hideOverlay">
              <p class="overlay-text">Interlaken, Switzerland</p>
              <img src="/kaiwen_images/switzerland.jpg">
            </div>
          </div>
          <div class="col-md-4">
            <div class="overlay" v-on:mouseover="displayOverlay" v-on:mouseleave="hideOverlay">
              <p class="overlay-text">Paris, France</p>
              <img src="/kaiwen_images/paris.jpg">
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-md-4">
            <div class="overlay" v-on:mouseover="displayOverlay" v-on:mouseleave="hideOverlay">
              <p class="overlay-text">Brussels, Belgium</p>
              <img src="/kaiwen_images/brussels.jpg">
            </div>
          </div>
          <div class="col-md-4">
            <div class="overlay" v-on:mouseover="displayOverlay" v-on:mouseleave="hideOverlay">
              <p class="overlay-text">Amsterdam, Netherlands</p>
              <img src="/kaiwen_images/amsterdam.jpg">
            </div>
          </div>
          <div class="col-md-4">
            <div class="overlay" v-on:mouseover="displayOverlay" v-on:mouseleave="hideOverlay">
              <p class="overlay-text">London, England</p>
              <img src="/kaiwen_images/london.jpg">
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-md-4">
            <div class="overlay" v-on:mouseover="displayOverlay" v-on:mouseleave="hideOverlay">
              <p class="overlay-text">Dublin, Ireland</p>
              <img src="/kaiwen_images/dublin.jpg">
            </div>
          </div>
          <div class="col-md-4">
            <div class="overlay" v-on:mouseover="displayOverlay" v-on:mouseleave="hideOverlay">
              <p class="overlay-text">Munich, Germany</p>
              <img src="/kaiwen_images/munich.jpg">
            </div>
          </div>
          <div class="col-md-4">
            <div class="overlay" v-on:mouseover="displayOverlay" v-on:mouseleave="hideOverlay">
              <p class="overlay-text">Barcelona, Spain</p>
              <img src="/kaiwen_images/barcelona.jpg">
            </div>
          </div>
        </div>
      </div>
      <div class="food">
        <h3 class="overlay" id="food-text">Scroll down for food ⬇️</h3>
      </div>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

function displayOverlay(e: any) {
  e.target.style.opacity = 0.2
  e.target.parentElement.querySelector('.overlay-text').style.display = 'inline'
  console.log(e.target.parentElement.querySelector('.overlay-text'))
}

function hideOverlay(e: any) {
  e.target.querySelector('img').style.opacity = 1
  e.target.querySelector('.overlay-text').style.display = 'none'
}

let showImg = (e: any) => {

  let imgs: NodeListOf<HTMLElement> = document.querySelectorAll<HTMLElement>('.overlay')
  for (let i = 0; i < imgs.length - 1; i++) {
    let item: HTMLElement = imgs[i]
    item.addEventListener('animationend', e => {
      let nextItem: HTMLElement = imgs[i + 1]
      nextItem.classList.add('fade-in')
    });
  }

  imgs[0].classList.add('fade-in')
}

</script>


<style scoped>
#profile-pic {
  border-radius: 5px;
}

.upper {
  margin-top: 5%;
  width: 50%;
  height: auto;
  margin-left: auto;
  margin-right: auto;
}

#align-btm {
  position: absolute;
  bottom: 0;
}

.relative {
  position: relative;
}

.low {
  margin-top: 3%;
  scroll-margin-top: 10px;
}

.low img {
  width: 100%;
  z-index: -1;
  border-radius: 5px;
}

.low .row {
  margin-top: 3%;
}

.overlay {
  position: relative;
  z-index: 1;
  opacity: 0;
  margin-bottom: 5%;
}

.overlay-text {
  position: absolute;
  top: 50% !important;
  left: 50%;
  padding: 0;
  transform: translate(-50%, -50%);
  color: white;
  display: none;
}

.fade-in {
  animation-name: fadeInOpacity;
	animation-iteration-count: 1;
	animation-timing-function: ease-in;
	animation-duration: 0.5s;
  animation-fill-mode: forwards
}

a {
  color: white;
}

#food-text {
  text-align: center;
}

@keyframes fadeInOpacity {
	0% {
		opacity: 0;
	}

	100% {
		opacity: 1;
	}
}

@media (max-width: 1399px) {
  #align-btm {
    position: static;
  }
}

</style>
