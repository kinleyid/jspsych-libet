# UPDATE, NOV 2021
The new and improved version of this plugin, which is compatible with jsPsych 7.0, can be found at https://github.com/jspsych/jspsych-contrib/tree/main/packages/plugin-libet-intentional-binding. I'll leave this version here for now, but the documentation for the new version is much more complete.

**Note, May 2023**: Two versions of the plugin are now available for compatibility with legacy jsPsych versions 6.1.0 and 6.3.0.

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
