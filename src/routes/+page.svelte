<script lang="ts">

  import { Info, Settings } from "@lucide/svelte";
</script>

<main class="flex place-content-center h-full w-full">
  <div class="flex flex-col w-72 h-full text-center place-content-center gap-4">
    <h1 class="text-5xl font-bold italic">grabagram</h1>
    <div class="w-full flex gap-2">
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
