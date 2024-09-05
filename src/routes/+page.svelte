<script lang="ts">

    import smusif from "$lib/assets/img/Frame 634.svg"
    import telegram from "$lib/assets/img/telegram-svgrepo-com 1.svg"
    import smusifLogo from "$lib/assets/img/Smusif-lable 1.png"
    import smusifNote from "$lib/assets/img/smusif-logo-0 1.png"
    import gradientMain from "$lib/assets/img/purpleGradientMain.svg"
    import gradientNote from "$lib/assets/img/purpleGradientNote.svg"

    import ArtistCard from "$lib/components/ArtistCard.svelte"
    import {artists} from "$lib/data/artists"
    import leftArrow from "$lib/assets/icons/left-arrow.svg"
    import rightArrow from "$lib/assets/icons/right-arrow.svg"

    import believe from "$lib/assets/img/believe.png"
    import zvonko from "$lib/assets/img/zvonko.svg"
    import kontor from "$lib/assets/img/kontor.png"
    import broma from "$lib/assets/img/broma.svg"

    import minimum from "$lib/assets/img/minimum.png"
    import moneyUp from "$lib/assets/img/moneyUp.png"
    import allWorld from "$lib/assets/img/all-world.png"
    import fastSup from "$lib/assets/img/fast-sup.png"
    import {releases} from "$lib/data/releases";
    import Releases from "$lib/components/Releases.svelte";
    import type {MouseEventHandler} from "svelte/elements";

    import telegramFooter from "$lib/assets/img/telegram-footer.svg"
    import vkFooter from "$lib/assets/img/vk-footer.svg"

    let artistSlider;
    let currentImage: HTMLElement;

    const releasesClick = (release, index): MouseEventHandler<HTMLButtonElement> => async (event) => {
        if (release[4]) {
            releases.forEach((release) => {
                release[4] = false;
                release[5].pause();
            })
        } else {
            releases.forEach((release) => {
                release[4] = false;
                release[5].pause();
            })
            release[4] = !release[4];
            release[5].play();
        }
        releases[index] = release;
        // releases = [...releases];
    }

    function hoverWhyUs(num: number) {
        document.querySelectorAll('.hover-image').forEach((img) => {
            img.classList.remove('active-image');
        })

        const imagesNum = new Map(
            [
                [1, document.getElementById('image1')],
                [2, document.getElementById('image2')],
                [3, document.getElementById('image3')],
                [4, document.getElementById('image4')]
            ]
        )
        currentImage = imagesNum.get(num)

        if (currentImage) {
            currentImage.classList.add('active-image');
        }
    }


</script>


<header>
    <div class="smusif-size">
        <div class="logo-animations">
            <a href="/" class="link">
                <img src="{smusif}" alt="Logo" class="logo">
            </a>
        </div>
        <nav>
            <ul>
                <li><a href="/">главная</a></li>
                <li><a href="/">о нас</a></li>
                <li><a href="/">почему мы</a></li>
                <li><a href="/">артисты</a></li>
                <li><a href="/">партнёры</a></li>
            </ul>
        </nav>
        <div class="second-logo-animations">
            <div class="logo-animations">
                <a href="https://t.me/smusif_label" class="link">
                    <img src="{telegram}" alt="Telegram" class="logo">
                </a>
            </div>
        </div>
    </div>
</header>

<div class="main-container">
    <div class="for-main-container">
        <main>
            <div class="content">
                <div class="no-button-animation">
                    <div class="smusif-logo-animations">
                        <img src="{smusifLogo}" alt="SMUSIF" class="smusif-logo">
                    </div>
                    <p class="subtitle">Твой проводник в мир музыки</p>
                    <form action="https://forms.yandex.ru/u/66bbd23684227c669abd390f/" target="_blank"
                          class="application-button-pos">
                        <div class="application-button-scale">
                            <button class="application-button">оставить заявку</button>
                        </div>
                    </form>
                </div>
                <img src="{gradientMain}" alt="Gradient" class="gradient">
            </div>
        </main>
    </div>
