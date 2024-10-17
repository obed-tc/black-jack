<script>
  import SoundOn from "../assets/icons/sound-on.svg";
  import SoundOff from "../assets/icons/sound-off.svg";
  import Profile from "../assets/icons/profile.svg";
  import Setting from "../assets/icons/setting.svg";
  import Support from "../assets/icons/support.svg";
  import Store from "../assets/icons/store.svg";

  let soundActive = false;
  function changeSound() {
    soundActive = !soundActive;
  }
</script>

<header
  class=" absolute top-0 bg-black bg-opacity-20 w-full px-10 h-[10vh] flex items-center justify-between text-white"
>
  <h1 class="font-bold text-2xl">BLACK JACK</h1>
  <div class="flex">
    <button on:click={changeSound}>
      {#if soundActive}
        <img src={SoundOn} class="w-10" alt="" />
      {/if}
      {#if !soundActive}
        <img src={SoundOff} class="w-10" alt="" />
      {/if}
    </button>

    <button>
      <img src={Profile} class="w-10" alt="" />
    </button>

    <button>
      <img src={Setting} class="w-10" alt="" />
    </button>

    <button>
      <img src={Support} class="w-10" alt="" />
    </button>

    <button>
      <img src={Store} class="w-10" alt="" />
    </button>
  </div>
</header>
