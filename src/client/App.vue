<template>
  <div id="app">
    <section class="gap">
      <h1>单组动画[憋废话往下拉]</h1>
    </section>
    <section class="wikisec" ref="wikisec">
      <div class="content">
        <div class="descr">
          <h1 :class="{hideLeft: aniMap.wikisec.h1}">The Volunteer (The Witcher 3 secondary quests copied from <a href="http://witcher.wikia.com/wiki/The_Volunteer">Fandom wiki</a> )</h1>
          <p :class="{hideLeft: aniMap.wikisec.h1}">Head out to White Eagle Fort, 
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
        <picture :class="{hideRight: aniMap.wikisec.h1}">
          <img src="./assets/Tw3_the_volunteer.jpg" alt="Tw3_the_volunteer" class="fluid">
        </picture>
      </div>
    </section>
    <section class="group">

    </section>
    <section class="gap">
      <h1>多组动画</h1>
    </section>
    <section class="acfsec" ref="acfsec">
      <header>
        <h1>ac factions</h1>
      </header>

      <main>
        <div class="content">
          <div class="card" :class="{hideDown: aniMap.acfsec[0].hidden}">
            <picture>
              <img src="./assets/ac-logo-ass.png" alt="ass" class="fluid">
            </picture>
            <h2>Hidden Ones</h2>
          </div>

          <div class="card" :class="{hideDown: aniMap.acfsec[1].hidden}">
            <picture>
              <img src="./assets/ac-logo-tmp.png" alt="tmp" class="fluid">
            </picture>
            <h2>Order</h2>
          </div>

          <div class="card" :class="{hideDown: aniMap.acfsec[2].hidden}">
            <picture>
              <img src="./assets/ac-logo-ass.png" alt="ass" class="fluid">
            </picture>
            <h2>Hidden Ones</h2>
          </div>

          <div class="card" :class="{hideDown: aniMap.acfsec[3].hidden}">
            <picture>
              <img src="./assets/ac-logo-tmp.png" alt="tmp" class="fluid">
            </picture>
            <h2>Order</h2>
          </div>

          <div class="card" :class="{hideDown: aniMap.acfsec[4].hidden}">
            <picture>
              <img src="./assets/ac-logo-ass.png" alt="ass" class="fluid">
            </picture>
            <h2>Hidden Ones</h2>
          </div>

          <div class="card" :class="{hideDown: aniMap.acfsec[5].hidden}">
            <picture>
              <img src="./assets/ac-logo-tmp.png" alt="tmp" class="fluid">
            </picture>
            <h2>Order</h2>
          </div>
        </div>

      </main>

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

section.acfsec {
  margin: 10em auto;
}

section.acfsec h1 {
  text-align: center;
}

section.acfsec div.content {
  flex-wrap: wrap;
}

section.acfsec .card {
  transition: all 0.5s cubic-bezier(0.445, 0.05, 0.55, 0.95);
  width: 10em;
  text-align: center;
  padding: 1em;
  background-color: white;
  margin: 1em;
}

</style>

<script lang="ts">
import Vue from 'vue';
import Component from 'vue-class-component';

import inView from 'in-view';
import { Observable } from 'rxjs';
import 'rxjs/add/operator/throttleTime';
import { Subscription } from 'rxjs/Subscription';

@Component({
  name: 'app'
})
export default class App extends Vue {

  windowScrolling = Observable.fromEvent(window, 'scroll');
  scrollSubscription: Subscription;

  aniMap = {
    wikisec: {
      h1: true,
      p: true,
      picture: true
    },
    acfsec: [
        {
          name: "card1",
          hidden: true
        },
        {
          name: "card2",
          hidden: true
        },
        {
          name: "card3",
          hidden: true
        },
        {
          name: "card4",
          hidden: true
        },
        {
          name: "card5",
          hidden: true
        },
        {
          name: "card6",
          hidden: true
        }
      ]
    

  }

  createScrollMonitor() {
    let subscription = this.windowScrolling
      .throttleTime(200)
      .subscribe(
        (next) => {
          console.log("发现窗口滚动，我们已经节流");
          this.animateWhenSeen(this.$refs.wikisec as Element);
          this.animateGroupWhenSeen(this.$refs.acfsec as Element);
        }
      );

    return subscription;
  };



  // onWindowScroll = () => {
  //   console.log("发现窗口滚动，请注意节流");

  //   // 注册一下有哪些元素是进入视野才动画出现，这里用到了之前html里的ref
  //   this.animateWhenSeen(this.$refs.wikisec as Element);
  //   this.animateGroupWhenSeen(this.$refs.acfsec as Element);
  // }

  animateWhenSeen(ele: Element){

    if(ele && inView.is(ele)) {
      // 此时元素可见，那么让它出现
      // 注意这里是反着的，false表示不隐藏
      this.switchElementAnimState( this.aniMap, ele.classList[0], false );
    } else {
      // 元素已经淡出视野，就恢复初始的状态
      this.switchElementAnimState( this.aniMap, ele.classList[0], true );
    }
    
  };

  animateGroupWhenSeen(ele: Element){

    if(ele && inView.is(ele)) {

      // 此时元素可见，那么让它出现
      // 注意这里是反着的，false表示不隐藏
      this.switchGroupAnimState(this.aniMap['acfsec'], 'hidden', false, 100 );

    } else {

      // 元素已经淡出视野，就恢复初始的状态
      this.switchGroupAnimState(this.aniMap['acfsec'], 'hidden', true, 100 );

    }
    
  };

  /**
   * 开关某一容器的所有元素动画状态
   */
  switchElementAnimState = (mapObject: any, eleName: string, switchTo: boolean) => {
    // 遍历所有key把对应value全部设置成switchTo的值
    for (let key in mapObject[eleName]) {
      mapObject[eleName][key] = switchTo;
    }
  };

  /**
   * 开关某一动画组的所有元素动画状态，带有延时效果
   */
  switchGroupAnimState = (mapArray: any[], stateKey: string, switchTo: boolean, timeout: number = 100) => {

    for (let i = 0; i < mapArray.length; i++) {
      setTimeout(() => {
        mapArray[i][stateKey] = switchTo;
      }, i*timeout);
    }

  };

  mounted() {
    this.scrollSubscription = this.createScrollMonitor();
  }

  destroyed() {
    this.scrollSubscription.unsubscribe();
  }

}
</script>
