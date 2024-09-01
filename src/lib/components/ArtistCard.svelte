<script lang="ts">

    export let avatarSrc: string
    export let name: string

</script>

<div class="artist-card">
    <div class="avatar">
        <img class="avatar-img" src={avatarSrc} alt={name} width="100%">
        <img class="avatar-glow" src={avatarSrc} alt={name} width="100%">
    </div>

    <div class="name">{name}</div>
</div>

<style lang="scss" >

  .artist-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: fit-content;
  }


  .avatar {
    position: relative;
    width: 200px;
    height: 200px;
    margin-bottom: 8px;
    pointer-events: none;
  }

  .avatar-img {
    position: relative;

    border-radius: 50%;
    z-index: 1;
  }

  .avatar-glow {
    position: absolute;
    left: 0;
    top: 0;

    border-radius: 50%;
    -webkit-filter: blur(160px);
    filter: blur(160px);
    opacity: 0.48;
  }

  .name {
    font-weight: 450;
    font-size: 20px;
  }

</style>