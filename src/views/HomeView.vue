<template>
  <v-app id="home">
    <NavBar/>
    <v-container fluid>
      <div class="head">
        <v-row>
          <v-col cols="5">
            <div style="position: relative" class="mt-16">
              <h1 class="text-grey">Hello,</h1>
              <h1 class="text-white">I'm Xinyu Chen</h1>
              <span class="text-grey">Software Enginnering Graduate</span>
              <br>

              <v-btn
                tile
                dark
                class="text-yellow mt-8"
                variant="outlined"
                @click="scroll('contact')"
              >Contact me</v-btn>
            </div>
          </v-col>
          <v-col cols="2">
            <div
              style="
                position: absolute;
                z-index: 9999;
                bottom: 0;
                margin-left: auto;
                margin-right: auto;
                left: 0;
                right: 0;
                text-align: center;
              "
              class="mt-16"
            >
              <v-icon @click="scroll('contact')">fas fa-angle-double-down</v-icon>
            </div>
          </v-col>
          <v-col cols="5">
            <div style="position: relative; z-index: 9999" class="mt-16">
              <v-img src="IMG_0074.jpg" contain max-height="300"></v-img>
            </div>
          </v-col>
        </v-row>
      </div>
      <v-col cols="12" class="mt-16" id="about">
        <div>
          <v-row>
            <v-col cols="12" sm="6">
              <div>
                <v-img src="IMG_2701.jpg" max-height="600" class></v-img>
              </div>
            </v-col>
            <v-col cols="12" sm="6">
              <h1 class="mt-16">About Me</h1>
              <div style="width: 800px">
                <v-slider v-model="slider2" color="black" disabled="true" min="-500" max="500"></v-slider>
              </div>
              <h2 class="mt-n4">Bio</h2>
              <p class="text-black">
                Born in China, Sep 1998
                <br>Bachelor of Engineering (Software)---------------------2021 Carleton University
                <br>Master of Engineering (System & Technology)-----------------------2022 McMaster University
              </p>
              <br>
              <h2 class="mt-n4">Work Experience</h2>
              <p class="text-black">
                2019/09--2020/08 &nbsp; &nbsp; &nbsp;
                <strong>Software Verifictaion Engineer @Ribbon Communication</strong>
                <br>2022/09--Now &nbsp; &nbsp; &nbsp;
                <strong>Support Engineer @Ribbon Communication</strong>
              </p>
              <br>
              <h2 class="mt-n4">Technical Skills</h2>
              <h3>Programming Languages</h3>
              <p class="text-black">
                <v-icon>fa-brands fa-php</v-icon>&nbsp;
                <v-icon>fa-brands fa-js</v-icon>&nbsp;
                <v-icon>fa-brands fa-java</v-icon>&nbsp;
                <v-icon>fa-brands fa-python</v-icon>&nbsp;
                <v-icon>fa-solid fa-database</v-icon>
              </p>
              <h3>Software Tools</h3>
              <p class="text-black">Eclipse, VS Code, VS Studio, HBuildX, Git Bash</p>

              <v-btn href="UpdatedResume.pdf" dark color="yellow" class="mt-4" download>Download Resume</v-btn>
              <br/>
            </v-col>
          </v-row>
        </div>
      </v-col>

      <v-col cols="12" sm="12" id="services">
        <div class="d-flex justify-center mb-6">
          <v-btn  size="x-large" color="#FBDF7E" class="mr-2" @click="showAll">All</v-btn>
          <v-btn  size="x-large" class="mr-2" variant="tonal" @click="showDesign">Web Design</v-btn>
          <v-btn  size="x-large" class="mr-2" variant="tonal" @click="showMVC">MVC Project</v-btn>
        </div>
      </v-col>

      <div id="change">
        <MVC v-if="value1"></MVC>
        <Web v-if="value3"></Web>

        <v-col cols="12" sm="12" xs="12" class="imgHover" v-if="value2">
          <v-row class="fill-height" justify="center">
            <template v-for="(item, i) in items" :key="i">
              <v-col cols="12" md="4" xs="12" sm="6" v-if="item.num<7">
                <v-hover v-slot="{ isHovering, props }">
                  <v-card
                    :elevation="isHovering ? 12 : 2"
                    :class="{ 'on-hover': isHovering }"
                    v-bind="props"
                  >
                    <v-img :src="item.img"  height="325px" @click=change(item.tp) cover></v-img>
                  </v-card>
                </v-hover>
              </v-col>
            </template>
          </v-row>
        </v-col>
      </div>

      <v-col cols="12" class="imgHover" v-if="value4">
          <v-row class="fill-height" align="center" justify="center">
            <template v-for="(item, i) in items" :key="i">
              <v-col cols="12" md="4" v-if="item.num>6">
                <v-hover v-slot="{ isHovering, props }">
                  <v-card
                    :elevation="isHovering ? 12 : 2"
                    :class="{ 'on-hover': isHovering }"
                    v-bind="props"
                  >
                    <v-img :src="item.img" height="325px" @click=change(item.tp) cover></v-img>
                  </v-card>
                </v-hover>
              </v-col>
            </template>
          </v-row>
        </v-col>

      <v-col cols="12" sm="12">
        <div class="d-flex justify-center mb-6">
          <v-btn color="#FBDF7E" class="mt-4" @click="disMore" v-if="!value4" v-show="value5">Load More</v-btn>
          <v-btn color="#FBDF7E" class="mt-4" @click="disMore" v-if="value4">Display Less</v-btn>
        </div>
      </v-col>

      <v-col cols="12" sm="12" class="px-16" id="contact">
        <v-row class="fill-height" align="center" justify="center">

            <div class="child">
              <h1>Contact info.</h1>
              <v-btn icon="fas fa-map-marker-alt" color class="mt-10" variant="outlined"></v-btn>
              <br>
              <span class="text-caption">Ottawa,ON</span>
              <br>
              <v-btn icon="fas fa-phone-alt" color class="mt-10" variant="outlined"></v-btn>
              <br>
              <span class="text-caption">613-2764-687</span>
              <br>
              <v-btn icon="fas fa-envelope" color class="mt-10" variant="outlined"></v-btn>
              <br>
              <span class="text-caption">nick.chenbca@gmail.com</span>
              <br>
            </div>
        </v-row>
      </v-col>
    </v-container>
    <FooterView/>
  </v-app>
