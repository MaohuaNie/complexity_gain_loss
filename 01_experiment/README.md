# 01_experiment — the online experiment

Both studies were programmed in JavaScript with **jsPsych** and run online via
**JATOS** on Prolific. `online_experiment_jatos.html` is the main experiment
script used for the Study 2 data collection, included as an example of the
online experiments. It documents the task flow: instructions, comprehension
questions (with the £2 bonus gate), block structure (gain/loss, randomized
order), choice screens (F/J keys, 35-s response window), the rating phase,
the Berlin Numeracy Test and short Hagen Matrices Test, and the bonus
computation. Study 1 used the same structure with two risky gambles per trial
instead of a risky and a sure option.

The file references its JATOS study assets (jsPsych `dist/` bundle, CSS,
stimulus images, instruction pages), which are not included; the HTML alone
therefore documents, but does not run, the experiment. The stimulus
definitions the experiments draw from are provided as CSV tables in
`../data/stimuli/`.
