<script lang="ts">
  import { onMount } from "svelte";
  import { Settings } from "@lucide/svelte";
  import { lastRetrievalDate, SettingsState } from "./state.svelte";

  let currentDate = new Date();
  let currentTime = currentDate.getTime();
  let countdown: number;

  onMount(() => {
    countdown = calculateRemainingTime()
    currentTime = setInterval(() => {
      countdown -= 1000; 
    }, 1000);
  });

  function calculateRemainingTime() {
    let delay: number;
    if (SettingsState.intervalType === "months") {
      currentDate.setMonth(currentDate.getMonth() === 0 ? 11 : currentDate.getMonth() - 1);
      return lastRetrievalDate - currentDate.getTime();
    } else if (SettingsState.intervalType === "weeks") {
      delay = 1000 * 60 * 60 * 24 * 7;
    } else {
      delay = 1000 * 60 * 60 * 24;
    }
    return lastRetrievalDate + delay - currentTime;
  }
</script>

<main class="flex place-content-center h-full w-full">
  <div class="flex flex-col w-full sm:w-96 h-full text-center place-content-center place-items-center gap-4 px-8">
    <h1 class="text-5xl font-bold italic">grabagram</h1>
    <div>
      <p>{Math.floor(countdown / (1000 * 60 * 60 * 24) % 7)} days</p>
      <p>{Math.floor(countdown / (1000 * 60 * 60) % 24)} hours</p>
      <p>{Math.floor(countdown / (1000 * 60) % 60)} minutes</p>
      <p>{Math.floor(countdown / 1000 % 60)} seconds</p>

    </div>
    <div class="w-3/4 flex gap-2">
      <button class="btn btn-primary flex-grow">Rot</button>
      <div class="tooltip tooltip-bottom" data-tip="Settings">
          <button class="btn btn-circle">
            <a href="/settings">
              <Settings />
            </a>
        </button>
      </div>
    </div>
  </div>
</main>

<style>

</style>
