![image info](./asset/done.PNG)

![image info](./asset/done3.png)

### Useful websites:
- [Transition](https://www.w3schools.com/css/css3_transitions.asp)
- [Transform](https://www.w3schools.com/css/css3_2dtransforms.asp)
- [Shadows](https://www.w3schools.com/css/css3_shadows.asp)

### What I have learned?
- Flexbox:
```
.panel {
	/* Share even space between other children */
	<!-- the flex grow factor -->
	flex: 1;
	...
}
```
- Specifies the components of a flexible length: the flex grow factor and flex shrink factor, and the flex basis.
```
flex: 1 0 auto;
```
- Add `open` class to the clicked panel
```
.panel.open {
	/* Take 5 times the amount of the extra room */
	flex: 5;
	font-size: 40px;
}
```
- Align items in the center center:
```
display: flex;
justify-content: center;
align-items: center;
```
- Transition:
```
transition:
	font-size 0.7s cubic-bezier(0.61, -0.19, 0.7, -0.11),
	flex 0.7s cubic-bezier(0.61, -0.19, 0.7, -0.11),
	background 0.2s;
```

### [Source Code:](https://github.com/stevedang-dev/JavaScript-30-Days-Challenge/blob/master/05%20-%20Flex%20Panel%20Gallery/index.html)
- JavaScript:

```
const panels = document.querySelectorAll('.panel');

function toggleOpen() {
	this.classList.toggle('open');
}

function toggleActive(e) {
	if (e.propertyName.includes('flex')) {
		this.classList.toggle('open-active');
	}
}
panels.forEach(panel => panel.addEventListener('click', toggleOpen));
panels.forEach(panel => panel.addEventListener('transitionend', toggleActive));

```

- CSS:

```

body { margin: 0; }
.panels {
	min-height: 100vh;
	overflow: hidden;
	display: flex;
	flex-direction: row;
}

.panel {
	/* Share even space between other children */
	flex: 1;
	color: white;
	text-align: center;
	align-items: center;
	transition:
		font-size 0.7s cubic-bezier(0.61, -0.19, 0.7, -0.11),
		flex 0.7s cubic-bezier(0.61, -0.19, 0.7, -0.11),
		background 0.2s;
	font-size: 20px;
	background-size: cover;
	background-position: center;
	display: flex;
	flex-direction: column;
	justify-content: center;
}

.panel-1 {
	background-image: url(./asset/1.jpg);
}

.panel-2 {
	background-image: url(./asset/2.jpg);
}

.panel-3 {
	background-image: url(./asset/3.jpg);
}

.panel-4 {
	background-image: url(./asset/4.jpg);
}

.panel-5 {
	background-image: url(./asset/5.jpg);
}

/* Flex children */
.panel > * {
	margin: 0;
	width: 100%;
	transition: transform 0.5s;
	flex: 1 0 auto;
	display: flex;
	justify-content: center;
	align-items: center;
}

.panel > *:first-child { transform: translateY(-100%); }
.panel.open-active > *:first-child { transform: translateY(0); }
.panel > *:last-child { transform: translateY(100%); }
.panel.open-active > *:last-child { transform: translateY(0); }

.panel p {
	text-transform: uppercase;
	font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif, cursive;
	text-shadow: 0 0 4px rgba(0, 0, 0, 0.72),
				0 0 14px rgba(0, 0, 0, 0.45);
	font-size: 2em;
}

.panel p:nth-child(2) {
	font-size: 4em;
}

.panel.open {
	/* Take 5 times the amount of the extra room */
	flex: 5;
	font-size: 40px;
}

.cta {
	color: white;
	text-decoration: none;
}

```

All done! Yaaaaay!
