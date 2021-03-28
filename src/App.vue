<template>
  <div id="app">
      <!-- Navigation -->
      <nav class="contain__navbar">
        <div class="container">

          <div class="navbar">
            <!-- logo -->
            <h1 class="navbar__brand">
              <img :src="require('@/assets/image/logo-bookmark.svg')" alt="">
            </h1>
          
            <!-- btn nav -->
            <div class="navbar__hamburger" @click="openNav">
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="15">
              <path fill="#242A45" fill-rule="evenodd" d="M0 0h18v3H0V0zm0 6h18v3H0V6zm0 6h18v3H0v-3z"/>
            </svg>
            </div>

            <!-- link -->
            <div class="nav">
              <div class="nav__top">
                <span>
                  <img :src="require('@/assets/image/logo-bookmark-autre.svg')" alt="">
                </span>
                <span @click="closeNav">
                  <svg xmlns="http://www.w3.org/2000/svg" width="16" height="15"><path fill="#FFF" fill-rule="evenodd" d="M8 5.379L13.303.075l2.122 2.122L10.12 7.5l5.304 5.303-2.122 2.122L8 9.62l-5.303 5.304-2.122-2.122L5.88 7.5.575 2.197 2.697.075 8 5.38z"/>
                  </svg>
                </span>
              </div>
              <ul class="nav__list">
                <li class="nav__link">features</li>
                <li class="nav__link">pricing</li>
                <li class="nav__link">contact</li>
                <li class="nav__link"><button class="btn__link">login</button></li>
              </ul>
              <div class="nav__social">
                <a href="" class="nav__link__social">
                  <img :src="require('@/assets/image/icon-facebook.svg')" alt="">
                </a>
                <a href="" class="nav__link__social">
                  <img :src="require('@/assets/image/icon-twitter.svg')" alt="">
                </a>
              </div>
            </div>
          </div>

        </div>
      </nav>

      <!-- Header -->
      <header class="container">

        <div class="header">

          <div class="header__media">
            <img :src="require('@/assets/image/illustration-hero.svg')" alt="">
            <span class="bg__circle"></span>
          </div>
          <div class="header__text">
            <h2 class="header__text__title">A Simple Bookmark Manager</h2>
            <p class="header__text__p">A clean and simple interface to organize tour favorite websites. Open a new browser tab and see your sites load instantly. Try if for free.</p>
            <div class="header__text__buttons">
              <button class="btn btn__blue__plain">Get it on Chrome</button>
              <button class="btn btn__light__plain">Get it on Firefox</button>
            </div>
          </div>

        </div>

      </header>

      <!-- Main -->
      <main>

        <!-- Section with tabs -->
        <section class="container section">

          <div class="s-section">
            <h3 class="s-section__title">Features</h3>
            <p class="s-section__p">Our aim is to make it quick and easy for you to acces your favourite websites. Your bookmark sync between your devices so you can access them on the go.</p>
          </div>

          <!-- Tabs -->
          <tabs-container>
            <template v-slot:link>
              <tabs-links 
              :file="tabs.links"
              @emit-go-tab="goTab"></tabs-links>
            </template>

            <template v-slot:tab>
              <tabs-items :file="tabs.text"></tabs-items>
            </template>
            
           
          </tabs-container>


        </section>

        <!-- Section with Cards -->
        <section class="container section">

          <div class="s-section">
            <h3 class="s-section__title">Download the extension</h3>
            <p class="s-section__p">We've got more browsers in the pipeline. Please do let us know if you've got a favourite you'd like us to prioritize.
            </p>
          </div>

          <!-- Cards -->
          <div class="wrapper__cards">
            <card-item :file="cards.cards[0]"></card-item>
            <card-item :file="cards.cards[1]"></card-item>
            <card-item :file="cards.cards[2]"></card-item>
          </div>

        </section>

        <!-- Section with Ask Questions -->
        <section class="container section">

           <div class="s-section">
            <h3 class="s-section__title">Frequently Asked Questions</h3>
            <p class="s-section__p">Here are some of our FAQs. If you have any other questions you'd like answered please feel free to email us.</p>
          </div>

          <!-- Ask -->
          <div class="wrapper__ask">
            <ask-item :file="questions.questions[0]" @emit-answer="answerAsk"></ask-item>
            <ask-item :file="questions.questions[1]" @emit-answer="answerAsk"></ask-item>
            <ask-item :file="questions.questions[2]" @emit-answer="answerAsk"></ask-item>
            <ask-item :file="questions.questions[3]" @emit-answer="answerAsk"></ask-item>
          </div>

          <div>
            <button class="btn btn__blue__plain btn__center">More info</button>
          </div>

        </section>

        <!-- Section contact us -->
        <section class="section wrapper__contact">
          <div class="container">
            <div class="contact">
              <span class="contact__text__sm">35,000+ already joined</span>
              <span class="contact__text__bg">Stay up-to-date with what we're doing</span>
              <div class="wrapper__form">
                <div class="contact__form"
                :class="{error : errorUserMail}">
                    <div>
                      <form action="" class="formulaire">
                        <input 
                        v-model="userMail"
                        type="text" 
                        class="contact__form__input">
                        <img v-if="errorUserMail"
                        class="error__logo" 
                        :src="require('@/assets/image/icon-error.svg')" alt="">
                      </form>
                      <span class="contact__form__error__icon"></span>
                    </div>
                    <span class="contact__form__error__text">Whoops, moke sure it's an email</span>
                </div>
                <span class="btn__contact__us" @click.prevent="sendMail(userMail)">Contact us</span>
              </div>
            </div>
          </div>
        </section>
      </main>

      <!-- Footer -->
      <footer class="wrapper__footer">
        <div class="container">
          <div class="footer">
            <h2 class="footer__logo">
              <img :src="require('@/assets/image/logo-bookmark-autre.svg')" alt="">
            </h2>
            <ul class="footer__links">
              <li class="footer__link"><a href="">Features</a></li>
              <li class="footer__link"><a href="">Pricing</a></li>
              <li class="footer__link"><a href="">Contact</a></li>
            </ul>
            <div class="footer__social">
              <a href="" class="footer__link__social">
                <img :src="require('@/assets/image/icon-facebook.svg')" alt="">
              </a>
              <a href="" class="footer__link__social">
                <img :src="require('@/assets/image/icon-twitter.svg')" alt="">
              </a>
            </div>
          </div>
        </div>
      </footer>


  </div>
