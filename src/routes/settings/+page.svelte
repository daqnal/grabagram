<script lang="ts">
    import { ChevronLeft } from "@lucide/svelte";
    import { SettingsState } from "../state.svelte";

    const themes: Array<string> = ["emerald", "night", "nord", "dracula"];

    function setThemeState(theme: string) {
        SettingsState.theme = theme;
        console.log(SettingsState.theme);
    }
</script>

<div class="flex w-full place-content-center">
    <div class="flex flex-col gap-2 w-full lg:w-1/2 p-8">
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
                <p>Theme</p>
                <div class="join" >
                    {#each themes as theme}
                        <input checked={theme === SettingsState.theme ? true : false} class="btn join-item" type="radio" name="theme-buttons" value={theme} aria-label={theme.charAt(0).toUpperCase() + theme.slice(1)} onclick={() => setThemeState(theme)}>
                    {/each}
               </div>
            </li>
            <li class="list-row flex place-content-between flex place-items-center">
                <p>Retrieval interval</p>
                <div class="flex gap-2">
                    <input type="number" class="input w-12" bind:value={SettingsState.intervalCount}>
                    <select class="select" bind:value={SettingsState.intervalType}>
                        <option value="days">days</option>
                        <option value="weeks">weeks</option>
                        <option value="months">months</option>
                    </select>
                </div>
            </li>
            <li class="list-row">
                <button class="btn btn-primary" onclick={() => console.log(SettingsState)}>Print settings to console</button>
            </li>
        </ul>
    </div>
</div>
