<template>
  <div class="content">
    <div class="hc">
      <a href="https://hackclub.com">
        <img
          src="https://assets.hackclub.com/flag-standalone.png"
          alt="Hack Club"
        />
      </a>
      <p>unofficial Hack Club YSWS grant calculator</p>
    </div>

    <slot />
  </div>
</template>

<style>
body {
  background-color: var(--ctp-mocha-base);
  color: var(--ctp-mocha-text);
}

.content {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.hc {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);

  display: flex;
  flex-direction: column;
  align-items: center;
}

.hc a {
  padding-top: 25vh;
}

.hc img {
  width: 128px;
  display: block;
}
</style>