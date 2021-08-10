<script>
    import Modal from './Modal.svelte'

    let people = [
        {name: "peroson", beltColour: 'black', age: 25, id: 1},
        {name: "peroson1", beltColour: 'white', age: 45, id: 2},
        {name: "peroson2", beltColour: 'red', age: 35, id: 3},
    ];

    const handleClick = (id) => {
        people = people.filter((person) => person.id !== id)
    }

</script>

<Modal/>
<main>
    {#each people as person (person.id)}
        <div>
            {#if person.beltColour == 'black'}
                <p><strong>master ninja</strong></p>
            {/if}
            <h4>{person.name}</h4>
            <p>{person.age} years old, {person.beltColour} belt.</p>
            <button on:click={() => handleClick(person.id)}>Delete</button>
        </div>
    {:else}
        <p>No people to show</p>
    {/each}
</main>

<style>
    main {
        text-align: center;
        padding: 1em;
        max-width: 240px;
        margin: 0 auto;
    }

    @media (min-width: 640px) {
        main {
            max-width: none;
        }
    }
</style>