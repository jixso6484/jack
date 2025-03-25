<script>
  export let content;
</script>

<div class="letter">
  <pre>{content}</pre>
</div>

<style>
  .letter {
    @apply w-80 bg-white p-6 rounded-2xl shadow-xl whitespace-pre-wrap text-gray-800 text-base;
    animation: fade-in 1s ease-out;
  }

  @keyframes fade-in {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
  }
</style>