</div>
<div class="sections-pos">
    <div class="sections-container">
        <section class="about-us">
            <h2>О нас</h2>
            <div class="about-us-content">
                <p class="about-us-text">Мы — международный музыкальный лейбл, объединяющий таланты со всего мира.
                    Мы продвигаем музыку, чтобы ваш талант зазвучал на всю планету!
                    Момент мы сотрудничаем с такими всемирно известными агрегаторами, как</p>
                <img src="{smusifNote}" alt="Note" class="smusif-note">
                <img src="{gradientNote}" alt="GradientNote" class="gradient-note">
                <div class="partners">
                    <div class="partner-card">
                        <img src="{believe}" alt="believe" class="believe">
                    </div>
                    <div class="partner-card partner-card-long">
                        <img src="{zvonko}" alt="zvonko">
                    </div>
                    <div class="partner-card partner-card-long">
                        <img src="{kontor}" alt="kontor">
                    </div>
                    <div class="partner-card">
                        <img src="{broma}" alt="broma" class="broma">
                    </div>
                </div>
            </div>
        </section>


        <section class="why-us">
            <h2>Почему мы</h2>
            <div class="why-us-container">
                <div class="why-us-choose">
                    <img src="{moneyUp}" alt="money-up" class="hover-image active-image" id="image1">
                    <img src="{allWorld}" alt="all-world" class="hover-image" id="image2">
                    <img src="{fastSup}" alt="fast-sup" class="hover-image" id="image3">
                    <img src="{minimum}" alt="minimum" class="hover-image" id="image4">
                </div>
                <div class="why-us-content">
                    <div class="why-us-money-up" on:mouseenter={() => hoverWhyUs(1)}>
                        <img src="{moneyUp}" alt="money-up">
                        <h3>Высокий доход</h3>
                        <p>Наш лейбл забирает всего 15% дохода, остальное уходит артисту</p>
                    </div>
                    <div class="why-us-all-world" on:mouseenter={() => hoverWhyUs(2)}>
                        <img src="{allWorld}" alt="all-world">
                        <h3>Международность</h3>
                        <p>Мы работаем со множеством, как отечественных, так и иностранных агрегаторов</p>
                    </div>
                    <div class="why-us-fast-sup" on:mouseenter={() => hoverWhyUs(3)}>
                        <img src="{fastSup}" alt="fast-sup">
                        <h3>Быстрая поддержка</h3>
                        <p>Наша поддержка отвечает в течение 4 часов и оперативно разбирает вашу проблему</p>
                    </div>
                    <div class="why-us-minimum" on:mouseenter={() => hoverWhyUs(4)}>
                        <img src="{minimum}" alt="minimum">
                        <h3>Минимальный вывод</h3>
                        <p>Минимальная сумма вывода для артиста составляет всего 150 ₽</p>
                    </div>
                </div>
            </div>
        </section>

        <section class="our-artists">
            <h2>Артисты</h2>
            <div class="artist-slider">
                <div class="carousel" bind:this={artistSlider}>
                    {#each artists as artist}
                        <ArtistCard name={artist[0]} avatarSrc={artist[1]}></ArtistCard>
                    {/each}
                </div>

                <button class="arrow-button left" on:click={() => artistSlider.scrollLeft -= 280}>
                    <img src={leftArrow} alt="left arrow">
                </button>
                <button class="arrow-button right" on:click={() => artistSlider.scrollLeft += 280}>
                    <img src={rightArrow} alt="right arrow">
                </button>
            </div>
        </section>

        <section class="our-releases">
            <h2>Релизы</h2>
            <div class="releases">
                {#each releases as release, index}
                    <Releases
                            releaseName={release[0]}
                            artistName={release[1]}
                            releaseImage={release[2]}
                            release={release[3]}
                            isPlaying={release[4]}
                            bind:audioElement={release[5]}
                            on:click={releasesClick(release, index)}
                    ></Releases>
                {/each}
            </div>
        </section>
    </div>
</div>
<footer>
    <div class="footer-things">
        <p>© Smusif 2024</p>
        <div class="footer-icos">
            <img src="{telegramFooter}" alt="telegram-footer">
            <img src="{vkFooter}" alt="vk-footer">
        </div>
        <p>support@smusif.ru</p>
    </div>
</footer>


<style lang="scss">

  footer {
    display: flex;
    justify-content: center;
    height: 120px;
    background-color: #FFFFFF0A;
    backdrop-filter: blur(24px);
    -webkit-backdrop-filter: blur(24px);
  }

  .footer-things {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 1160px;
    padding: 0 20px;
    p {
      font-weight: 450;
      font-size: 28px;
      line-height: 28px;
      color: #FFFFFF66;
    }
  }

  .footer-icos {
    display: flex;
    margin-left: auto;
    padding-right: 40px;
    gap: 20px;
  }

  .releases {
    display: flex;
    flex-wrap: wrap;
    gap: 20px
  }

  .why-us-container {
    display: flex;
  }

  .why-us-choose {
    display: flex;
    align-items: center;
    position: relative;
    min-width: 280px;
    min-height: 280px;
    overflow: hidden;

    img {
      position: absolute;
      width: 280px;
      height: 280px;
      object-fit: cover;
      transition: opacity 0.5s ease-in-out;
    }

    .hover-image {
      opacity: 0;
    }

    .active-image {
      opacity: 1;
    }
  }

  .why-us-content {
    display: flex;
    justify-content: end;
    gap: 20px;
    flex-wrap: wrap;

    div {
      background-color: #FFFFFF0A;
      display: flex;
      min-height: 160px;
      padding: 15px 0 0 19px;
      gap: 16px;
      align-items: start;
      flex-direction: column;
      border-radius: 20px;
      border: 1px solid rgba(255, 255, 255, 0.08);
      backdrop-filter: blur(24px);
      -webkit-backdrop-filter: blur(24px);

      h3 {
        font-size: 32px;
        line-height: 35.2px;
      }

      p {
        font-weight: 300;
        font-size: 24px;
        line-height: 26.4px;
        text-align: start;
      }

      img {
        transition: transform 0.3s ease; /* Плавный переход для увеличения */
      }

      &:hover img {
        transform: scale(1.1); /* Увеличение изображения при наведении */
      }
    }
  }

  .why-us-money-up {
    min-width: 364px;
    max-width: 364px;

    img {
      position: absolute;
      width: 64px;
      height: auto;
      top: -12px;
      left: 308px;
    }
  }

  .why-us-all-world {
    min-width: 336px;
    max-width: 336px;

    img {
      position: absolute;
      width: 64px;
      height: auto;
      top: -12px;
      left: 280px;
    }
  }

  .why-us-fast-sup {
    min-width: 340px;
    max-width: 340px;

    img {
      position: absolute;
      width: 64px;
      height: auto;
      top: -12px;
      left: 288px;
    }
  }

  .why-us-minimum {
    position: relative;
    min-width: 360px;
    max-width: 360px;

    img {
      position: absolute;
      width: 64px;
      height: auto;
      top: -12px;
      left: 308px;
    }
  }

  .no-button-animation {
    opacity: 0;
    transform: scale(0.9);
    animation: fadeInZoom 1.5s forwards;
  }

  .main-container {
    width: 100%;
    max-width: 1160px;
    padding: 0 20px;
    margin: 0 auto;
  }

  header {
    width: 100%;
    display: flex;
    justify-content: center;
    padding: 20px;
    background: rgba(0, 0, 0, 0.2);
    backdrop-filter: blur(24px);
    -webkit-backdrop-filter: blur(24px);
    position: fixed;
    top: 0;
    opacity: 0;
    animation: fadeInDown 1s forwards;
    z-index: 100;
  }

  .smusif-size {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 1120px;
  }

  .logo-animations {
    opacity: 0;
    transform: translateY(-20px);
    animation: logoFadeIn 1.2s forwards;
  }

  .logo {
    width: 32px;
    height: auto;
    transition: transform 0.3s ease;

    &:hover {
      transform: scale(1.1);
    }
  }

  .link {
    display: flex;
  }

  nav ul {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    gap: 56px;
  }

  nav ul li {
    transition: transform 0.3s ease;

    &:hover {
      transform: scale(1.05);
    }
  }

  nav ul li a {
    color: #fff;
    text-decoration: none;
    font-size: 20px;
    font-weight: lighter;
    position: relative;
    overflow: hidden;
    transition: color 0.3s ease;

    &:hover {
      color: #ffcc00;
    }
  }

  main {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    max-height: 1200px;
    min-height: 1000px;
  }

  .content {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: auto 0;
    z-index: 1;
  }

  .gradient {
    position: absolute;
    width: 183.42%;
    height: 236.04%;
    top: -70%;
    left: -50%;
    z-index: -1;
    opacity: 0;
    animation: fadeInUp 1s forwards 0.5s;
  }

  .smusif-logo {
    width: 100%;
    max-width: 862px;
    height: auto;
    opacity: 0;
    transform: translateY(20px);
    animation: fadeInUp 1s forwards 0.5s;
    z-index: 1;
  }

  .subtitle {
    font-size: 48px;
    line-height: 32px;
    margin-top: 23px;
    font-weight: 450;
    color: #fff;
    opacity: 0;
    transform: translateY(20px);
    animation: fadeInUp 1s forwards 0.7s;
  }

  .application-button {
    background-color: #FFFFFF0A;
    color: #ffffff;
    width: 320px;
    height: 56px;
    padding-bottom: 4px;
    font-size: 32px;
    font-weight: 300;
    border-radius: 56px;
    border: 1px solid rgba(255, 255, 255, 0.08);
    backdrop-filter: blur(24px);
    -webkit-backdrop-filter: blur(24px);
    cursor: pointer;
    transition: 0.4s ease;
    opacity: 0;
    animation: fadeInUp 1s forwards 0.9s;

    &:hover {
      background-color: rgba(255, 255, 255, 0.08);
    }
  }

  .application-button-scale {
    width: fit-content;
    margin-top: 60px;
    transition: 0.4s ease;

    &:hover {
      transform: scale(1.05);
    }
  }

  .application-button-pos {
    display: flex;
    justify-content: center;
  }

  .sections-container {
    margin-top: 120px; /* Отступ сверху для отделения от основного контента */
    width: 100%;
    max-width: 1160px;
    padding: 0 20px;
  }

  .about-us-content {
    position: relative;
    display: flex; /* Включаем flexbox для контейнера */
    align-items: start; /* Центрируем элементы по вертикали */
    justify-content: space-between; /* Пространство между текстом и изображением */
    z-index: 1;
    flex-direction: column;
  }

  .about-us-text {
    font-weight: 200;
    text-align: left;
    max-width: 755px;
  }

  .smusif-note {
    position: absolute;
    min-width: 25%;
    right: 0;
    top: -18%;
  }

  .gradient-note {
    position: absolute;
    width: 100%;
    top: -100%;
    right: -28%;
    z-index: -1;
  }

  .partners {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    margin-top: 48px;
  }

  .partner-card {
    background-color: #FFFFFF0A;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 300px;
    height: 60px;
    border-radius: 20px;
    border: 1px solid rgba(255, 255, 255, 0.08);
    backdrop-filter: blur(24px);
    -webkit-backdrop-filter: blur(24px);

    img {
      max-width: 100%;
      max-height: 100%;
      object-fit: contain;
      pointer-events: none;
    }

    &:nth-child(3) {
      margin-left: 80px;
    }
  }

  .partner-card-long {
    width: 500px;
  }

  .believe {
    padding-bottom: 2px;
  }

  .broma {
    padding-bottom: 6px;
  }

  .sections-pos {
    display: flex; /* Включаем flexbox */
    justify-content: center; /* Центрируем по горизонтали */
    align-items: center; /* Центрируем по вертикали (если нужно) */
  }

  .sections-container section {
    padding-bottom: 315px; /* Отступ между секциями */
  }

  .sections-container h2 {
    font-size: 40px;
    line-height: 32px;
    margin-bottom: 100px;
  }

  .sections-container p {
    font-size: 32px;
    line-height: 35.2px;
  }

  .artist-slider {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;

    &:before, &:after {
      position: absolute;
      top: auto;
      height: 800px;
      width: 180px;
      z-index: 2;
      content: '';
    }

    &:before {
      left: 0;
      background: linear-gradient(to right, #000000, #000000CC, #00000000);
    }

    &:after {
      right: 0;
      background: linear-gradient(to left, #000000, #000000CC, #00000000);
    }
  }

  .carousel {
    display: flex;
    align-items: center;
    gap: 80px;
    margin: -300px 0;
    padding: {
      top: 300px;
      bottom: 300px;
      right: 180px;
      left: 180px;
    }
    overflow: hidden;
  }

  .arrow-button {
    position: absolute;
    top: calc(50% - 34.4px);
    width: 40px;
    height: 40px;
    z-index: 2;
    display: flex;
    justify-content: center;
    align-items: center;

    background-color: #FFFFFF0A;
    border-radius: 50%;
    border: 1px solid #FFFFFF14;
    backdrop-filter: blur(24px);
    -webkit-backdrop-filter: blur(24px);
    cursor: pointer;
    transition: 0.4s ease;

    &:hover {
      transform: scale(1.08);
      background-color: #FFFFFF14;
    }

    &.left {
      left: 400px;
    }

    &.right {
      right: 400px;
    }
  }

  @keyframes fadeInDown {
    from {
      opacity: 0;
      transform: translateY(-20px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  @keyframes fadeInUp {
    from {
      opacity: 0;
      transform: translateY(20px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  @keyframes fadeInZoom {
    from {
      opacity: 0;
      transform: scale(0.9);
    }
    to {
      opacity: 1;
      transform: scale(1);
    }
  }

  @keyframes logoFadeIn {
    from {
      opacity: 0;
      transform: translateY(-20px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
</style>
