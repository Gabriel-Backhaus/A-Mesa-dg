---
{"dg-publish":true,"permalink":"/A Mesa/Eventos/Calendário/Calendário/","dg-note-properties":{}}
---

<div id="calendario-a-mesa"></div>

<style>
  .mesa-calendar {
    display: grid;
    gap: 1.25rem;
  }

  .mesa-calendar__months {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(17rem, 1fr));
    gap: 1rem;
  }

  .mesa-calendar__month {
    padding: 0.85rem;
    border: 1px solid var(--background-modifier-border, #555);
    border-radius: 8px;
    background: var(--background-secondary);
  }

  .mesa-calendar__month h2 {
    margin: 0 0 0.7rem;
    text-align: center;
    font-size: 1.1rem;
  }

  .mesa-calendar__weekdays,
  .mesa-calendar__days {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 0.18rem;
  }

  .mesa-calendar__weekdays {
    margin-bottom: 0.3rem;
    color: var(--text-muted, #aaa);
    font-size: 0.72rem;
    text-align: center;
  }

  .mesa-calendar__day {
    display: grid;
    aspect-ratio: 1;
    place-items: center;
    border-radius: 4px;
    color: var(--text-normal);
    text-decoration: none;
  }

  .mesa-calendar__day:hover,
  .mesa-calendar__day:focus-visible {
    background: rgba(240, 100, 73, 0.28);
    color: #ffef60;
    outline: 1px solid #f06449;
  }
</style>

<script>
(() => {
  const months = [
    { id: "jaio", name: "Jaio", days: 29 },
    { id: "fervembro", name: "Fervembro", days: 28 },
    { id: "fluvio", name: "Fluvio", days: 30 },
    { id: "quarto", name: "Quarto", days: 28 },
    { id: "mail", name: "Mail", days: 29 },
    { id: "hexis", name: "Hexis", days: 28 },
    { id: "mistis", name: "Mistis", days: 29 },
    { id: "brumario", name: "Brumário", days: 28 },
    { id: "noctumbro", name: "Noctumbro", days: 29 },
    { id: "floreio", name: "Floreio", days: 28 },
    { id: "verdejo", name: "Verdejo", days: 29 },
    { id: "ceifo", name: "Ceifo", days: 28 }
  ];

  const weekdays = ["Dom", "Seg", "Ter", "Qua", "Qui", "Sex", "Sáb"];
  const root = document.querySelector("#calendario-a-mesa");

  // Mude para true somente depois de criar as notas dos dias.
  const dayPagesExist = false;

  function dayUrl(month, day) {
    if (!dayPagesExist) return `#${month.id}-${day}`;

    return `/calendario/${month.id}/${String(day).padStart(2, "0")}/`;
  }

  let weekday = 0;

  root.innerHTML = `
    <section class="mesa-calendar">
      <div class="mesa-calendar__months">
        ${months.map((month) => {
          const days = Array.from({ length: month.days }, (_, index) => {
            const day = index + 1;
            const firstDayStyle =
              index === 0 ? `style="grid-column-start: ${weekday + 1}"` : "";

            return `
              <a
                class="mesa-calendar__day"
                href="${dayUrl(month, day)}"
                ${firstDayStyle}
                title="${day} de ${month.name}"
              >${day}</a>
            `;
          }).join("");

          weekday = (weekday + month.days) % 7;

          return `
            <section class="mesa-calendar__month">
              <h2>${month.name}</h2>
              <div class="mesa-calendar__weekdays">
                ${weekdays.map((name) => `<span>${name}</span>`).join("")}
              </div>
              <div class="mesa-calendar__days">${days}</div>
            </section>
          `;
        }).join("")}
      </div>
    </section>
  `;
})();
</script>