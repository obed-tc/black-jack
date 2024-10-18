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

<div class="carta-box shadow-lg w-[6.5vw] h-[20vh] {reverse ? 'rotar' : ''}">
  <div class="carta">
    <div class="cara">
      <div
        class="bg-white shadow-xl rounded-lg min-w-[6.5vw] max-w-[6.5vw] h-[20vh] p-1 flex flex-col"
      >
        <div class=" ">
          <p class="font-bold">{cards[numberCard]}</p>
          <img src={icono} class="w-[12px]" alt="" />
        </div>

        <div class="flex-1 flex justify-center">
          {#if numberCard <= 3}
            <div
              class="flex flex-col space-y-3 absolute mt-[-40px] h-full justify-center {numberCard ==
              1
                ? 'justify-center'
                : ''}"
            >
              {#each Array(numberCard) as _, index}
                <img
                  src={icono}
                  class={numberCard != 1 ? "w-[3vh]" : "w-[40px]"}
                  alt=""
                />
              {/each}
            </div>
          {/if}

          {#if numberCard >= 4 && numberCard < 10}
            <div class="flex h-full absolute items-center mt-[-40px]">
              <div class="flex flex-col space-y-3">
                {#each Array(parseInt((numberCard / 2).toString())) as _, index}
                  <img src={icono} class="w-[2.5vh]" alt="" />
                {/each}
              </div>
              {#if numberCard % 2 != 0}
                <img src={icono} class="w-[2.5vh] mx-[0.2vw]" alt="" />
              {/if}
              {#if numberCard % 2 == 0}
                <div class="w-[14px]"></div>
              {/if}
              <div class="flex flex-col space-y-3">
                {#each Array(parseInt((numberCard / 2).toString())) as _, index}
                  <img src={icono} class="w-[2.5vh]" alt="" />
                {/each}
              </div>
            </div>
          {/if}

          <div
            class="absolute flex flex-col justify-center mt-[-40px] h-full space-y-2"
          >
            {#if numberCard == 10}
              {#each Array(parseInt((numberCard / 4).toString())) as _, index}
                <div class="flex space-x-1">
                  <div class="flex flex-col space-y-3">
                    {#each Array(parseInt((numberCard / 4).toString())) as _, index}
                      <img src={icono} class="w-[2vh]" alt="" />
                    {/each}
                  </div>
                  {#if (numberCard / 2) % 2 != 0}
                    <img src={icono} class="w-[2vh]" alt="" />
                  {/if}
                  <div class="flex flex-col space-y-3">
                    {#each Array(parseInt((numberCard / 4).toString())) as _, index}
                      <img src={icono} class="w-[2vh]" alt="" />
                    {/each}
                  </div>
                </div>
              {/each}
            {/if}
          </div>

          <div class="h-full flex flex-col justify-between space-y-2">
            {#if numberCard >= 11}
              <div class="flex flex-col items-center justify-center">
                <p class="text-[18px] font-bold">{cards[numberCard]}</p>

                <img src={icono} class="w-[30px] -mt-1" alt="" />
              </div>
            {/if}
          </div>
        </div>

        <div class="  rotate-180">
          <p class="font-bold">{cards[numberCard]}</p>
          <img src={icono} class="w-[12px]" alt="" />
        </div>
      </div>
    </div>
    <div class="cara detras h-[20vh] w-[6.5vw]">
      <img src={Background} alt="" class="h-full w-full rounded-lg" />
    </div>
  </div>
</div>
