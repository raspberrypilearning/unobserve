In JavaScript wordt de `unobserve`-methode gebruikt met een intersection observer om het observeren van een doelelement te stoppen.

Je kunt `unobserve` gebruiken om te voorkomen dat een animatie wordt geactiveerd, of om geheugen- of prestatieproblemen te voorkomen.

Here is an example of how `unobserve` is used in the [Animated story](https://projects.raspberrypi.org/en/projects/animated-story) project in the [More web](https://projects.raspberrypi.org/en/raspberrypi/more-web) path:

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
