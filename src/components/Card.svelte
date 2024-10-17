

<script>
// @ts-nocheck
import Trebol from "../assets/trebol.svg";
import Corazon from "../assets/Corazon.svg";
import Picas from "../assets/picas.svg";
import Diamante from "../assets/diamante.svg";
    export let numberCard;
    export let sign;
    // let numberCard=3;

    let icono=sign=="picas"?Picas:sign=="trebol"?Trebol:sign=="corazon"?Corazon:Diamante;
    let cards={

        1:"A",
        2:"2",
        3:"3",
        4:"4",
        5:"5",
        6:"6",
        7:"7",
        8:"8",
        9:"9",
        10:"10",
        11:"J",
        12:"Q",
        13:"K",

};
</script>

<div class="bg-white shadow-xl rounded-lg min-w-[15vw] max-w-[15vw] relative h-[50vh] p-3 flex flex-col">

    <div class=" ">
        <p  class="font-bold ml-1">{cards[numberCard]}</p>
        <img src={icono} class="w-[20px]" alt="">

    </div>
<div class="flex-1">
    {#if numberCard<=3}
        <div class="flex flex-col h-full items-center {numberCard==1?'justify-center':'justify-between'}">
            {#each Array(numberCard) as _,index}

            
        <img src={icono} class="{numberCard!=1?'w-[35px]':'w-[100px]'}" alt="">
            {/each}
        </div>
    {/if}

    {#if numberCard>=4 && numberCard<10}
    <div class="flex  h-full items-center justify-around px-5">
        <div class="flex flex-col justify-between h-full">
            {#each Array(parseInt((numberCard/2).toString())) as _,index}
        <img src={icono} class="w-[35px]" alt="">

        {/each}
        </div>
        {#if numberCard%2!=0}
        <img src={icono} class="w-[35px]" alt="">

        {/if}
        <div class="flex flex-col justify-between h-full">
        {#each Array(parseInt((numberCard/2).toString())) as _,index}
        <img src={icono} class="w-[35px]" alt="">

        {/each}
        </div>
    </div>
    {/if}

    <div class="h-full flex flex-col justify-between  space-y-7">

    {#if numberCard==10}
        {#each Array(parseInt((numberCard/4).toString())) as _,index}
            <div class="flex  h-full items-center justify-around px-5">
                <div class="flex flex-col justify-between h-full">
                    {#each Array(parseInt((numberCard/4).toString())) as _,index}
        <img src={icono} class="w-[35px]" alt="">

                {/each}
                </div>
                {#if (numberCard/2)%2!=0}
        <img src={icono} class="w-[35px]" alt="">

                {/if}
                <div class="flex flex-col justify-between h-full">
                {#each Array(parseInt((numberCard/4).toString())) as _,index}
        <img src={icono} class="w-[35px]" alt="">

                {/each}
                </div>
            </div>
        
        {/each}
    {/if}

{#if numberCard>=11}
<div class="flex flex-col items-center justify-center h-full">
    <p class="text-[50px] font-bold">{cards[numberCard]}</p>

    <img src={icono} class="w-[50px] -mt-1" alt="">
<!-- 
    {#if cards[numberCard]=="J"}
    <img src="" alt="J">
        
    {/if}
    {#if cards[numberCard]=="Q"}
    <img src="" alt="J">
        
    {/if}
    {#if cards[numberCard]=="K"}
    <img src="" alt="J">
        
    {/if} -->

</div>
    
{/if}
</div>


</div>

    <div class="  rotate-180 ">
        <p  class="font-bold ml-1">{cards[numberCard]}</p>
        <img src={icono} class="w-[20px]" alt="">

    </div>
</div>