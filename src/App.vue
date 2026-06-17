<template>
  <Experiment title="Perspective-taking experiment">
    <InstructionScreen :title="'Welcome'">
      Welcome to the experiment! You will first read a set of instructions. The instructions are divided into three parts. Please move to the next screen to read the first part.
    </InstructionScreen>

    <InstructionScreen :title="'Instructions'">
      In this experiment, you will play a game with another participant. You will play the role of the listener, while the other participant will play the role of the speaker. 

      <br><br>

      On each trial, you will see a grid containing four objects and a description above it. The description is produced by the speaker to indicate one of the objects in the grid. You will only be presented the speaker's description in written form, you won't hear it spoken aloud.
      
    </InstructionScreen>

    <InstructionScreen :title="'Instructions'">
      The speaker sees a slightly different version of the grid. Their grid contains only three objects because one cell is hidden by an occluder. In your grid, the speaker's occluded cell is shown as a grey cell. This means that the speaker cannot see the object in the grey cell. 

      <br><br>

      Apart from the hidden object, both grids contain the same objects. However, the position of the visible objects is shuffled across the two grids, so the speaker cannot use location words (e.g., "top left" or "bottom right") to refer to an object.
    
    </InstructionScreen>

    <InstructionScreen :title="'Instructions'">
      On the speaker's screen, one of the visible objects is marked with an asterisk (*). Their task is to describe that object. 
      
      <br><br>

      Your task is to use their description, which will appear above the grid, to determine which object they intended to refer to and select it.

      <br><br>

      At the end of the experiment, you will be asked to complete a short questionnaire.
  
    </InstructionScreen>

    <InstructionScreen :title="'Example'">

      <img
        src="instructions/example_view.png"
        style="width: 800px; max-width: 100%;"
      />

      <p>
        Example of the speaker's view (left) and your view (right).
        The grey cell indicates the object that is hidden from the speaker.
        The asterisk (*) marks the object that the speaker has to describe.
      </p>

      <p>
        During the experiment, you will only see the right view. The speaker's view is shown here only to illustrate how the game works.
        Your task is to click on the object that you think the speaker is referring to.
      </p>

    </InstructionScreen>

    <PracticeBlock :practiceTrials="practiceTrials" />

    <GridTrial
      v-for="trial in trials"
      :key="trial.id"
      :trial="trial"
    />

    <Questionnaire />

    <SubmitResultsScreen />
  </Experiment>
</template>

<script>
import _ from "lodash";
import trials from "./trials";
import PracticeBlock from "./PracticeBlock.vue";
import practiceTrials from "./PracticeTrials";
import GridTrial from "./GridTrial.vue";
import Questionnaire from "./Questionnaire.vue";

export default {
  name: "App",
  components: {
    GridTrial,
    PracticeBlock,
    Questionnaire
  },
  data() {
    return {
      trials,
      practiceTrials
    };
  },
  computed: {
    _() {
      return _;
    }
  }
};
</script>