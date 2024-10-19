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
    user-select: none;
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

  @media (max-width: 1132px) {
    .name {
      font-size: 18px;
    }
  }
  @media (max-width: 1000px) {
    .name {
      font-size: 16px;
    }
  }
  @media (max-width: 860px) {
    .name {
      font-size: 14px;
    }
  }
  @media (max-width: 700px) {
    .name {
      font-size: 12px;
    }
  }
  @media (max-width: 580px) {
    .name {
      font-size: 10px;
    }
  }

</style>