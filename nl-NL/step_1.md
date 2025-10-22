In JavaScript wordt de `unobserve`-methode gebruikt met een intersection observer om het observeren van een doelelement te stoppen.

Je kunt `unobserve` gebruiken om te voorkomen dat een animatie wordt geactiveerd, of om geheugen- of prestatieproblemen te voorkomen.

Hier is een voorbeeld van het gebruik van `unobserve` in het [Geanimeerd verhaal](https://projects.raspberrypi.org/nl-NL/projects/animated-story) project in het [Meer Web](https://projects.raspberrypi.org/nl-NL/raspberrypi/more-web) pad:

## --- code ---

language: js
filename:
line_numbers: true
line_number_start: 1
line_highlights: 6
-------------------------------------------------------

// Verberg bounce observer
const bounceObserver = new IntersectionObserver((entries) => {
if (entries[0].isIntersecting) {
console.log("BOUNCE TRIGGER IN VIEWPORT");
document.querySelector("#bounce").style.opacity = 0;
bounceObserver.unobserve(entries[0].target);
}
});
bounceObserver.observe(document.querySelector("#hideBounce");

\--- /code ---

Op regel 6 wordt `bounceObserver` aangeroepen om het doelitem (het element met `id="hideBounce"`) `unobserve` te maken.

Hiermee worden geheugen- of prestatieproblemen vermeden, omdat het niet nodig is om het element te blijven observeren als het eenmaal verborgen is.
