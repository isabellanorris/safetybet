<template>
  <!-- component -->
  <div
    class="bg-blue-800 flex items-center justify-center p-4 max-w-50 mx-auto min-h-80"
  >
    <div v-if="step === 0" class="mx-auto w-full max-w-[550px] min-h-80">
      <div class="text-green-100 p-8">
        Before you start, we have a few questions to ensure you have an informed
        betting experience
      </div>
      <button
        class="hover:shadow-form rounded-md bg-[#6A64F1] py-3 px-8 text-base font-semibold text-green-100 outline-green-100"
        @click.prevent="next"
      >
        Enter
      </button>
    </div>
    <div v-if="step === 1" class="mx-auto w-full max-w-[550px] min-h-80">
      <div class="text-green-100 pb-8">
        Which of these are examples of high risk betting behaviours?
        <br />(Select 2)
      </div>
      <form>
        <div class="text-left text-green-100 pl-32">
          <input
            type="checkbox"
            id="option1"
            name="option1"
            value="option1"
            v-model="option1"
          />
          <label for="option1">
            Setting and sticking to limits of time and money</label
          ><br />
        </div>
        <div class="text-left text-green-100 pl-32">
          <input
            type="checkbox"
            id="option2"
            name="option2"
            value="option2"
            v-model="option2"
          />
          <label for="option2"> Gambling to earn money or escape problems</label
          ><br />
        </div>
        <div class="text-left text-green-100 pl-32">
          <input
            type="checkbox"
            id="option3"
            name="option3"
            value="option3"
            v-model="option3"
          />
          <label for="option4"> Knowing when to walk away</label><br />
        </div>
        <div class="text-left text-green-100 pl-32">
          <input
            type="checkbox"
            id="option4"
            name="option4"
            value="option4"
            v-model="option4"
          />
          <label for="option4"> Borrowing or stealing to fund gambling</label
          ><br />
        </div>
        <div>
          <button
            class="hover:shadow-form rounded-md bg-[#6A64F1] py-3 px-8 text-base font-semibold text-green-100 outline-green-100"
            @click.prevent="next"
          >
            Next
          </button>
        </div>
      </form>
    </div>
    <div v-if="step === 2" class="mx-auto w-full max-w-[550px] min-h-80">
      <div class="text-green-100 pb-8">
        If something has 2/1 odds, what is the chance of this outcome happening?
        <br />
        (Select 1)
      </div>
      <form>
        <div class="text-left text-green-100 pl-32">
          <input type="checkbox" value="odds1" v-model="percentage1" />
          <label for="odds1"> 50%</label><br />
        </div>
        <div class="text-left text-green-100 pl-32">
          <input type="checkbox" value="odds2" v-model="percentage2" />
          <label for="odds2"> 20%</label><br />
        </div>
        <div class="text-left text-green-100 pl-32">
          <input type="checkbox" value="odds3" v-model="percentage3" />
          <label for="odds3"> 33.3%</label><br />
        </div>
        <div class="text-left text-green-100 pl-32">
          <input type="checkbox" value="odds4" v-model="percentage4" />
          <label for="odds4"> 100%</label><br />
        </div>
        <button
          class="mx-auto hover:shadow-form rounded-md bg-[#6A64F1] px-8 text-base font-semibold text-green-100 outline-green-100"
          @click.prevent="next"
        >
          Next
        </button>
      </form>
    </div>
    <div v-if="step === 3" class="mx-auto w-full max-w-[550px] min-h-80">
      <div class="text-green-100 pb-8">
        Which of these odds have the lowest returns if you bet £1?<br />
        (Select 1)
      </div>
      <form>
        <div class="text-left text-green-100 pl-32">
          <input type="checkbox" value="odds1" v-model="odds1" />
          <label for="odds1"> 3/1</label><br />
        </div>
        <div class="text-left text-green-100 pl-32">
          <input type="checkbox" value="odds2" v-model="odds2" />
          <label for="odds2"> 7/1</label><br />
        </div>
        <div class="text-left text-green-100 pl-32">
          <input type="checkbox" value="odds3" v-model="odds3" />
          <label for="odds3"> 11/2</label><br />
        </div>
        <div class="text-left text-green-100 pl-32">
          <input type="checkbox" value="odds4" v-model="odds4" />
          <label for="odds4"> 9/2</label><br />
        </div>
        <button
          class="hover:shadow-form rounded-md bg-[#6A64F1] py-3 px-8 text-base font-semibold text-green-100 outline-green-100"
          @click.prevent="submit"
        >
          Finish
        </button>
      </form>
    </div>
    <div v-if="step === 5" class="mx-auto w-full max-w-[550px] min-h-80">
      <div class="text-green-100 p-8">
        Thank you for completing the quiz.<br />
        Please enjoy a safe betting experience!
      </div>
    </div>
    <div v-if="step === 6" class="mx-auto w-full max-w-[550px] min-h-80">
      <div class="text-green-100 pb-8">
        <div class="pb-1">
          Looks like you might want to learn more about betting odds!
        </div>
        <div class="pb-1">Here are some helpful links:</div>
        <a
          class="text-white font-bold hover:text-green-100"
          href="https://www.begambleaware.org/understanding-risks-gambling"
        >
          Understanding The Risks Of Gambling</a
        >
        <br />
        <a
          class="text-white font-bold hover:text-green-100"
          href="https://mybettingsites.co.uk/learn/betting-odds-explained/"
        >
          Betting Odds Explained</a
        >
        <br />
        <a
          class="text-white font-bold hover:text-green-100"
          href="https://www.timeform.com/betting/odds-calculator"
        >
          Odds Calculator</a
        >
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        step: 0,
        option1: undefined,
        option2: undefined,
        option3: undefined,
        option4: undefined,
        odds1: undefined,
        odds2: undefined,
        odds3: undefined,
        odds4: undefined,
        percentage1: undefined,
        percentage2: undefined,
        percentage3: undefined,
        percentage4: undefined,
      };
    },
    methods: {
      next() {
        this.step += 1;
      },
      submit() {
        if (
          !this.option1 &&
          !this.option3 &&
          this.option2 &&
          this.option4 &&
          this.percentage3 &&
          this.odds1
        ) {
          this.step = 5;
        } else {
          this.step = 6;
        }
      },
    },
  };
</script>
