<template>
  <div id="app">
    <section class="gap">
      <h1>憋废话往下拉</h1>
    </section>
    <section class="wikisec" ref="wikisec">
      <div class="content">
        <div class="descr">
          <h1>The Volunteer (The Witcher 3 secondary quests from Fandom)</h1>
          <p>Head out to White Eagle Fort, 
            which is just west of Oxenfurt Harbor, 
            to hear a badly singing troll who goes by the name Trollololo.
            Talk to him to learn that he sees himself as a Redanian soldier now, 
            having been asked by some to guard over some boats that the soldiers took from peasants in the area.
            However, the peasants arrived to take their boats back while the soldiers were still there and the two groups fought.
            Trollololo tried to help the soldiers but due to his brute strength he accidentally killed everyone, 
            peasants and soldiers alike. He then decided to not let the "meat" go to waste and cooked and ate the bodies.
            Geralt can then decide to let it slide or kill Trollololo.
          </p>
        </div>
        <picture>
          <img src="./assets/Tw3_the_volunteer.jpg" alt="Tw3_the_volunteer" class="fluid">
        </picture>
      </div>
    </section>
    <section class="gap">
      <h1>划过了快回去</h1>
    </section>
  </div>
</template>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

section.wikisec {
  margin-top: 19em;
}

section.wikisec  div.content {
  border-bottom: 1px solid #f3f4f5;
}

section.wikisec  picture {
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 1s ease-in;
}

section.gap {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 150vh;
}

div.descr {
  max-width: 40%;
  transition: all 1s ease-in;
  margin-right: 3em;
}

div.descr  h1 {
  transition: inherit;
}

div.descr  p {
  line-height: 30px;
  font-size: 18px;
  transition: inherit;
}


</style>

<script lang="ts">
import Vue from 'vue';
import Component from 'vue-class-component';

@Component({
  name: 'app'
})
export default class App extends Vue {

}
</script>
