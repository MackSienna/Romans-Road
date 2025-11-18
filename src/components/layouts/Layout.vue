<script setup></script>

<template>
  <header>
    <h1 class="text-gradient">Romans Road</h1>
  </header>
  <main>
    <slot />
  </main>
  <footer>
    <small><b>Boatie</b></small>
    <a href="https://github.com/MackSienna" target="_blank">
      <img
        alt="Profile"
        src="https://avatars.githubusercontent.com/u/236309616?v=4"
      />
      <p>MackSienna</p>
      <i class="fa-regular fa-font-awesome"></i>
    </a>
  </footer>
</template>

<style scoped>
header,
footer,
main {
  padding: 1.5rem;
  width: 100%;
  max-width: 560px;
  margin: auto;
}

main {
  flex: 1;
}

footer {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  align-items: center;
  padding: 4rem 0;
  padding-bottom: 2rem;
}

footer a {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  padding: 0.2rem;
  padding-right: 0.8rem;
  background: var(--background-muted);
  border-radius: 3rem;
  border: 1px solid transparent;
  transition-duration: 400ms;
  text-decoration: none;
}

footer a:hover {
  border-color: var(--color-link);
}

footer a img {
  max-width: 110px;
  aspect-ratio: 1 / 1;
  border-radius: 100%;
}
</style>