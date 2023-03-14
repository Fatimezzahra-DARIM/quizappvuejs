<template>
  <main class="flex h-screen items-center justify-center bg-gray-100">
    <!-- Quiz container -->
    <div
      class="bg-white flex-none container relative shadow-lg rounded-lg px-12 py-6"
    >
      <!-- <img src="@/assets/images/backgrounquiz.avif" alt="" class="absolute top-0 left-0" /> -->
      <!-- Contents -->
      <div class="relative z-20">
        <!-- Score container -->
        <div class="text-right text-gray-800">
          <p class="text-sm loading-3">Score</p>
          <p class="font-bold">60</p>
        </div>
        <!-- <p>para Test</p> -->
        <!-- Timer container -->
        <div class="bg-white shadow-lg p-1 rounded-full w-full h-5 mt-4">
          <div class="bg-blue-700 rounded-full w-11/12 h-full"></div>
        </div>
        <!-- Question container  -->
        <div
          class="rounded-lg bg-gray-100 p-2 neumorph-1 text-center font-bold text-gray-800 mt-8"
        >
          <div class="bg-white p-5">{{ currentQuestion.question }}</div>
        </div>
        <!-- Options container 
        <div class="mt-8">
           Option container 
          <div class="neumorph-1 bg-gray-100 p-2 rounded-lg">
            <div class="bg-white rounded-lg font-bold flex p-2">
               option ID 
              <div class="bg-gray-400 p-3 rounded-lg">A</div>
               option name 
              <div class="flex items-center pl-6">Fatime</div>
            </div>
          </div>
        </div> -->
        <!-- Options container
        <div class="mt-8">
          Option container
          <div class="neumorph-1 bg-gray-100 p-2 rounded-lg">
            <div class="bg-red-600 rounded-lg font-bold flex p-2 text-white">
              option ID
              <div class="bg-gray-800 p-3 rounded-lg">B</div>
              option name
              <div class="flex items-center pl-6">ezzahra</div>
            </div>
          </div>
        </div> -->
        <!-- Options container -->
        <div class="mt-8">
          <!-- Option container -->
          <div v-for="(choice, item) in currentQuestion.choices" :key="item">
            <div
              class="neumorph-1 option-default bg-gray-100 p-2 rounded-lg relative"
              :ref="optionChosen"
              @click="onOptionClicked(choice, item)"
            >
              <div
                class="bg-blue-700 p-1 transform rotate-45 rounded-md h-10 w-10 text-white font-bold absolute right-0 top-0 shadow-md"
              >
                <p class="transform -rotate-45">+10</p>
              </div>
              <div class="rounded-lg font-bold flex p-2">
                <!-- option ID -->
                <div class="p-3 rounded-lg">{{ item }}</div>
                <!-- option name -->
                <div class="flex items-center pl-6">{{ choice }}</div>
              </div>
            </div>
          </div>
        </div>

        <!-- Options container 
        <div class="mt-8">
           Option container 
          <div class="neumorph-1 bg-gray-100 p-2 rounded-lg">
            <div class="bg-white rounded-lg font-bold flex p-2">
               option ID 
              <div class="bg-gray-400 p-3 rounded-lg">D</div>
               option name 
              <div class="flex items-center pl-6">best</div>
            </div>
          </div>
        </div> -->
        <!-- Progress indicator container -->
        <div class="mt-8 text-center">
          <div class="h-1 w-12 bg-gray-800 rounded-full mx-auto"></div>
          <p class="font-bold text-gray-800">2/10</p>
        </div>
      </div>
    </div>
  </main>
</template>
<style scoped>
.neumorph-1 {
  box-shadow: 6px 6px 18px rgba(0, 0, 0, 0.09), -6px -6px 18px #fff;
}
.container {
  max-width: 400px;
  border-radius: 25px;
  background-image: url(@/assets/images/backgrounquiz.avif);
}
</style>

<script>
import { onMounted, ref } from "vue";
export default {
  setup() {
    //data
    let questionCounter = ref(0);
    const currentQuestion = ref({
      question: "",
      answer: 1,
      choices: [],
    });
    const questions = [
      {
        question: "what's your name?",
        answer: 2,
        choices: ["A", "b", "c", "D"],
      },
      {
        question: "what's your name?",
        answer: 1,
        choices: ["E", "F", "G", "H"],
      },
      {
        question: "what's your name?",
        answer: 3,
        choices: ["1", "2", "3", "4"],
      },
    ];
    const onQuizStart = () => {
      currentQuestion.value = questions[questionCounter.value];
    };
    //methods/functions
    let itemsRef = [];
    const optionChosen = (element) => {
      if (element) {
        itemsRef.push(element);
      }
    };
    const onOptionClicked = (choice, item) => {
      // console.log(itemsRef[item]);
      const divContainer = itemsRef[item];
      const optionID = item + 1;
      if (currentQuestion.value.answer == optionID) {
        console.log("y r correct");
        divContainer.classList.add("option-correct");
        divContainer.classList.remove("option-default");
      } else {
        console.log("y r wrong");
        divContainer.classList.add("option-wrong");
        divContainer.classList.remove("option-default");
      }
      console.log(choice, item);
    };
    //lifecycle hooks
    onMounted(() => {
      onQuizStart();
    });
    //return
    return {
      currentQuestion,
      questions,
      questionCounter,
      onQuizStart,
      onOptionClicked,
      optionChosen,
    };
  },
};
</script>
