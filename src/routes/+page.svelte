<script>
    let opened = false;
  
    const openLetter = () => {
      opened = true;
    };
  
    const letterContent = `
シノへ

昨日あった出来事を振り返ると、私たちの間にあったたくさんの話が思い出されます。
いつも電話でお互いの声を聞き合いながら、近くにいた時間が恋しいです。あの時、
断固として「だめだ！」と叫びながら別れの挨拶をした記憶もありますが、
その瞬間にも私はあなたのそばで応援したいという決意をしていました。

実は、大学1年生の時、軍隊に入隊する前の私は、
自分を振り返るとあなたに見せるには足りなかった、
もしかすると醜い人間だったと告白したいです。
ピザが好きで、時にはピザの箱をこっそり隠していた姿もありましたが、
時が経つにつれて少しずつ変わっていったと感じています。
私たちは皆、変わることができ、変わらなければならないと信じています。
一言が人の人生を変えることができるように。

私はいつもあなたの悩みや成長を共に記録し、
正しい方向へ進めるよう心から応援する人になりたいです。
お互いが望む未来に向かって進むためには、共に成長する時間が必要だと思います。
ですから、意図せずに距離を置かないでください。あなたの声、温かい応援が恋しいです。

愛してる。本当に愛してるよ。

  `;
  </script>
  
  <div class="outer-container">
    {#if !opened}
      <div class="envelope" on:click={openLetter}>
        <div class="text-on-envelope">
          눌러서 열어보세요 ✨
        </div>
      </div>
    {:else}
      <div class="letter">
        <pre class="letter-text">{letterContent}</pre>
        <img class="letter-gif" src="/a.gif" alt="Decorative Gif" />
      </div>
    {/if}
  </div>
  
  <style>
    /* Google Fonts에서 Dancing Script 불러오기 */
    @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;500;700&display=swap');
  
    .outer-container {
      width: 100vw;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: linear-gradient(to bottom, #ffd1dc, #f8effd);
      position: relative;
      margin: 0;
      padding: 0;
    }
  
    .envelope {
      position: relative;
      cursor: pointer;
      width: 80%;
      max-width: 400px;
      aspect-ratio: 4/3;
      background: url('/envelope.jpg') no-repeat center center;
      background-size: contain;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
      transition: transform 0.3s ease-out, box-shadow 0.3s ease-out;
    }
    .envelope:hover {
      transform: translateY(-5px);
      box-shadow: 0 12px 24px rgba(0,0,0,0.3);
    }
  
    .text-on-envelope {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: 1.125rem;
      font-weight: 600;
      color: #fff;
      text-shadow: 0 2px 5px rgba(0,0,0,0.6);
      z-index: 1;
      /* 여기선 기본 폰트 유지 (필요 시 Dancing Script 적용 가능) */
    }
  
    .letter {
      width: 80%;
      max-width: 400px;
      height: 28rem;
      background: white;
      border: 1px solid #eee;
      border-radius: 12px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
      padding: 2rem;
      color: #333;
      overflow: auto;
      animation: fade-in 0.7s ease-out;
      background-image: repeating-linear-gradient(
        to bottom,
        transparent,
        transparent 2.2rem,
        #f0f0f0 2.2rem,
        #f0f0f0 2.4rem
      );
      font-family: 'Dancing Script', cursive;
      line-height: 1.8;
    }
  
    .letter-text {
      font-size: 1rem;
      white-space: pre-wrap;
    }
    
    .letter-gif {
      display: block;
      margin: 1rem auto 0 auto;
      max-width: 100%;
    }
  
    @keyframes fade-in {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
  