</template>

<script>
import { defineComponent } from "vue";
import NavBar from "../components/NavBar.vue";
import FooterView from "../components/FooterView.vue";
import MVC from "../components/MVC.vue";
import Web from "../components/WebView.vue";
// Components

export default defineComponent({
  name: "HomeView",

  setup() {
    return {
      slider2: 5000,

      items: [
        {
          img: "model-uml.png",
          tp: 3,
          num:1,
        },
        {
          img: "p1.png",
          tp: 3,
          num:2,
        },
        {
          img: "p5.png",
          tp: 1,
          num:3,
        },
        {
          img: "p2.png",
          tp: 1,
          num:4,
        }, 
        {
          img: "p3.png",
          tp: 3,
          num:5,
        },
        {
          img: "p4.png",
          tp: 1,
          num:6,
        },
        {
          img: "p4.png",
          tp: 1,
          num:7,
        },
       
      ]
    };
  },

  data(){
    return{
      value1: false,
      value2: true,
      value3: false,
      value4: false,
      value5: true,
    }
  },

  methods: {
    scroll(refName) {
      const element = document.getElementById(refName);
      element.scrollIntoView({ behavior: "smooth" });
    },
    showMVC() {
      this.value1 = true;
      this.value2 = false;
      this.value3 = false;
      this.value5 = false;
    },
    showDesign() {
      this.value1 = false;
      this.value2 = false;
      this.value3 = true;
      this.value5 = false;
    },
    showAll() {
      this.value1 = false;
      this.value2 = true;
      this.value3 = false;
      this.value5 = true;
    },
    change(number) {
      if(number ==1){
        this.value1 = false;
        this.value2 = false;
        this.value3 = true;
      }
      if(number ==3){
        this.value1 = false;
        this.value2 = false;
        this.value3 = true;
      }
    }, 
    disMore(){
      this.value4= !this.value4;
    }
  
  },
  components: {
    NavBar,
    FooterView,
    MVC,
    Web,
  }
});
</script>
<style scoped>
.v-container {
  padding: 16px 0 16px 0;
}
.head {
  position: relative;
  text-align: center;
  padding: 12px;
  margin-bottom: 6px;
  height: 400px;
  width: 100%;
  color: white;
}
.head:before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 50%;
  background: black;
  transform: skew(0deg, 6deg);
}
.head:after {
  content: "";
  position: absolute;
  top: 0;
  right: 0;
  height: 100%;
  width: 50%;
  background: black;
  transform: skew(0deg, -6deg);
}
.egg {
  display: block;
  margin-left: 100px;
  margin-top: 50px;
  width: 356px;
  height: 300px;
  background-color: #fbdf7e;
  border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
}
.first {
  width: 100%;
  height: 280px;
  text-align: center;
  padding: 2rem 2rem;
}
.child {
  display: inline-block;
  padding: 2rem 1rem;
  vertical-align: middle;
  text-align: center;
  margin-right: 8px;
}
.imgHover {
  padding: 0 50px;
}
.pre {
  width: 100%;
  height: 380px;
  text-align: center;
  padding: 0 200px;
  background-color: #f5f5f5;
}
.hire {
  width: 100%;
  height: 200px;
  padding: 0 200px;
  background-color: #e9e9e9;
  margin-top: -24px;
}
</style>