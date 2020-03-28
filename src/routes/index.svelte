<script>
  import { onMount } from 'svelte'
  let bg = ''
  let bgAnimation = ''
  let blurredBg = `//res.cloudinary.com/sixth/image/upload/c_fill,e_blur:500,q_auto,w_500/v1585348748/bg.jpg`

  onMount(() => {
    function resize() {
      const bgWidth = document.body.offsetWidth
      const bgHeight = document.body.offsetHeight
      bg = `//res.cloudinary.com/sixth/image/upload/c_crop,g_center,f_auto,h_${bgHeight},q_auto,w_${bgWidth}/v1585348748/bg.webp`
      bgAnimation = 'animate-in'
    }
    window.onresize = resize
    resize()
  })
</script>

<style>
  figure {
    text-align: center;
    margin: 0 auto;
    margin: 0 0 1em 0;
  }

  figure img {
    height: 120px;
    margin-bottom: 20px;
  }

  .logo {
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  figcaption {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 50px;
    font-size: 14px;
  }

  .bg {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    z-index: -1;
    background-size: cover;
    background-position: center;
    background-image: url({blurredBg});
  }

  .bg .inner {
    width: 100%;
    height: 100%;
    background-size: cover;
    background-position: center;
    transition: opacity 4s ease-out;
    transition-delay: 200ms;
    opacity: 0;
  }

  .bg.animate-in .inner {
    opacity: 1;
  }
</style>

<svelte:head>
  <title>Sixth</title>
</svelte:head>

<div class="logo">
  <figure>
    <img
      alt="Sixth"
      src="//res.cloudinary.com/sixth/image/upload/v1585348748/sixth.svg" />
    <figcaption>
      frontend development
      <br />
      hello@sixth.dk
      <br />
      cvr 38.41.89.98
    </figcaption>
  </figure>
</div>

<div class="bg {bgAnimation}" style="background-image:url({blurredBg})">
  <div class="inner" style="background-image:url({bg});" />
</div>
