---
{"dg-publish":true,"permalink":"/A Mesa/Regiões & Geopolítica/Mapa Mundi/","dg-note-properties":{}}
---

<div class="mapa-mundi-root"></div>

<script>
(() => {
  const root = document.querySelector(".mapa-mundi-root");
  if (!root) return;

  const areas = [
    {
      name: "Ana",
      href: "/A%20Mesa/Regi%C3%B5es%20%26%20Geopol%C3%ADtica/Ana/",
      x: 350, y: 380, width: 105, height: 62
    },
    {
      name: "Norden",
      href: "/A%20Mesa/Regi%C3%B5es%20%26%20Geopol%C3%ADtica/Norden/",
      x: 620, y: 370, width: 155, height: 62
    },
    {
      name: "Regiões Bárbaras",
      href: "/A%20Mesa/Regi%C3%B5es%20%26%20Geopol%C3%ADtica/Regi%C3%B5es%20B%C3%A1rbaras/",
      x: 875, y: 305, width: 270, height: 65
    },
    {
      name: "Glória",
      href: "/A%20Mesa/Regi%C3%B5es%20%26%20Geopol%C3%ADtica/Gloria/",
      x: 760, y: 525, width: 125, height: 58
    },
    {
      name: "Agronostrum",
      href: "/A%20Mesa/Regi%C3%B5es%20%26%20Geopol%C3%ADtica/Agronostrum/",
      x: 540, y: 565, width: 210, height: 60
    }
  ];

  root.innerHTML = `
    <div class="mapa-mundi">
      <img
        src="/img/user/Imagens/mapa-a-mesa.jpg"
        alt="Mapa de A Mesa com os continentes Lartuath, Toir, Plagan e Aljanub."
      >
      <svg viewBox="0 0 2048 1536" aria-label="Regiões com artigos publicados">
        ${areas.map((area) => `
          <a href="${area.href}" aria-label="Abrir ${area.name}">
            <title>Abrir ${area.name}</title>
            <rect
              x="${area.x}"
              y="${area.y}"
              width="${area.width}"
              height="${area.height}"
            ></rect>
          </a>
        `).join("")}
      </svg>
    </div>
    <p class="mapa-mundi__hint">
      Passe o cursor sobre um nome destacado para abrir seu artigo.
    </p>
  `;

  const style = document.createElement("style");
  style.textContent = `
    .mapa-mundi {
      position: relative;
      width: min(100%, 1100px);
      margin: 1.5rem auto;
      line-height: 0;
    }

    .mapa-mundi img,
    .mapa-mundi svg {
      display: block;
      width: 100%;
      height: auto;
    }

    .mapa-mundi svg {
      position: absolute;
      inset: 0;
    }

    .mapa-mundi rect {
      fill: transparent;
      stroke: transparent;
      stroke-width: 3;
      transition: fill 150ms ease, stroke 150ms ease;
    }

    .mapa-mundi a:hover rect,
    .mapa-mundi a:focus rect {
      fill: rgba(255, 239, 96, 0.18);
      stroke: rgb(255, 239, 96);
    }

    .mapa-mundi__hint {
      text-align: center;
      opacity: 0.75;
    }
  `;

  document.head.append(style);
})();
</script>