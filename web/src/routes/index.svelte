<script>
  import fetch from 'cross-fetch';
  import { ApolloClient, HttpLink, InMemoryCache } from "@apollo/client/core";
  import { query, setClient } from "svelte-apollo";
  import successkid from 'images/successkid.jpg';
  import { Users } from '@/generated/graphql';

  const client = new ApolloClient({
    link: new HttpLink({ uri: 'http://localhost:3000/graphql', fetch }),
    cache: new InMemoryCache()
  });
  setClient(client);

  const users = query(Users);
</script>

<svelte:head>
  <title>Sapper project template</title>
</svelte:head>

<h1>Great success!</h1>

<figure>
  <img alt="Success Kid" src="{successkid}">
  <figcaption>Have fun with Sapper!</figcaption>
</figure>

<p><strong>Try editing this file (src/routes/index.svelte) to test live reloading.</strong></p>

{#if $users.loading}
  <p>
    Loading...
  </p>
{:else if $users.error}
  <p>
    Error
  </p>
{:else}
  <ul>
    {#each $users.data.users as user}
      <li>
        {user.name}
      </li>
    {/each}
  </ul>
{/if}

<style>
  h1, figure, p {
    text-align: center;
    margin: 0 auto;
  }

  h1 {
    font-size: 2.8em;
    text-transform: uppercase;
    font-weight: 700;
    margin: 0 0 0.5em 0;
  }

  figure {
    margin: 0 0 1em 0;
  }

  img {
    width: 100%;
    max-width: 400px;
    margin: 0 0 1em 0;
  }

  p {
    margin: 1em auto;
  }

  @media (min-width: 480px) {
    h1 {
      font-size: 4em;
    }
  }
</style>
