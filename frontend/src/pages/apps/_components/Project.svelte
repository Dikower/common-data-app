<script>
  import {goto} from '@roxi/routify';
  import {fade} from 'svelte/transition';
  import {onMount} from 'svelte';

  export let title = 'Влияние проходимого расстояния на здоровье';
  export let participants_count = 42;
  export let project_img;
  export let project_link;
  onMount(() => {
    if (project_img == null) {
      project_img = "/images/project_images/follow_project_card.png";
    }
  });
</script>

<div class="project-card" on:click={() => $goto('../../project/'+project_link)} in:fade>
  <div class="img-wrapper">
    <img size="100%, 20%" src="{'/'+project_img+'.png'}" class="img" alt="Картинка проекта">
  </div>

  <div class="title">
    <h2 class="project-title">{title}</h2>
  </div>

  <div class="bar">
    <div class="progress" style="width: {participants_count}%"></div>
  </div>
</div>


<style>
  .bar {
    width: 100%;
    height: 4px;
    background: #9B9B9B;
  }

  .progress {
    background: black;
    height: 4px;
  }

  .img {
    object-fit: cover;
    height: 194px;
    width: 223px;

  }

  .img-wrapper {
    width: 100%;
    text-align: center;
  }

  .project-card {
    font-family: "Helvetica Norm";
    display: flex;
    flex-direction: column;
    max-width: 223px;
    padding-right: 1%;
    padding-bottom: 5%;
  }
  .project-card:hover {
    cursor: pointer;
  }
  .project-title {
    font-size: calc(16px + (18 - 16) * ((100vw - 300px) / (1440 - 300)));
    padding-top: 5%;
    padding-bottom: 5%;
  }
</style>