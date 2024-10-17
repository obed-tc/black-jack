<script lang="ts">
  import Card from "../components/Card.svelte";

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
  ];

  let cartasGame = [...cartas];

  function getCardPlayer() {
    let randomIndex = Math.floor(Math.random() * cartasGame.length);
    cardSelected = cartasGame[randomIndex];
    cartasGame.splice(randomIndex, 1);
    cartasGame = [...cartasGame];

    console.log(`Carta seleccionada:`, cardSelected);
    console.log(`Cartas restantes:`, cartasGame);
  }
</script>

<div class=" bg-gray-200 min-h-screen">
  {cartas.length}
  <!-- <div class="flex">
        {#each cartas as carta }
        <Card  numberCard={carta.numberCard} sign={carta.sign}></Card>
        {/each}
    </div> -->

  {#if cardSelected}
    <Card
      numberCard={cardSelected.numberCard}
      sign={cardSelected.sign}
      reverse={true}
    ></Card>
  {/if}

  <br />

  <button
    class="bg-green-500 py-2 px-6 rounded-full text-white cursor-pointer absolute z-20"
    on:click={getCardPlayer}
  >
    Iniciar
    {cartasGame.length}
  </button>
</div>
