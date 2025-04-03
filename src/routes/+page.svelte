<script lang="ts">
  import { onMount } from 'svelte';

  // src/assets/images 폴더 내의 모든 jpg 파일을 eager 옵션으로 불러옴
  const images = import.meta.glob('/src/assets/images/*.jpg', { eager: true });
  const imageList = Object.values(images).map(
    (mod) => (mod as { default: string }).default
  );

  // 현재 퀴즈 데이터: 이미지의 이름(정답)과 이미지 경로
  let currentQuiz: { name: string; src: string } | null = null;
  // 결과 메시지: 정답이 표시되면 값이 채워짐
  let result = '';

  // 랜덤 퀴즈 선택 함수
  function pickRandomQuiz() {
    const randomIndex = Math.floor(Math.random() * imageList.length);
    const src = imageList[randomIndex];
    // 파일 경로에서 확장자 제외한 파일 이름 추출 (한글 파일명 포함)
    const nameMatch = src.match(/\/([^\/]+)\.jpg$/);
    // decodeURIComponent를 사용해 URL 인코딩된 한글을 복원합니다.
    const name = nameMatch ? decodeURIComponent(nameMatch[1]) : 'Unknown';
    currentQuiz = { name, src };
    result = '';
  }

  onMount(() => {
    pickRandomQuiz();
  });

  // 버튼 클릭 핸들러
  // 정답이 아직 안보이면 정답을 보여주고, 정답이 보이면 다음 퀴즈로 넘어감.
  function handleButtonClick() {
    if (!result && currentQuiz) {
      result = `정답은 ${currentQuiz.name} 입니다.`;
    } else {
      pickRandomQuiz();
    }
  }
</script>

<main>
  <h1>이미지 퀴즈</h1>
  {#if currentQuiz}
    <img src={currentQuiz.src} alt="퀴즈 이미지" style="max-width:300px;" />
  {/if}
  <div>
    <button on:click={handleButtonClick}>
      {#if !result}
        정답 확인
      {:else}
        다음
      {/if}
    </button>
  </div>
  {#if result}
    <p>{result}</p>
  {/if}
</main>

<style>
  main {
    text-align: center;
    margin-top: 2rem;
    font-family: sans-serif;
  }
  button {
    padding: 0.5rem;
    margin: 1rem;
    font-size: 1rem;
    cursor: pointer;
  }
  img {
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.2);
  }
</style>
