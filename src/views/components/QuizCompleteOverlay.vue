<template>
  <div class="start">
    <!-- Info Box -->
    <div class="info_box">
      <div class="info_title">
        <span> Rules of YouCode Quiz </span>
      </div>
      <div class="info_list">
        <div class="info">
          1. You will have only <span>30 seconds</span> per each question.
        </div>
        <div class="info">
          2. Once you select your answer, you can't reselect.
        </div>
        <div class="info">
          3. You can't select any option once time goes off.
        </div>
        <div class="info">
          4. You can't exit from the Quiz while you're playing.
        </div>
        <div class="info">
          5. You'll get points on the basis of your correct answers.
        </div>
      </div>
      <div class="buttons">
        <button @click="$emit('showQuiz')" class="restart">Continue</button>
      </div>
    </div>
  </div>
</template>
<style>
.info_box {
  width: 540px;
  background: #fff;
  border-radius: 5px;
  /* pointer-events: none; */
  transform: translate(-50%, -50%) scale(0.9);
  transition: all 0.3s ease;
}
.info_box .info_title {
  height: 60px;
  width: 100%;
  border-bottom: 1px solid lightgray;
  display: flex;
  align-items: center;
  padding: 0 150px;
  font-size: 20px;
  font-weight: 600;
}
.info_box .info_list {
  padding: 15px 35px;
}
.info_box .info_list .info {
  margin: 5px 0;
  font-size: 17px;
}
.info_box .info_list .info span {
  font-weight: 600;
  color: rgb(84, 84, 231);
}
.info_box .buttons {
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  padding: 0 35px;
  border-top: 1px solid lightslategray;
}
.buttons button {
  margin: 0 5px;
  height: 40px;
  width: 100px;
  outline: none;
  border: 1px solid transparent;
  border-radius: 5px;
  color: #fff;
  font-size: 16px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
}

.buttons .restart {
  color: #fff;
  background: rgb(84, 84, 231);
}
.buttons .restart:hover {
  background: rgb(237, 237, 247);
  color: rgb(84, 84, 231);
  border-color: rgb(84, 84, 231);
}
</style>

<!-- <script>
export default {
    props: ['toggle'],
  

}


</script> -->
