<script lang="ts">
  import { onMount } from "svelte";
  import Card from "../components/Card.svelte";
  import Footer from "../components/Footer.svelte";
  import Header from "../components/Header.svelte";
  import TableBlackJack from "../assets/images/table-black-jack.png";
  import { Cartas } from "../constanst/cartas";
  import Modal from "../components/Modal.svelte";
  let cardSelected: any = null;
  let cartas = Cartas;

  let cartasGame = [...cartas];
  let deeler: any[] = [];
  let player: any[] = [];
  let score: any[] = [];
  let deelerScore: any[] = [0, 0];
  let isRender = false;
  onMount(() => {
    distributeCards();
  });
  let isModalOpen = false;

  function openModal() {
    isModalOpen = true;
  }

  function closeModal() {
    isModalOpen = false;
    reset();
  }
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

  function getNear21(lista: any[]) {
    let x = lista[0];
    let y = lista[1];
    if (x <= 21 && y <= 21) {
      return 21 - x >= 21 - y ? y : x;
    }
    if (x > 21) {
      if (y > 21) {
        return 0;
      } else {
        return y;
      }
    } else {
      return y;
    }
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
      console.log("Perdiste");
      openModal();
    }
  }
  function stopPlayer() {
    console.log(deeler[1]);
    deeler[1].reverse = false;
    deeler = [...deeler];

    getScoreDeeler();

    for (let i = 0; i < 10; i++) {
      if (deelerScore[0] < 17) {
        addCardDeeler();
      } else {
        break;
      }
    }

    for (let i = 0; i < 10; i++) {
      let puntoTotalDeeler = getNear21(deelerScore);
      console.log("============");
      console.log(deelerScore);
      console.log(puntoTotalDeeler);
      console.log("============");

      if (puntoTotalDeeler < 17 && puntoTotalDeeler > 0) {
        addCardDeeler();
      } else if (puntoTotalDeeler == 0) {
        console.log("terminando for");
        break;
      } else {
        break;
      }
    }

    console.log("Punto deeler");
    console.log(getNear21(deelerScore));
    console.log("Punto jugador");

    console.log(getNear21(score));
    openModal();
  }
  function getWinner() {
    let datoPlayer = getNear21(score);
    let datoBot = getNear21(deelerScore);

    let player = 21 - datoPlayer;
    let bot = 21 - datoBot;

    if (player == 21) {
      return "Perdiste";
    }

    console.log("JAJAJAJ");
    console.log(21 - getNear21(score));
    console.log(bot);
    console.log(player);
    if (bot == player) {
      return "Empate";
    }

    if (bot < player && bot >= 0 && player >= 0) {
      return "Ganador Deeler";
    } else {
      return "Ganador Jugador";
    }
  }
  function reset() {
    deeler = [];
    player = [];
    score = [0, 0];
    deelerScore = [0, 0];
    isRender = false;
    distributeCards();
  }
  function render() {
    isRender = true;
    openModal();
  }
</script>

<div class=" bg-[#00493a] min-h-screen pt-[10vh] flex flex-col">
  <Modal isOpen={isModalOpen} {closeModal}>
    <div>
      <p>{isRender ? "Perdiste por rendición" : getWinner()}</p>
    </div>
  </Modal>

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
              : deelerScore[0] == deelerScore[1]
                ? deelerScore[0]
                : getNear21(deelerScore)}
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
          {score[0] == score[1] ? score[0] : score}
          {getNear21(score) == 0 ? "Perdiste" : ""}
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
          on:click={render}>Rendirse</button
        >
        <button
          class="bg-black uppercase font-bold px-6 py-3 rounded-lg text-white w-[12vw] h-[10vh] text-2xl"
          on:click={reset}>Nuevo</button
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
