
<template>
    <div class="pl-2 pt-2 absolute">
      <div class="inline text-white/100 font-mono text-xs" id="logTerminalBackground">
        <p>aaa</p>
      </div>
    </div>
</template>


<style>
  .logClass {
    opacity: 100;
  }
  .logClass.fade-out {
    opacity: 0;
    transition: opacity 0.2s ease;
  }
</style>

<script lang:ts>
  let log1,
    log2,
    log3,
    log4 = '';
  let container;

  function createElement() {
    const element = document.createElement('div');
    element.textContent = `${log4}`;
    element.setAttribute('class', 'logClass');
    element.setAttribute('id', 'logID');
    container.appendChild(element);

    const observer = new IntersectionObserver((entries) => {
      if (entries[0].intersectionRatio <= 0) {
        removeElements(container);
        observer.disconnect();
      }
    });
    observer.observe(element);
  }

  function removeElements(container) {
    let elements = Array.from(container.children);
    elements.forEach((element) => {
      element.addEventListener('transitionend', () =>{
        container.removeChild(element);
      }, {once: true});
      element.classList.add('fade-out');
    });
  }

  function handleKeydown(e) {
      arrowConverter(e);
      createElement();
  }

  function arrowConverter(e) {
      log1 = 'input.keyboard(';
      log2 = e.keyCode;

      switch (e.keyCode) {
          case 37:
              log2 = 'arrow_left';
              break;
          case 38:
              log2 = 'arrow_up';
              break;
          case 39:
              log2 = 'arrow_right';
              break;
          case 40:
              log2 = 'arrow_down';
              break;
      }

      log3 = log2 + ');';
      log4 = log1 + log3;
  }

    export let onKeydown;
    export handleKeydown;
</script>    

<svelte:window on:keydown|preventDefault={handleKeydown} />
