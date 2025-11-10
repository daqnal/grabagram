<script>
  import { ChevronLeft } from "@lucide/svelte";

    
</script>

<div class="flex w-full place-content-center">
    <div class="flex flex-col gap-2 w-1/2 py-8">
        <div class="flex gap-2 place-items-center">
            <div class="tooltip tooltip-bottom" data-tip="Return to main page">
                <button class="btn btn-circle">
                    <a href="/">
                        <ChevronLeft />
                    </a>
                </button>
            </div>
            <h1 class="text-2xl font-bold">Settings</h1>
        </div>
        <ul class="list bg-base-100 rounded-box shadow-lg">
            <li class="list-row flex place-content-between flex place-items-center">
                <span>Theme</span>
                <div class="join">
                    <input class="btn join-item" type="radio" name="theme-buttons" value="emerald" aria-label="Emerald">
                    <input class="btn join-item" type="radio" name="theme-buttons" value="night" aria-label="Night">
                    <input class="btn join-item" type="radio" name="theme-buttons" value="nord" aria-label="Nord">
                    <input class="btn join-item" type="radio" name="theme-buttons" value="dracula" aria-label="Dracula">
                </div>
            </li>
        </ul>
    </div>
</div>