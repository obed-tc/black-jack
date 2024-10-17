<script>
  // @ts-nocheck
  import Trebol from "../assets/trebol.svg";
  import Corazon from "../assets/corazon.svg";
  import Picas from "../assets/picas.svg";
  import Diamante from "../assets/diamante.svg";
  import Background from "../assets/background-card.jpg";

  import "../styles/card-style.css";
  export let numberCard;
  export let sign;
  export let reverse;
  // let numberCard=3;

  let icono =
    sign == "picas"
      ? Picas
      : sign == "trebol"
        ? Trebol
        : sign == "corazon"
          ? Corazon
          : Diamante;
  let cards = {
    1: "A",
    2: "2",
    3: "3",
    4: "4",
    5: "5",
    6: "6",
    7: "7",
    8: "8",
    9: "9",
    10: "10",
    11: "J",
    12: "Q",
    13: "K",
  };

  function girarCarta() {
    const cartaBox = document.querySelector(".carta-box");
    cartaBox.classList.toggle("rotar");
  }
</script>

<button on:click={girarCarta}> Girar </button>
<div class="carta-box w-[15vw] h-[50vh] {reverse ? 'rotar' : ''}">
  <div class="carta">
    <div class="cara">
      <div
        class="bg-white shadow-xl rounded-lg min-w-[15vw] max-w-[15vw] h-[50vh] p-3 flex flex-col"
      >
        <div class=" ">
          <p class="font-bold ml-1">{cards[numberCard]}</p>
          <img src={icono} class="w-[20px]" alt="" />
        </div>
        <div class="flex-1">
          {#if numberCard <= 3}
            <div
              class="flex flex-col h-full items-center {numberCard == 1
                ? 'justify-center'
                : 'justify-between'}"
            >
              {#each Array(numberCard) as _, index}
                <img
                  src={icono}
                  class={numberCard != 1 ? "w-[35px]" : "w-[100px]"}
                  alt=""
                />
              {/each}
            </div>
          {/if}

          {#if numberCard >= 4 && numberCard < 10}
            <div class="flex h-full items-center justify-around px-5">
              <div class="flex flex-col justify-between h-full">
                {#each Array(parseInt((numberCard / 2).toString())) as _, index}
                  <img src={icono} class="w-[35px]" alt="" />
                {/each}
              </div>
              {#if numberCard % 2 != 0}
                <img src={icono} class="w-[35px]" alt="" />
              {/if}
              <div class="flex flex-col justify-between h-full">
                {#each Array(parseInt((numberCard / 2).toString())) as _, index}
                  <img src={icono} class="w-[35px]" alt="" />
                {/each}
              </div>
            </div>
          {/if}

          <div class="h-full flex flex-col justify-between space-y-7">
            {#if numberCard == 10}
              {#each Array(parseInt((numberCard / 4).toString())) as _, index}
                <div class="flex h-full items-center justify-around px-5">
                  <div class="flex flex-col justify-between h-full">
                    {#each Array(parseInt((numberCard / 4).toString())) as _, index}
                      <img src={icono} class="w-[35px]" alt="" />
                    {/each}
                  </div>
                  {#if (numberCard / 2) % 2 != 0}
                    <img src={icono} class="w-[35px]" alt="" />
                  {/if}
                  <div class="flex flex-col justify-between h-full">
                    {#each Array(parseInt((numberCard / 4).toString())) as _, index}
                      <img src={icono} class="w-[35px]" alt="" />
                    {/each}
                  </div>
                </div>
              {/each}
            {/if}

            {#if numberCard >= 11}
              <div class="flex flex-col items-center justify-center h-full">
                <p class="text-[50px] font-bold">{cards[numberCard]}</p>

                <img src={icono} class="w-[50px] -mt-1" alt="" />
              </div>
            {/if}
          </div>
        </div>

        <div class="  rotate-180">
          <p class="font-bold ml-1">{cards[numberCard]}</p>
          <img src={icono} class="w-[20px]" alt="" />
        </div>
      </div>
    </div>
    <div class="cara detras h-[50vh]">
      <img src={Background} alt="" class="h-full w-full rounded-lg" />
    </div>
  </div>
</div>
