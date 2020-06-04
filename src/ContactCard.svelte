<script>
    export let username;
    export let jobTitle;
    export let description;
    export let userImage;

    const initialName = username;
</script>
<style>
	.contact-card {
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
        max-width: 30rem;
        border-radius: 5px;
        margin: 1rem 0;
    }

    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .thumb {
        width: 33%;
        height: 100%;
    }

    .thumb-placeholder {
        background-color: #ccc
    }

    img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    .user-data {
        width: 67%;
        display: flex;
        flex-direction: column;
        justify-content: center;
    }

    h1 {
        font-size: 1.25rem;
        font-family: "Roboto Slab", sans-serif;
    }

    h2 {
        font-size: 1rem;
        font-weight: normal;
        color: #5a5a5a;
    }

    .description {
        border-top: 1px solid #ccc;
        padding: 1rem;
    }
</style>

<div class="contact-card">
  <header>
    <!--Dynamic css classes-->
    <div class="thumb" class:thumb-placeholder="{!userImage}">
        <img src="{userImage}" alt="{username}">
    </div>

    <div class="user-data">
      <h1>{username} / {initialName}</h1>
      <h2>{jobTitle}</h2>
    </div>
  </header>
  <div class="description">
    <!--Outputting html e.g <strong>-->
    <p>{@html description}</p>
  </div>
</div>
