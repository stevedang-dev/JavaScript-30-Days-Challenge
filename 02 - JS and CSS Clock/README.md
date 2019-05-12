![image info](./asset/done.PNG)

### Useful websites:
- Transition timing function: https://developer.mozilla.org/en-US/docs/Web/CSS/transition-timing-function


### What I have learned?
1. CSS:
- Set the origin to the right end 100% instead for the center.
- transform-origin: where to do the rotation of the element.
```
transform-origin: 100%;
```

- Get all the hands start at 12 o'clock 
```
transform: rotate(90deg);
```

- Show movement effects
```
transition: all 0.05s;
```

- Tick effects for the hands, bouncing, go forward and back to the right position.
- NOTE: `transition-timing-function` click on the little icon next to it to create some fun ones.
```
transition-timing-function: cubic-bezier(0.1, 2.7, 0.58, 1);
```

- Transition Timinng Function Examples: [Source - https://developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/CSS/transition-timing-function)

```
/* Keyword values */
transition-timing-function: ease;
transition-timing-function: ease-in;
transition-timing-function: ease-out;
transition-timing-function: ease-in-out;
transition-timing-function: linear;
transition-timing-function: step-start;
transition-timing-function: step-end;

/* Function values */
transition-timing-function: steps(4, jump-end);
transition-timing-function: cubic-bezier(0.1, 0.7, 1.0, 0.1);

/* Steps Function keywords */
transition-timing-function: steps(4, jump-start);
transition-timing-function: steps(10, jump-end);
transition-timing-function: steps(20, jump-none);
transition-timing-function: steps(5, jump-both);
transition-timing-function: steps(6, start);
transition-timing-function: steps(8, end);

/* Multiple timing functions */
transition-timing-function: ease, step-start, cubic-bezier(0.1, 0.7, 1.0, 0.1);

/* Global values */
transition-timing-function: inherit;
transition-timing-function: initial;
transition-timing-function: unset;
```

2. JavaScript:
- document.querySelector
- `secondHand.style.<css rule> = '';`

```
    const secondHand = document.querySelector('.second-hand');
    const minHand = document.querySelector('.min-hand');
    const hourHand = document.querySelector('.hour-hand');

    function setDate() {
        const now = new Date();

        const seconds = now.getSeconds();
        // Add 90 degrees because we set these to 90deg for 12 o'clock
        const secondsDegrees = ((seconds / 60) * 360) + 90;
        setTransition(secondHand, seconds);
        secondHand.style.transform = `rotate(${secondsDegrees}deg)`;
        
        const mins = now.getMinutes();
        const minsDegrees = ((mins / 60) * 360) + 90;
        setTransition(minHand, mins);
        minHand.style.transform = `rotate(${minsDegrees}deg)`;

        const hours = now.getHours();
        const hoursDegrees = ((hours / 12) * 360) + 90;
        setTransition(hourHand, hours);
        hourHand.style.transform = `rotate(${hoursDegrees}deg)`;
    }

    // Turn on/off transition for reset transition bug.
    function setTransition (e, val) {
        e.style.transition = (val === 0) ? 'none ': 'all 0.05s cubic-bezier(0.1, 2.7, 0.58, 1)';
    }

    setInterval(setDate, 1000);
```
