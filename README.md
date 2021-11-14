# Note!
As of Nov 2021, I am in the process of adding this repository to jspsych-contrib (and have updated it for compatibility with jsPsych 7). Once I do, I will hyperlink to the updated repository here.

# jspsych-libet
A jsPsych plugin for measuring intentional binding using a Libet clock.

## Parameters
| Parameter | Type | Default Value | Description |
|-|-|-|-|
| cond_bo | string | 'baseline' | Specifies whether the condition is "baseline" or "operant" |
| cond_kt | string | 'key' | Specifies whether the condition is "key" or "tone" |
| tone_file | audio file | *undefined* | The tone file to be played |
| hand_est | boolean | true | If true, the participant will produce their estimate by moving the clock hand themselves |
| instructions | HTML string | '' | if `hand_est` is `true`, participants will be shown these instructions during estimation |

## Data generated
| Name | Type | Value |
|-|-|-|
| keypress_ms | numeric | The time, in milliseconds, at which the participant pressed a key |
| theta_keypress | numeric | The angle of the clock hand, in radians, when the participant pressed a key |
| tone_ms | numeric | The time, in milliseconds, at which the tone began to play |
| theta_tone | numeric | The angle of the clock hand, in radians, when the tone began to play |

## Examples

### Allowing the participant to move the clock hand to estimate the time of a tone
```
var trial = {
    type: 'libet',
    tone_file: 'tone.mp3',
    cond_bo: 'operant',
    cond_kt: 'tone',
    hand_est: true
};
```

### Trial with written estimate of clock location at time of tone
```
var trial = {
    type: 'libet',
    tone_file: 'tone.mp3',
    cond_bo: 'operant',
    cond_kt: 'tone',
    hand_est: false
};
var estimation = {
  type: 'survey-text',
  questions: [
    {prompt: "What number was the clock hand pointing at when the tone played?"}
  ],
};
```
