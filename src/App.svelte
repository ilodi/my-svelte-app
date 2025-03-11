<script>
  import { onMount } from "svelte";
  import gsap from "gsap";

  /**
   * @type {gsap.TweenTarget}
   */
  let label;
  /**
   * @type {gsap.TweenTarget}
   */
  let card;
  /**
   * @type {gsap.TweenTarget}
   */
  let paragraph;
  /**
   * @type {string | HTMLParagraphElement}
   */
  let contact;
  /**
   * @type {string | HTMLDivElement}
   */
  let instagram;

  onMount(() => {
    gsap.set(card, { opacity: 0 }); // Ocultar el div al inicio
    gsap.set([label, paragraph, contact, instagram], { opacity: 0 }); // Ocultar el texto al inicio

    gsap.to(card, {
      opacity: 1,
      height: "50vh",
      duration: 1.5,
      ease: "power2.out",
      onComplete: () => {
        gsap.to(label, {
          opacity: 1,
          y: 0,
          duration: 1,
          ease: "power2.out"
        });
        gsap.to(paragraph, {
          opacity: 1,
          y: 0,
          duration: 1,
          ease: "power2.out",
          delay: 1
        });
        gsap.to([contact, instagram], {
          opacity: 1,
          duration: 1,
          ease: "power2.out",
          delay: 2
        });
      }
    });
  });
</script>

<style>
  .card {
    width: 40vw;
    height: 0;
    background-color: #242424;
    color: #fff;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: 30px;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    border-radius: 15px;
    overflow: hidden;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
    border: 3px solid #0055CC;
    transition: border-color 0.3s ease-in-out;
  }

  .card:hover {
    border-color: #FFD700;
  }

  .contact {
    margin-top: 20px;
    font-size: 1rem;
    font-weight: bold;
  }

  .social {
    margin-top: 10px;
  }

  .social a {
    color: #FFD700;
    text-decoration: none;
    font-size: 1rem;
    margin-left: 10px;
  }
</style>

<div bind:this={card} class="card">
  <h1 bind:this={label} style="
    margin: 0;
    transform: translateY(-20px);
    font-size: 2.5rem;
    font-weight: bold;
    letter-spacing: 1.5px;
  ">ZOE PLUS</h1>
  <p bind:this={paragraph} style="
    transform: translateY(-20px);
    font-size: 1.2rem;
    line-height: 1.6;
    max-width: 80%;
  ">
    Transformamos ideas en soluciones digitales. <strong> Creación de software, marketing digital, gestión de redes sociales, fotografía y video, y productos digitales.</strong> Impulsamos tu visión con <strong>innovación y creatividad.</strong> En cada proyecto, un compromiso con la calidad y el detalle.
  </p>
  <p bind:this={contact} class="contact"><a href="mailto:admin@zoe-plus.xyz" style="color: #FFD700; text-decoration: none;">📧</a></p>
 
</div>
