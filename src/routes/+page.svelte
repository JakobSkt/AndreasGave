<script>
    let start = false;
    let showGift = false;
    let nameCleared = false;
    let nope = false;
    let name = "";

    function checkName() {
    if (name == "Andreas" || name == "andreas") {
            nameCleared = true
        } else {
            nope = true;
            alert("Det er vist ikke din gave 🚩🚩");
        }
    }

</script>

<main>
    {#if !start}
    
    <div class="btnContainer"> 
        <button class="open" on:click={() => start = true}> GÅ TIL GAVE </button>
    </div>

    <img src="./images/Forside.png">
    {:else}
        {#if showGift}
            <img src="./images/Gave.png" alt="Gavekort">
        {:else}
            {#if nope}
                <img src="./images/nope.jpg" alt="nope">
            {/if}
            <div class="questionContainer">
                <div class="question">
                    <h2> Hvad er dit navn? </h2>
                    <input bind:value={name}>
                    <button class="next" on:click={() => checkName()}> Fortsæt </button>
                    {#if nameCleared}
                        <button class="gift" on:click={() => showGift = true}> ÅBEN GAVE </button>
                    {/if}
                </div>
            </div>
           
        {/if}

    {/if}
</main>


<style>
    * { 
        margin: 0;
        padding: 0;
        font-family: "League Spartan";

    }

    img {
        display: block;
        height: 100vh;
        width: 100vw;
        z-index: 1;
    }

    .open {
        outline: none;
        border: none;
        padding: 5px 25px;
        border-radius: 10px;
        background-color: #0CC0DF;
        color: white;
        font-size: 1.75em;
        box-shadow: 0px 2px 6px rgb(193, 193, 193);
    }

    .btnContainer {
        position: fixed;
        z-index: 5!important;
        top: 50vh;
        left: 25vw;
    }

    .questionContainer {
        height: 100vh;
        width: 100vw;
        background: #0CC0DF;
        color: white;

    }

    .question {
        margin: auto;
        width: 75vw;
        position: absolute;
        top: 50vh;
        left: 12vw;
        text-align: center;
    }

    input {
        outline: none; 
        border: none;
        border-radius: 20px;
        padding: 10px;
        text-align: center;
    }

    .next {
        margin-top: 15px;
        outline: none;
        border: none;
        padding: 5px 15px;
        border-radius: 10px;
        background-color: white;
        color: #0CC0DF;
        font-size: 1em;
    }

    .gift {
        margin-top: 25px;
        outline: none;
        border: none;
        padding: 5px 15px;
        border-radius: 10px;
        background-color: #ffa800;
        color: white;
        font-size: 2em;
    }
</style>
