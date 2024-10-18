<script lang="ts">
  import { onMount } from "svelte";
  import Card from "../components/Card.svelte";
  import Footer from "../components/Footer.svelte";
  import Header from "../components/Header.svelte";
  import TableBlackJack from "../assets/images/table-black-jack.png";

  let cardSelected: any = null;
  let cartas = [
    { numberCard: 1, sign: "trebol" },
    { numberCard: 2, sign: "trebol" },
    { numberCard: 3, sign: "trebol" },
    { numberCard: 4, sign: "trebol" },
    { numberCard: 5, sign: "trebol" },
    { numberCard: 6, sign: "trebol" },
    { numberCard: 7, sign: "trebol" },
    { numberCard: 8, sign: "trebol" },
    { numberCard: 9, sign: "trebol" },
    { numberCard: 10, sign: "trebol" },
    { numberCard: 11, sign: "trebol" }, // Sota
    { numberCard: 12, sign: "trebol" }, // Caballo
    { numberCard: 13, sign: "trebol" }, // Rey
    { numberCard: 1, sign: "diamante" },
    { numberCard: 2, sign: "diamante" },
    { numberCard: 3, sign: "diamante" },
    { numberCard: 4, sign: "diamante" },
    { numberCard: 5, sign: "diamante" },
    { numberCard: 6, sign: "diamante" },
    { numberCard: 7, sign: "diamante" },
    { numberCard: 8, sign: "diamante" },
    { numberCard: 9, sign: "diamante" },
    { numberCard: 10, sign: "diamante" },
    { numberCard: 11, sign: "diamante" }, // Sota
    { numberCard: 12, sign: "diamante" }, // Caballo
    { numberCard: 13, sign: "diamante" }, // Rey
    { numberCard: 1, sign: "corazon" },
    { numberCard: 2, sign: "corazon" },
    { numberCard: 3, sign: "corazon" },
    { numberCard: 4, sign: "corazon" },
    { numberCard: 5, sign: "corazon" },
    { numberCard: 6, sign: "corazon" },
    { numberCard: 7, sign: "corazon" },
    { numberCard: 8, sign: "corazon" },
    { numberCard: 9, sign: "corazon" },
    { numberCard: 10, sign: "corazon" },
    { numberCard: 11, sign: "corazon" }, // Sota
    { numberCard: 12, sign: "corazon" }, // Caballo
    { numberCard: 13, sign: "corazon" }, // Rey
    { numberCard: 1, sign: "diamante" },
    { numberCard: 2, sign: "diamante" },
    { numberCard: 3, sign: "diamante" },
    { numberCard: 4, sign: "diamante" },
    { numberCard: 5, sign: "diamante" },
    { numberCard: 6, sign: "diamante" },
    { numberCard: 7, sign: "diamante" },
    { numberCard: 8, sign: "diamante" },
    { numberCard: 9, sign: "diamante" },
    { numberCard: 10, sign: "diamante" },
    { numberCard: 11, sign: "diamante" }, // Sota
    { numberCard: 12, sign: "diamante" }, // Caballo
    { numberCard: 13, sign: "diamante" }, // Rey

    { numberCard: 1, sign: "trebol" },
    { numberCard: 2, sign: "trebol" },
    { numberCard: 3, sign: "trebol" },
    { numberCard: 4, sign: "trebol" },
    { numberCard: 5, sign: "trebol" },
    { numberCard: 6, sign: "trebol" },
    { numberCard: 7, sign: "trebol" },
    { numberCard: 8, sign: "trebol" },
    { numberCard: 9, sign: "trebol" },
    { numberCard: 10, sign: "trebol" },
    { numberCard: 11, sign: "trebol" }, // Sota
    { numberCard: 12, sign: "trebol" }, // Caballo
    { numberCard: 13, sign: "trebol" }, // Rey
    { numberCard: 1, sign: "diamante" },
    { numberCard: 2, sign: "diamante" },
    { numberCard: 3, sign: "diamante" },
    { numberCard: 4, sign: "diamante" },
    { numberCard: 5, sign: "diamante" },
    { numberCard: 6, sign: "diamante" },
    { numberCard: 7, sign: "diamante" },
    { numberCard: 8, sign: "diamante" },
    { numberCard: 9, sign: "diamante" },
    { numberCard: 10, sign: "diamante" },
    { numberCard: 11, sign: "diamante" }, // Sota
    { numberCard: 12, sign: "diamante" }, // Caballo
    { numberCard: 13, sign: "diamante" }, // Rey
    { numberCard: 1, sign: "corazon" },
    { numberCard: 2, sign: "corazon" },
    { numberCard: 3, sign: "corazon" },
    { numberCard: 4, sign: "corazon" },
    { numberCard: 5, sign: "corazon" },
    { numberCard: 6, sign: "corazon" },
    { numberCard: 7, sign: "corazon" },
    { numberCard: 8, sign: "corazon" },
    { numberCard: 9, sign: "corazon" },
    { numberCard: 10, sign: "corazon" },
    { numberCard: 11, sign: "corazon" }, // Sota
    { numberCard: 12, sign: "corazon" }, // Caballo
    { numberCard: 13, sign: "corazon" }, // Rey
    { numberCard: 1, sign: "diamante" },
    { numberCard: 2, sign: "diamante" },
    { numberCard: 3, sign: "diamante" },
    { numberCard: 4, sign: "diamante" },
    { numberCard: 5, sign: "diamante" },
    { numberCard: 6, sign: "diamante" },
    { numberCard: 7, sign: "diamante" },
    { numberCard: 8, sign: "diamante" },
    { numberCard: 9, sign: "diamante" },
    { numberCard: 10, sign: "diamante" },
    { numberCard: 11, sign: "diamante" }, // Sota
    { numberCard: 12, sign: "diamante" }, // Caballo
    { numberCard: 13, sign: "diamante" }, // Rey

    { numberCard: 1, sign: "trebol" },
    { numberCard: 2, sign: "trebol" },
    { numberCard: 3, sign: "trebol" },
    { numberCard: 4, sign: "trebol" },
    { numberCard: 5, sign: "trebol" },
    { numberCard: 6, sign: "trebol" },
    { numberCard: 7, sign: "trebol" },
    { numberCard: 8, sign: "trebol" },
    { numberCard: 9, sign: "trebol" },
    { numberCard: 10, sign: "trebol" },
    { numberCard: 11, sign: "trebol" }, // Sota
    { numberCard: 12, sign: "trebol" }, // Caballo
    { numberCard: 13, sign: "trebol" }, // Rey
    { numberCard: 1, sign: "diamante" },
    { numberCard: 2, sign: "diamante" },
    { numberCard: 3, sign: "diamante" },
    { numberCard: 4, sign: "diamante" },
    { numberCard: 5, sign: "diamante" },
    { numberCard: 6, sign: "diamante" },
    { numberCard: 7, sign: "diamante" },
    { numberCard: 8, sign: "diamante" },
    { numberCard: 9, sign: "diamante" },
    { numberCard: 10, sign: "diamante" },
    { numberCard: 11, sign: "diamante" }, // Sota
    { numberCard: 12, sign: "diamante" }, // Caballo
    { numberCard: 13, sign: "diamante" }, // Rey
    { numberCard: 1, sign: "corazon" },
    { numberCard: 2, sign: "corazon" },
    { numberCard: 3, sign: "corazon" },
    { numberCard: 4, sign: "corazon" },
    { numberCard: 5, sign: "corazon" },
    { numberCard: 6, sign: "corazon" },
    { numberCard: 7, sign: "corazon" },
    { numberCard: 8, sign: "corazon" },
    { numberCard: 9, sign: "corazon" },
    { numberCard: 10, sign: "corazon" },
    { numberCard: 11, sign: "corazon" }, // Sota
    { numberCard: 12, sign: "corazon" }, // Caballo
    { numberCard: 13, sign: "corazon" }, // Rey
    { numberCard: 1, sign: "diamante" },
    { numberCard: 2, sign: "diamante" },
    { numberCard: 3, sign: "diamante" },
    { numberCard: 4, sign: "diamante" },
    { numberCard: 5, sign: "diamante" },
    { numberCard: 6, sign: "diamante" },
    { numberCard: 7, sign: "diamante" },
    { numberCard: 8, sign: "diamante" },
    { numberCard: 9, sign: "diamante" },
    { numberCard: 10, sign: "diamante" },
    { numberCard: 11, sign: "diamante" }, // Sota
    { numberCard: 12, sign: "diamante" }, // Caballo
    { numberCard: 13, sign: "diamante" }, // Rey
  ];

  let cartasGame = [...cartas];
  let deeler: any[] = [];
  let player: any[] = [];
  let score: any[] = [];
  let deelerScore: any[] = [0, 0];

  onMount(() => {
    distributeCards();
  });
  function getCard() {
    let randomIndex = Math.floor(Math.random() * cartasGame.length);
    cardSelected = cartasGame[randomIndex];
    cartasGame.splice(randomIndex, 1);
    cartasGame = [...cartasGame];
    return cardSelected;
  }

  function distributeCards() {
    player.push({ card: getCard(), reverse: false });
    player.push({ card: getCard(), reverse: false });
    player = [...player];
    deeler.push({ card: getCard(), reverse: false });
    deeler.push({ card: getCard(), reverse: true });
    deeler = [...deeler];
    getScorePlayer();
  }

  function addCardPlayer() {
    player.push({ card: getCard(), reverse: false });
    player = [...player];
    getScorePlayer();
  }
  function addCardDeeler() {
    deeler.push({ card: getCard(), reverse: false });
    deeler = [...deeler];
    getScoreDeeler();
  }
  function getScorePlayer() {
    score = [0, 0];
    player.map((item) => {
      console.log(item.card.numberCard);
      let number = item.card.numberCard;

      if (number >= 10) {
        score[0] += 10;
        score[1] += 10;
      } else if (number == 1) {
        score[0] += 11;
        score[1] += 1;
      } else {
        score[0] += item.card.numberCard;
        score[1] += item.card.numberCard;
      }
    });
    score = score;
    getResult();
  }
  function getScoreDeeler() {
    deelerScore = [0, 0];
    deeler.map((item) => {
      console.log(item.card.numberCard);
      let number = item.card.numberCard;

      if (number >= 10) {
        deelerScore[0] += 10;
        deelerScore[1] += 10;
      } else if (number == 1) {
        deelerScore[0] += 11;
        deelerScore[1] += 1;
      } else {
        deelerScore[0] += item.card.numberCard;
        deelerScore[1] += item.card.numberCard;
      }
    });
    deelerScore = deelerScore;
  }

  function getResult() {
    if (score[0] > 21 && score[1] > 21) {
      alert("Perdiste");
    }
  }
  function stopPlayer() {
    console.log(deeler[1]);
    deeler[1].reverse = false;
    deeler = [...deeler];

    getScoreDeeler();
    for (let i = 0; i < 10; i++) {
      if (deelerScore[0] <= 17) {
        addCardDeeler();
      } else {
        return;
      }
    }
  }
  function reset() {
    deeler = [];
    player = [];
    score = [0, 0];
    deelerScore = [0, 0];
    distributeCards();
  }
