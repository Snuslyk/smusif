<script lang="ts">

    import smusif from "$lib/assets/img/Frame 634.svg";
    import telegram from "$lib/assets/img/telegram-svgrepo-com 1.svg";
    import smusifLogo from "$lib/assets/img/Smusif-lable 1.png";
    import smusifNote from "$lib/assets/img/smusif-logo-0 1.png";
    import gradientMain from "$lib/assets/img/purpleGradientMain.svg";
    import gradientNote from "$lib/assets/img/purpleGradientNote.svg";

    import ArtistCard from "$lib/components/ArtistCard.svelte";
    import {artists} from "$lib/data/artists";
    import leftArrow from "$lib/assets/icons/left-arrow.svg";
    import rightArrow from "$lib/assets/icons/right-arrow.svg";

    import believe from "$lib/assets/img/believe.png";
    import zvonko from "$lib/assets/img/zvonko.svg";
    import kontor from "$lib/assets/img/kontor.png";
    import broma from "$lib/assets/img/broma.svg";

    import minimum from "$lib/assets/img/minimum.png";
    import moneyUp from "$lib/assets/img/moneyUp.png";
    import allWorld from "$lib/assets/img/all-world.png";
    import fastSup from "$lib/assets/img/fast-sup.png";
    import {releases} from "$lib/data/releases";
    import Releases from "$lib/components/Releases.svelte";
    import type {MouseEventHandler} from "svelte/elements";

    import telegramFooter from "$lib/assets/img/telegram-footer.svg";
    import vkFooter from "$lib/assets/img/vk-footer.svg";

    let artistSlider;
    let currentImage: HTMLElement;

    let artistSliderCardId: number = 0;
    const artistOffset: number[] = artists
        .slice(0, artists.length - 2)
        .map((_, id) => id * 280);

    const sliderClick = (direction: 'left' | 'right'): MouseEventHandler<HTMLButtonElement> => async (event) => {
        if (direction === 'left') {
            artistSliderCardId = (artistSliderCardId > 0) ? artistSliderCardId - 1 : artistOffset.length - 1;
        } else {
            artistSliderCardId = (artistSliderCardId < artistOffset.length - 1) ? artistSliderCardId + 1 : 0;
        }

        console.log(artistSliderCardId);
        artistSlider.scrollLeft = artistOffset[artistSliderCardId];
    }

    console.log(artistOffset)

    let aboutUsSection;
    let whyUsSection;
    let ourArtistsSection;
    let ourReleasesSection;

    function calculateScroll(section) {
        const offset = 200;
        const sectionPosition = section.getBoundingClientRect().top + window.scrollY;
        const offsetPosition = sectionPosition - offset;

        window.scrollTo({
            top: offsetPosition,
            behavior: 'smooth'
        });
    }

    const scrollToSection = (num: number): MouseEventHandler<HTMLButtonElement> => async (event) => {
        event.preventDefault(); // Prevent the default anchor behavior

        switch (num) {
            case 1:
                calculateScroll(aboutUsSection);
                break;
            case 2:
                calculateScroll(whyUsSection);
                break;
            case 3:
                calculateScroll(ourArtistsSection);
                break;
            case 4:
                calculateScroll(ourReleasesSection);
                break;
        }
    }

    const releasesClick = (release, index): MouseEventHandler<HTMLButtonElement> => async (event) => {
        if (release[4]) {
            releases.forEach((release) => {
                release[4] = false;
                release[6] = false;
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
                <li><a href="#about-us" on:click={scrollToSection(1)}>о нас</a></li>
                <li><a href="#why-us" on:click={scrollToSection(2)}>почему мы</a></li>
                <li><a href="#our-artists" on:click={scrollToSection(3)}>артисты</a></li>
                <li><a href="#our-releases" on:click={scrollToSection(4)}>релизы</a></li>
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
        <section bind:this={aboutUsSection} id="about-us">
            <h2>О нас</h2>
            <div class="about-us-content">
                <p class="about-us-text">Мы — международный музыкальный лейбл, объединяющий таланты со всего мира.
                    Мы продвигаем музыку, чтобы ваш талант зазвучал на всю планету!
                    Момент мы сотрудничаем с такими всемирно известными агрегаторами, как</p>
                <img src="{smusifNote}" alt="Note" class="smusif-note">
                <img src="{gradientNote}" alt="GradientNote" class="gradient-note">
                <div class="partners">
                    <a href="https://www.believe.com/">
                        <div class="partner-card">
                            <img src="{believe}" alt="believe" class="believe">
                        </div>
                    </a>
                    <a href="https://zvonkodigital.com/">
                        <div class="partner-card partner-card-long">
                            <img src="{zvonko}" alt="zvonko">
                        </div>
                    </a>
                    <a href="https://kontornewmedia.com/">
                        <div class="partner-card partner-card-long">
                            <img src="{kontor}" alt="kontor">
                        </div>
                    </a>
                    <a href="https://broma16.ru/">
                        <div class="partner-card">
                            <img src="{broma}" alt="broma" class="broma">
                        </div>
                    </a>
                </div>
            </div>
        </section>


        <section bind:this={whyUsSection} id="why-us">
            <h2>Почему мы</h2>
            <div class="why-us-container">
                <div class="why-us-choose">
                    <img src="{moneyUp}" alt="money-up" class="hover-image active-image" id="image1">
                    <img src="{allWorld}" alt="all-world" class="hover-image" id="image2">
                    <img src="{fastSup}" alt="fast-sup" class="hover-image" id="image3">
                    <img src="{minimum}" alt="minimum" class="hover-image" id="image4">
                </div>
                <div class="why-us-content">
                    <div class="why-us-content-div">
                        <div class="why-us-money-up" role="button" tabindex="0" on:mouseenter={() => hoverWhyUs(1)}>
                            <img src="{moneyUp}" alt="money-up">
                            <h3>Высокий доход</h3>
                            <p>Наш лейбл забирает всего 15% дохода, остальное уходит артисту</p>
                        </div>
                        <div class="why-us-all-world" role="button" tabindex="0" on:mouseenter={() => hoverWhyUs(2)}>
                            <img src="{allWorld}" alt="all-world">
                            <h3>Международность</h3>
                            <p>Мы работаем со множеством, как отечественных, так и иностранных агрегаторов</p>
                        </div>
                    </div>
                    <div class="why-us-content-div">
                        <div class="why-us-fast-sup" role="button" tabindex="0" on:mouseenter={() => hoverWhyUs(3)}>
                            <img src="{fastSup}" alt="fast-sup">
                            <h3>Быстрая поддержка</h3>
                            <p>Наша поддержка отвечает в течение 4 часов и оперативно разбирает вашу проблему</p>
                        </div>
                        <div class="why-us-minimum" role="button" tabindex="0" on:mouseenter={() => hoverWhyUs(4)}>
                            <img src="{minimum}" alt="minimum">
                            <h3>Минимальный вывод</h3>
                            <p>Минимальная сумма вывода для артиста составляет всего 150 ₽</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section bind:this={ourArtistsSection} id="our-artists">
            <h2>Артисты</h2>
            <div class="artist-slider">
                <div class="carousel" bind:this={artistSlider}>
                    {#each artists as artist}
                        <ArtistCard
                                    name={artist[0]}
                                    avatarSrc={artist[1]}
                        ></ArtistCard>
                    {/each}
                </div>

                <button class="arrow-button left" on:click={sliderClick('left')}>
                    <img src={leftArrow} alt="left arrow">
                </button>
                <button class="arrow-button right" on:click={sliderClick('right')}>
                    <img src={rightArrow} alt="right arrow">
                </button>
            </div>
        </section>

        <section bind:this={ourReleasesSection} id="our-releases">
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
            <a href="https://t.me/smusif_label" class="telegram-link">
                <img src="{telegramFooter}" alt="telegram-footer">
            </a>
            <a href="https://vk.com/smusif" class="link">
                <img src="{vkFooter}" alt="vk-footer">
            </a>
        </div>
        <p>support@smusif.ru</p>
    </div>
</footer>


<style lang="scss">

  @import "$lib/assets/css/pagecss.scss";

</style>
