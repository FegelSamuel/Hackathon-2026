<template>
    <div class="mt-10 font-secondary">

        <!-- UPLOAD SCREEN -->
        <div v-if="states[currState]=='upload'">
            <h1 class="w-full text-center font-bold text-2xl">UPLOAD EEG DATA</h1>
            <div class="flex flex-col items-center my-5 gap-3">
                <UFileUpload v-model="selectedFile" accept=".csv" label="Drop File Here (max 20MB)" class="w-96 min-h-48" />
                <SMButton text="SUBMIT" @click="submitCSV()"/>
            </div>
        </div>

        <!-- IN PROCESS SCREEN -->
        <div v-else-if="states[currState]=='processing'">
            <!-- <h1 class="w-full text-center font-bold text-2xl animation-pulse">PROCESSING DATA...</h1> -->
            <div class="my-5 w-full flex justify-center">
                <img src="https://media.tenor.com/boSsE56i-F8AAAAM/genshin-wish.gif" class="h-full w-full"></img>
            </div>
        </div>

        <!-- RESULTS SCREEN -->
        <div v-else-if="states[currState]=='results'">
            <h1 class="w-full text-center font-bold text-2xl">RESULTS</h1>
            <div class="w-full my-5 flex justify-center">
                <ResultsWindow />
            </div>
            <div class="h-96"></div>
            <!-- next steps buttons -->
            <div class="flex flex-row justify-center gap-3 delay-[2s] animate-window-fade-in">
                <SMButton text="EXPORT RESULT"/>
                <SMButton text="RESET" @click="reset()"/>
            </div>
        </div>  

        <!-- ERROR -->
         <div v-else>
            <h1 class="w-full text-center font-bold text-2xl">ERROR</h1>
            <div class="flex flex-row justify-center">
                <SMButton text="RESTART" @click="reset()"/>
            </div>
         </div>
    </div>
</template>

<script setup lang="ts">
import { ref } from "vue"

const max_file_size = 20 * 1024 * 1024
const states = ['upload', 'processing', 'results']
const currState = ref(0)
const selectedFile = ref<File | null>(null)


function submitCSV() {
    // validity checks
    console.log(selectedFile.value)
    if (selectedFile.value == null) {
        alert("Please upload a file.")
        return;
    }
    if (selectedFile.value.size > max_file_size) {
        alert("File too large. Please upload a smaller file.")
        return;
    }

    // give file to model

    // next step
    currState.value++;
    calculateData()
}

function calculateData() {
    const balls = ref(true)
  //simulate a 1 sec wait/buffer before data is ready to present
  setTimeout(() => {
    currState.value++;
  }, 4500)

}

function reset() {
    currState.value = 0;
    selectedFile.value = null;
}
</script>