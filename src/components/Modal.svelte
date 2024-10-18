<script>
  export let isOpen = false;
  export let closeModal = () => {};
</script>

{#if isOpen}
  <div
    class="fixed inset-0 z-50 flex items-center justify-center pt-[90px] bg-black bg-opacity-10"
  >
    <div
      class="bg-black bg-opacity-80 rounded-md shadow-lg w-full max-w-lg mx-4 p-2 relative"
    >
      <div class="flex flex-col justify-center items-center text-center">
        <h3
          class="text-3xl absolute mt-[-20px] w-full text-green-600 shadow-sm font-extrabold"
          style="-webkit-text-stroke: 1px black;"
        >
          RESULTADOS
        </h3>

        <!-- <button on:click={closeModal} class="text-gray-600 hover:text-gray-900">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-6 w-6"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </button> -->
      </div>

      <div class="modal-body text-xl text-white text-center font-semibold py-5">
        <slot />
      </div>

      <button
        class="bg-green-600 text-white px-4 py-2 rounded-md hover:bg-green-700 mt-[-10px] absolute ml-[45%]"
        on:click={closeModal}
      >
        OK
      </button>
      <!-- <div class="mt-4 flex justify-end">
        <button
          class="bg-yellow-500 text-white px-4 py-2 rounded-md hover:bg-gray-600 mr-2"
          on:click={closeModal}
        >
          Cancel
        </button>
        <button
          class="bg-blue-500 text-white px-4 py-2 rounded-md hover:bg-blue-600"
        >
          Confirm
        </button>
      </div> -->
    </div>
  </div>
{/if}
