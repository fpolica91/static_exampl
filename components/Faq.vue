<template>
  <div class="faq">
    <ul class="faq__list">
      <li
        v-for="(qa, index) in qas"
        :id="qa.id"
        :key="index"
        class="faq__qa"
      >
        <h3 class="faq__question">
          Q: {{ qa.question }}
        </h3>
        <p class="faq__answer" v-if="!qa.type" >
          A: {{ qa.answer }}
        </p>

        <p v-if="qa.type === 'childcare'">
            A: {{qa.prefix}} <a :href="qa.url" target="_blank">{{qa.linkText}}</a> can!
        </p>

        <p v-if="qa.type === 'mailto'">
            A: {{qa.answer}} <a href="mailto:contact@schoolahoop.org">Contact us!</a>
        </p>

         <p v-if="qa.type === 'funding'">
            A: {{qa.prefix}} <a :href="qa.url" target="_blank">{{qa.linkText}}</a> and others donors to <a :href="qa.secondUrl" target="_blank">{{qa.secondLinkText}}</a>!
        </p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    qas: {
      type: Array,
      default: () => [],
    },
  },
}
</script>

<style lang="scss">
.faq {

  &__list {
    list-style: none;
    padding-left: 0;
  }

  &__qa {
    margin: 30px 0;
    background-color: white;
    padding: 30px;
    border-radius: 20px;
    -webkit-box-shadow: 5px 5px 26px 5px rgba(37,32,79,0.18);
    box-shadow: 5px 5px 26px 5px rgba(37,32,79,0.18);

    @media(min-width: 576px) {
      padding: 40px 80px 40px 80px;
    }
  }

  &__question {
    color: green;
    font-size: 1.3rem;
    font-weight: bold;
    margin-bottom: 40px;
  }

  &__answer {
    font-size: 1.1rem;
    opacity: 1;
    margin: 10px 0;
  }
}
</style>
