<script>
    import { onMount } from "svelte";
    let daysLeft;
    let audio;
    let isMuted = false;

    onMount(() => {
        const today = new Date();
        const targetDate = new Date("2023-05-19");
        const differenceInTime = targetDate.getTime() - today.getTime();
        daysLeft = Math.ceil(differenceInTime / (1000 * 3600 * 24));
        audio = new Audio("driftking.mp3");
        audio.volume = 0.5;
    });

    function toggleMute() {
        isMuted = !isMuted;
        audio.muted = isMuted;
    }
</script>

<main>
    <h1>
        {daysLeft} days until 
        <span class="family" on:click={() => audio.play()}>family</span>
    </h1>
    <div class="video-container">
        <iframe
            width="928"
            height="522"
            src="https://www.youtube.com/embed/iIY5b1JMvGs"
            title="Every time &quot;family&quot; is said in the Fast &amp; Furious franchise 1-9"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
            allowfullscreen
        />
    </div>
    <div class="mute-toggle" on:click={toggleMute}>
        {isMuted ? "Unmute" : "Mute"}
    </div>
</main>

<style>
    @import url("https://fonts.googleapis.com/css2?family=Montserrat+Alternates:wght@700&display=swap");
    @keyframes bounce {
        0%,
        20%,
        50%,
        80%,
        100% {
            transform: translateY(0);
        }
        40% {
            transform: translateY(-30px);
        }
        60% {
            transform: translateY(-15px);
        }
    }

    :global(body) {
        font-family: "Montserrat Alternates", sans-serif;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100vh;
        margin: 0;
        background-color: #fff;
        background-image: url("https://www.transparenttextures.com/patterns/car-tire.png");
        color: #ffffff;
    }

    h1 {
        font-size: 4rem;
        margin: 0;
        padding-bottom: 4rem;
        background: linear-gradient(45deg, #a0a0a0, #e0e0e0);
        -webkit-background-clip: text;
        color: transparent;
        text-shadow: 1px 1px 0px rgba(255, 255, 255, 0.3),
            -1px -1px 0px rgba(0, 0, 0, 0.2),
            2px 2px 0px rgba(255, 255, 255, 0.2),
            -2px -2px 0px rgba(0, 0, 0, 0.1),
            3px 3px 0px rgba(255, 255, 255, 0.1),
            -3px -3px 0px rgba(0, 0, 0, 0.1);
    }

    .family {
        color:  #ff8b3d;
        text-shadow: 0 0 10px #ff6b81;
        cursor: pointer;
        transition: text-shadow 0.2s;
        text-decoration: none;
    }

    .family:hover {
        animation: bounce 1s;
        text-shadow: 0 0 20px #ff6b81;
    }

    .mute-toggle {
        position: absolute;
        top: 10px;
        left: 10px;
        font-size: 1rem;
        cursor: pointer;
        background: linear-gradient(45deg, #a0a0a0, #e0e0e0);
        -webkit-background-clip: text;
        color: transparent;
        text-shadow: 1px 1px 0px rgba(255, 255, 255, 0.3),
            -1px -1px 0px rgba(0, 0, 0, 0.2),
            2px 2px 0px rgba(255, 255, 255, 0.2),
            -2px -2px 0px rgba(0, 0, 0, 0.1),
            3px 3px 0px rgba(255, 255, 255, 0.1),
            -3px -3px 0px rgba(0, 0, 0, 0.1);

    }

    .video-container {
        position: relative;
        padding-bottom: 56.25%;
        height: 0;
        overflow: hidden;
    }

    .video-container iframe {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
    }
</style>

