<template>
  <div class="container">
    <div class="row">
      <div class="col-md-12 ml-auto mr-auto who-we-are">
        <div class="row">
          <div class="col-lg-6" id="about-container">
              <NuxtLink to="/privacy">
                Home page
             </NuxtLink>
            <h1 id="about">Who we are</h1>
            <p>Schoolahoop is here to help! We’re a free service that helps you discover more elementary school options based on what’s important for your child.</p>
            <p>Schoolahoop is in Beta and supports K-5th graders looking for elementary schools in Tarrant County only. We are just getting started and need your feedback. Thanks for helping us better serve local parents like you!</p>
          </div>
          <div class="col-lg-5 offset-lg-1" id="hoops-container">
            <!-- <img class="hoops" itemprop="image" itemscope itemtype="https://schema.org/image" src="/hoops.svg" style="width: 100%;" alt="Two 'O's from the Schoolahoop school finder logo with confetti"> -->
            <cld-image alt="Icon for school Quiz" publicId="hoops_faq.svg">
              <cld-transformation quality="auto" />
            </cld-image>
          </div>
        </div>
      </div>
    </div>

    <div class="row faq-section">
      <div class="col-md-12 ml-auto mr-auto">
        <h2 class="color-teal">FAQs</h2>
        <faq :qas="qas" />
      </div>
    </div>
  </div>
</template>

<script>
import Faq from "~/components/Faq";


export default {
  components: { Faq },
  head: {
    bodyAttrs: {
      class: "white-navbar faq-page",
    },
  },
  data() {
    return {
      qas: [
        {
          question: "How does Schoolahoop work?",
          answer:
            "Schoolahoop matches you with nearby schools that fit your child and family. Just take our brief quiz, and we’ll show you schools that most closely reflect your preferences and needs. Then we’ll put you in touch with your top matches so you can schedule a tour or ask questions.",
        },
        {
          question: "What regions does Schoolahoop serve?",
          answer:
            "Schoolahoop currently serves parents in Tarrant County, Texas. Would you like to see Schoolahoop in your area? ",
            type: "mailto"
        },
        {
          question: "What school districts does Schoolahoop cover?",
          answer:
            "Schoolahoop covers all school districts in Tarrant County including Aledo ISD, Arlington ISD, Azle ISD, Birdville ISD, Burleson ISD, Carroll ISD, Castleberry ISD, Crowley ISD, Eagle Mountain-Saginaw ISD, Everman ISD, Fort Worth ISD, Godley ISD, Grapevine-Colleyville ISD, Hurst-Euless-Bedford ISD, Keller ISD, Kennedale ISD, Lake Worth ISD, Mansfield ISD, Northwest ISD, and White Settlement ISD. If a district falls partially within Tarrant County, we cover the schools that fall within the county lines.",
        },
        {
          question: "What grades does Schoolahoop serve?",
          answer:
            "We currently have the capability of matching you with schools that serve kindergarten through fifth grade. Some of the schools we recommend may go beyond these grades. Still, we do not have the ability to match you with specific grades beyond elementary school at this time. We will be adding support to match you with 6-12th grades in the future.",
        },
        {
          question: "Why is “no spanking” an option when filling out the quiz?",
          answer:
            "19 US states, including Texas, allow corporal punishment in schools at the state level. Texas allows spanking in its public schools, and the rules vary by district.",
        },
        {
          question: 'What schools are included in Schoolahoop results?',
          answer: ' We match families with public charter schools, microschools, public virtual schools, charter virtual schools, private virtual schools, and hybrid private schools so they can discover as many great options for their child as possible. We plan to explore adding additional school types in the future.'
        },
        {
          question: "Which schools do you prioritize in your results?",
          answer:
            "Our algorithm is based solely on what you say matters to you in a school.",
        },
        {
          question:
            "The other school finders provide letter grades or school rankings. Why don’t you?",
          answer:
            "Data and numbers are important, but they don’t always tell us everything we need to know to make the best decision for our families.  Our approach prioritizes schools that most closely reflect what matters most to you when it comes to your child’s education, academic and otherwise.",
        },
        {
          question:
            "I see charter schools in my matches. Don’t they charge tuition?",
          answer:
            "All public charter schools in Texas are tuition-free and open-enrollment.",
        },
        {
          question:
            "Can Schoolahoop match me with childcare?",
          prefix:
          "No, but our partner ",
          linkText: "Best Place for Kids™",
          url :'https://bestplace4kids.com/',
          type: 'childcare'
        },
        {
          question: "How does Schoolahoop make money?",
          type: 'funding',
          prefix: 'Schoolahoop is a nonprofit service that’s supported by generous grants from',
          linkText:  "The Miles Foundation",
          url: "https://www.milesfdn.org/",
          secondLinkText: "Lincoln Studio",
          secondUrl: "https://joinlincoln.org/studio"
        },
        {
          id: 'es-lang',
          question: '¿Se ofrece español?',
          answer: 'Schoolahoop llegará pronto para nuestros amigos de habla español en Tarrant County.',
        },
      ],
    };
  },
  mounted() {
    this.$store.commit("viewConfig/showFooterOnMobile");
    this.repositionHoops();
    window.addEventListener("resize", this.repositionHoops);
    document
      .getElementsByClassName("topnav-container")[0]
      .removeAttribute("style");
  },
  methods: {
    repositionHoops() {
      let width = document.documentElement.clientWidth;
      let hoops = document.getElementById("hoops-container");
      let about_text = document.getElementById("about-container");
      if (width <= 991) {
        hoops.style.display = "none";
      } else {
        hoops.style.display = "block";
        hoops.parentNode.insertBefore(about_text, hoops);
      }
    },
  },
};
</script>

<style lang="scss">
.faq-page {
  h1,
  h2 {
    font-family: Nunito;
    font-size: 60px;
    font-weight: bold;
    font-stretch: normal;
    font-style: normal;
    line-height: normal;
    letter-spacing: normal;
    text-align: left;
    color: #4fc5d5;
    margin-left: 0;
    margin-top: 0;
    @media (min-width: 1500px) {
      font-size: 70px;
    }

    @media (max-width: 991px) {
      font-size: 40px;
    }
  }
  p {
    font-family: Nunito;
    font-size: 24px;
    font-weight: normal;
    font-stretch: normal;
    font-style: normal;
    line-height: normal;
    letter-spacing: normal;
    color: #25204f;
    opacity: 1;
    @media (min-width: 1500px) {
      font-size: 25px;
    }
    @media (max-width: 991px) {
      font-size: 16px;
    }
  }
  .who-we-are {
    padding: 0 100px;
    margin-top: 80px;
    margin-bottom: 100px;

    @media (max-width: 991px) {
      margin-top: 0;
      margin-bottom: 30px;
      padding: 0 20px;
    }
  }
  .hoops {
    margin-top: 40px;
    @media (max-width: 991px) {
      margin-bottom: 40px;
    }
    @media (max-width: 576px) {
      margin-top: 0;
    }
  }
  .faq-section {
    > .col-md-12 {
      padding-left: 10px;
      padding-right: 10px;
    }
    h1,
    h2 {
      margin-left: 80px;

      @media (max-width: 991px) {
        margin-left: 8px;
      }
    }
     h3{
      @media (min-width: 1500px) {
        font-size: 1.4rem;
       }
    }
  }

  @media (max-width: 600px) {
    .wrapper:not(.navbar--hidden) {
      padding-top: 80px;
    }
  }
}
</style>