</script>

<div class=" bg-[#00493a] min-h-screen pt-[10vh] flex flex-col">
  <Header></Header>

  <main class="flex-1 flex flex-col items-center">
    <!-- <img src={TableBlackJack} alt="" class="w-[70vw] relative z-0" /> -->
    <div class="absolute flex flex-col justify-center">
      <img src={TableBlackJack} alt="" class="w-[75vw] z-0 relative" />
      <p
        class="absolute text-green-800 text-2xl z-20 top-20 w-full text-center font-semibold"
      >
        Black Jack
      </p>
      <!-- Contenido dentro del div -->
    </div>

    <div class="absolute z-20 flex flex-col justify-between h-[86vh]">
      <!-- <p class="text-white text-xl">
        Tu puntaje: {score}
      </p>
      {#if deeler[0]}
        <p class="text-white text-xl">
          Puntaje mesa: {deelerScore[0] == 0 && deelerScore[1] == 0
            ? deeler[0].card.numberCard
            : deelerScore}
        </p>
      {/if} -->

      <!-- {cartas.length} -->

      <div class="flex flex-col justify-center items-center">
        <div class="flex space-x-3 mt-20 justify-center">
          {#each deeler as carta}
            <Card
              numberCard={carta.card.numberCard}
              sign={carta.card.sign}
              reverse={carta.reverse}
            ></Card>
          {/each}
        </div>

        {#if deeler[0]}
          <p class="text-white text-3xl font-semibold">
            {deelerScore[0] == 0 && deelerScore[1] == 0
              ? deeler[0].card.numberCard
              : deelerScore}
          </p>
        {/if}
      </div>

      <div class="flex flex-col space-y-4 items-center">
        <div class="flex space-x-2">
          {#each player as carta}
            <Card
              numberCard={carta.card.numberCard}
              sign={carta.card.sign}
              reverse={carta.reverse}
            ></Card>
          {/each}
        </div>

        <p class="text-white text-3xl font-semibold">
          {score}
        </p>
      </div>
      <!-- {#if cardSelected}
        <Card
          numberCard={cardSelected.numberCard}
          sign={cardSelected.sign}
          reverse={true}
        ></Card>
      {/if} -->
    </div>

    <div
      class=" bg-black bg-opacity-30 py-3 absolute bottom-0 w-full flex justify-between px-[5vw]"
    >
      <div class="flex space-x-5">
        <button
          class="bg-black uppercase font-bold px-6 py-3 rounded-lg text-white w-[12vw] h-[10vh] text-2xl"
          on:click={stopPlayer}>Parar</button
        >
        <button
          class="bg-black uppercase font-bold px-6 py-3 rounded-lg text-white w-[12vw] h-[10vh] text-2xl"
          on:click={addCardPlayer}>Pedir</button
        >
      </div>
      <div class="flex space-x-5">
        <button
          class="bg-black uppercase font-bold px-6 py-3 rounded-lg text-white w-[12vw] h-[10vh] text-2xl"
          on:click={addCardPlayer}>Rendirse</button
        >
        <button
          class="bg-black uppercase font-bold px-6 py-3 rounded-lg text-white w-[12vw] h-[10vh] text-2xl"
          on:click={reset}>Empezar</button
        >
      </div>
    </div>
    <!-- <button
      class="bg-green-500 py-2 px-6 rounded-full text-white cursor-pointer absolute z-20"
      on:click={distributeCards}
    >
      Iniciar
      {cartasGame.length}
    </button> -->
  </main>
  <!-- <Footer></Footer> -->
</div>
