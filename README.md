
# Round Robin Tournament Generator

A javascript function that create a schedule where every team plays against every other team exactly once.

## Parameters

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `teams` | `array` | **Required**. Array of teams. The array items can be anything. |
| `isDouble` | `boolean` | **Optional**. If true, double rounds of fixtures will be returned. |



## Usage/Examples

Get the raw result:

```javascript
import roundRobinTournament from './roundRobinTournament.min.js';

const teams = [
  { id: 26, name: 'Arsenal' },
  { id: 52, name: 'Aston Villa' },
  { id: 13, name: 'Bournemouth' },
  { id: 7, name: 'Brentford' },
  { id: 33, name: 'Brighton and Hove Albion' },
  { id: 41, name: 'Chelsea' },
  { id: 18, name: 'Crystal Palace' },
  { id: 40, name: 'Everton' },
  { id: 28, name: 'Fulham' },
  { id: 19, name: 'Leeds United' }
];

console.log(roundRobinTournament(teams, true));
```

Full usage example:

#### index.html
```html
<style>
  p, h4 {
    margin: 0;
  }
  #schedule {
    font-size: 0.8rem;
  }
  .fixture {
    display: inline-block;
    border: 1px solid;
    padding: 5px;
    min-width: 260px;
  }
</style>
<div id="schedule"></div>
<script src="./main.js" type="module"></script>
```

#### main.js
```javascript
import roundRobinTournament from './roundRobinTournament.js';

const teams = [
  { id: 26, name: 'Arsenal' },
  { id: 52, name: 'Aston Villa' },
  { id: 13, name: 'Bournemouth' },
  { id: 7, name: 'Brentford' },
  { id: 33, name: 'Brighton and Hove Albion' },
  { id: 41, name: 'Chelsea' },
  { id: 18, name: 'Crystal Palace' },
  { id: 40, name: 'Everton' },
  { id: 28, name: 'Fulham' },
  { id: 19, name: 'Leeds United' }
];

const rounds = roundRobinTournament(teams, true);
rounds.forEach((fixtures, i_fixture) => {
  fixtures.forEach((matches, i_match) => {
    var div = document.createElement('div');
    div.classList.add('fixture');
    var h4 = document.createElement('h4');
    h4.innerHTML = 'Week: ' + ((i_match + 1) + (i_fixture * fixtures.length));
    div.appendChild(h4);
    matches.forEach((match) => {
      var p = document.createElement('p');
      p.innerHTML = match[0].name + ' vs ' + match[1].name;
      div.appendChild(p);
    });
    document.getElementById('schedule').appendChild(div);
  });
});
```
#### Results:
![Demo](https://raw.githubusercontent.com/chaskayu/round-robin-tournament-generator/main/demo.png)

## Feedback

If you have any feedback, please reach out to me at chaska.yu@gmail.com

