<script>
  let opened = false;
  const openLetter = () => {
    opened = true;
  };
  
  const letterContent = `
  사랑하는 내 여자친구에게 🌸

  오늘 하루도 수고했어. 
  너와 함께 하는 매일이 정말 소중하고 행복해.
  
  앞으로도 계속 함께 하자.
  
  사랑해 ❤️
  `;
</script>

<div class="container">
  {#if !opened}
    <div class="envelope" on:click={openLetter}>
      <div class="airmail-border">
        <div class="address">
          <div class="to">받는 사람: 나의 사랑 💕</div>
          <div class="from">보내는 사람: 너를 사랑하는 나 🌷</div>
        </div>
      </div>
      <div class="hint">편지를 클릭해서 열어보세요 ✨</div>
    </div>
  {:else}
    <div class="letter">
      <pre>{letterContent}</pre>
    </div>
  {/if}
</div>

<style>
.container {
  @apply flex items-center justify-center h-screen;
  background-color: #fffaf0; /* 따뜻한 크림색 배경 */
}

.envelope {
  @apply w-80 h-52 bg-white rounded-lg shadow-2xl cursor-pointer relative;
}

.airmail-border {
  @apply absolute top-2 bottom-2 left-2 right-2 border-4 border-dashed border-blue-400 rounded;
}

.address {
  @apply absolute inset-0 flex flex-col justify-center items-center text-sm text-gray-700;
}

.to, .from {
  @apply mb-2;
}

.hint {
  @apply absolute bottom-[-30px] left-0 right-0 text-center text-gray-600 text-sm;
}

.letter {
  @apply w-80 bg-white p-6 rounded-xl shadow-2xl text-gray-700 whitespace-pre-wrap text-base;
  animation: fade-in 1s ease-out;
}

@keyframes fade-in {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}
</style>
