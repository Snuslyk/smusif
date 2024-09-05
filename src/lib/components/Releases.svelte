<script lang="ts">
    import playIco from "$lib/assets/icons/stop.svg";
    import stopIco from "$lib/assets/icons/play.svg";
    import { createEventDispatcher, onMount } from 'svelte';

    export let releaseName: string;
    export let artistName: string;
    export let releaseImage: string;
    export let release: string;

    export let audioElement: HTMLAudioElement;
    let buttonIcon = stopIco;
    export let isPlaying: boolean = false;

    const dispatch = createEventDispatcher();

    $: buttonIcon = isPlaying ? playIco : stopIco;

    if (audioElement) {
        isPlaying ? audioElement.play() : audioElement.pause();
    }

    console.log(isPlaying)

    function toggleAudio() {
        if (audioElement) {
            if (audioElement.paused) {
                audioElement.play();
                isPlaying = true;
                dispatch('playState');
            } else {
                audioElement.pause();
                isPlaying = false;
                dispatch('stopState');
            }
        }
    }

    function resetAudio() {
        if (audioElement) {
            audioElement.currentTime = 0;
            audioElement.play();
            isPlaying = true;
            dispatch('playState');
        }
    }
</script>

<button
        class="release-card {isPlaying ? 'is-playing' : ''}"
        on:click
        on:dblclick={resetAudio}>
    <div class="left-part">
        <img src="{releaseImage}" alt="releaseImg">
        <div class="release-texts">
            <h3>{releaseName}</h3>
            <h4>{artistName}</h4>
        </div>
    </div>
    <div class="right-part">
        <img src="{buttonIcon}" alt="button-icon">
        <audio bind:this={audioElement}>
            <source src="{release}" type="audio/mp3">
        </audio>
    </div>
</button>

<style lang="scss">
  .release-card {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 15px 19px;
    width: 100%;
    background-color: #FFFFFF0A;
    border-radius: 20px;
    border: 1px solid rgba(255, 255, 255, 0.08);
    backdrop-filter: blur(24px);
    -webkit-backdrop-filter: blur(24px);
    cursor: pointer;
    transition: background-color 0.3s ease;

    &.is-playing {
      background-color: #FFFFFF00;
    }
  }

  .left-part {
    display: flex;

    img {
      width: 52px;
      border-radius: 113px;
      height: auto;
    }
  }

  .right-part {
    display: flex;
    padding-right: 16px;
  }

  .release-texts {
    display: flex;
    flex-direction: column;
    padding-left: 20px;

    h3 {
      font-weight: 450;
      font-size: 28px;
      line-height: 28px;
      margin-bottom: 4px;
      text-align: left;
    }

    h4 {
      font-weight: 400;
      font-size: 20px;
      line-height: 20px;
      opacity: 40%;
      text-align: left;
    }
  }
</style>
