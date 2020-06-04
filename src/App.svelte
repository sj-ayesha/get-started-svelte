<script>
  import ContactCard from "./ContactCard.svelte";

  let name = "Ayesha";
  let title = "";
  let image = "";
  let description = "";
  let age = 24;
  let formState = "empty";

  let createdContacts = [];

  // Reactive Variables
  $: uppercaseName = name.toUpperCase();

  $: console.log(name);

  $: if (name === "Jownally") {
    console.log("it runs!");
    age = 25;
  }
  ///////////////////////////////////////

  function incrementAge() {
    age = age + 1;
  }

  function changeName() {
    name = "Jownally";
  }

  function nameInput(event) {
    const enteredValue = event.target.value;
    name = enteredValue;
  }

  function addContact() {
    if (
      name.trim().length == 0 ||
      title.trim().length == 0 ||
      image.trim().length == 0 ||
      description.trim().length == 0
    ) {
      formState = "invalid";
      return;
    }
    createdContacts = [
      ...createdContacts,
      {
		id: Math.random(),
        name: name,
        title: title,
        image: image,
        description: description
      }
    ];
    formState = "done";
  }

  function deleteFirst() {
	  createdContacts = createdContacts.slice(1);
  }

  function deleteLast() {
	  createdContacts = createdContacts.slice(0, -1);
  }
</script>

<style>
  h1 {
    color: #ff3e00;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }

  #form {
    width: 30rem;
    max-width: 100%;
  }
</style>

<main>
  <div id="form">
    <div class="form-control">
      <label for="username">Username</label>
      <input type="text" bind:value={name} id="username" />
    </div>

    <div class="form-control">
      <label for="jobTitle">Job Title</label>
      <input type="text" bind:value={title} />
    </div>

    <div class="form-control">
      <label for="imageSource">Image Url</label>
      <input type="text" bind:value={image} id="imageSource" />
    </div>

    <div class="form-control">
      <label for="description">Description</label>
      <textarea rows="3" bind:value={description} id="description" />
    </div>

    <button on:click={addContact}>Add Contact</button>
	<button on:click={deleteFirst}>Delete First</button>
	<button on:click={deleteLast}>Delete Last</button>
  </div>
  <!-- <h1>Hello {uppercaseName}, my age is {age}!</h1>
	<button on:click="{incrementAge}">Change Age</button> -->
  <!-- <button on:click="{changeName}">Change Name</button> -->

  <!--Binding to Element Properties-->
  <!-- <input type="text" value="{name}" on:input="{nameInput}"> -->
  <!----------------------------------------------------------->

  <!--Two Way Binding- change value of age when name is Jownally or only change name value-->
  <!-- <input type="text" bind:value="{name}">
	<input type="text" bind:value="{title}"> -->
  <!---Deeper into Bindings-->
  <!-- <input type="text" bind:value="{image}">
	<textarea rows="3" bind:value="{description}"></textarea> -->

  <!--conditional if statement-->
  <!--Props components-->
  {#if formState === 'invalid'}
    <p>Invalid input!</p>
  {:else}
    <p>Please add data</p>
  {/if}

	<!--For Each outputting list-->
	<!--contact.id will allow each element to have an id which will help to manipulate correct data & updating dom for initial data each time-->
  {#each createdContacts as contact, index (contact.id)}
  <!--else & index for counting functionality-->
  	<h2># {index + 1}</h2>
    <ContactCard
      username={contact.name}
      jobTitle={contact.title}
      description={contact.description}
      userImage={contact.image} />
	{:else}
		<p>Please add some contacts!</p>
  {/each}
</main>
