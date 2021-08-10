<script>
    import Modal from './Modal.svelte'

    let showModal = false;

    let people = [
        {name: "peroson", beltColour: 'black', age: 25, id: 1},
        {name: "peroson1", beltColour: 'white', age: 45, id: 2},
        {name: "peroson2", beltColour: 'red', age: 35, id: 3},
    ];

    const handleClick = (id) => {
        people = people.filter((person) => person.id !== id)
    }

    const toggleModal = () => {
        showModal = !showModal;
    }
</script>

<Modal message="Hey, I am a prop value" {showModal} on:click={toggleModal}/>
<main>
    <button on:click|once={toggleModal}>Open Modal</button>
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