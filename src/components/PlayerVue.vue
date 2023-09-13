<template>
	<audio id="player" volume="0.1"  loop>
		<source src="/sound/Polozhenie.mp3" type="audio/mpeg">
		Your browser does not support the audio element.
	</audio>

	<div class="PlayerGeneralComponent"> 
        <div></div>
        <div class="PlayerComponent"> 
            <i class="PlayerBtn bi bi-file-play-fill"     onclick="document.getElementById('player').play()"></i>
            <i class="PlayerBtn bi bi-pause-btn-fill"     onclick="document.getElementById('player').pause()"></i>
            <i class="PlayerBtn bi bi-volume-up-fill"     onclick="document.getElementById('player').volume += 0.1"></i>
            <i class="PlayerBtn bi bi-volume-down-fill"   onclick="document.getElementById('player').volume -= 0.1"></i>
            <i class="PlayerBtn bi bi-volume-mute-fill"   onclick="document.getElementById('player').muted=!document.getElementById('player').muted"></i>
        </div>
        <div></div>
	</div>
</template>
<style>
	.PlayerGeneralComponent{ 
        position: relative;
		z-index: 1;
        display: flex;
        justify-content: space-around;
	}
    .PlayerComponent{ 
        color: rgb(32, 32, 32);;
        display: flex;
        padding: 20px;
        gap: 50px;
        border-radius: 8px;
        background-color: wheat;
        left: 50%;
	}
    .PlayerBtn:hover{
        box-shadow: 3px 3px 3px 2px rgba(0, 0, 0, 0.2);
    }
</style>
<script>
</script>