</template>

<script>
import TabsContainer from '@/components/tabs/TabsContainer.vue';
import TabsLinks from '@/components/tabs/TabsLinks.vue';
import TabsItems from '@/components/tabs/TabsItems.vue';
import CardItem from '@/components/cards/CardItem.vue';
import AskItem from '@/components/ask/AskItem.vue';
import FileTabs from '@/assets/file/tabs.json';
import FileCards from '@/assets/file/cards.json';
import FileQuestions from '@/assets/file/questions.json';


export default {
  name: 'App',
  data() {
    return {
      tabs: FileTabs.data,
      cards: FileCards.data,
      questions: FileQuestions.data,
      userMail: '',
      errorUserMail: false,
    }
  },
  methods: {
    sendMail(email) {
      if (/^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/.test(email)) {
          this.errorUserMail = false
      } else {
        this.errorUserMail = true
      }
    },
    answerAsk(payload) {
      console.log(payload.message)
      if (document.querySelector('.ask.activate')) {
        document.querySelector('.ask.activate').classList.remove('activate')
      }
        document.querySelector('.ask[data-id="'+payload.message+'"]').classList.add('activate')
    },
    goTab(payload) {
      document.querySelector('.n-tabs__link.active').classList.remove('active')
      document.querySelector('.n-tabs__link[data-id="'+payload.message+'"]').classList.add('active')
      document.querySelector('.t-tab.visible').classList.remove('visible')
      document.querySelector('.t-tab[data-id="'+payload.message+'"]').classList.add('visible')
    },
    openNav() {
      let nav = document.querySelector('.nav')
      if (nav.classList.contains('open')) {
        nav.classList.remove('open')
      } else {
        nav.classList.add('open')
      }
    },
    closeNav() {
      document.querySelector('.nav').classList.remove('open')
    }
  },
  components: {
    TabsContainer,
    TabsLinks,
    TabsItems,
    CardItem,
    AskItem
  }
}
</script>

<style src="@/assets/scss/app.scss" lang="scss"></style>