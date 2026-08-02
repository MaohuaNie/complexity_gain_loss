# Data

## Files

| File | Contents |
|---|---|
| `study1/merged_data_study1.csv.gz` | Study 1: complete pre-exclusion trial-level export, 150 participants, one row per jsPsych event |
| `study2/merged_data_study2.csv.gz` | Study 2: same, 150 participants |
| `stimuli/study1_stimuli.csv` | Study 1 lottery definitions (gain-domain form; loss trials are sign-flipped) |
| `stimuli/study2_stimuli_gain.csv` / `study2_stimuli_loss.csv` | Study 2 lottery definitions per domain |
| `stimuli/study2_catch_gain.csv` / `study2_catch_loss.csv` | Study 2 high-EV-difference (attention) trials |

Read the merged data in R with `data.table::fread("study1/merged_data_study1.csv.gz")`
(needs the `R.utils` package).

The data contain no personal identifiers: participants are identified by
anonymous codes (`prolific_pid` holds `s1_p001` … `s2_p150`), and the
`prolific_study_id`, `prolific_session_id`, and `source_file` fields hold
correspondingly anonymized values.

## Column dictionary (merged data)

One row per jsPsych event (instructions, comprehension questions, choice
trials, surveys, …). `trial_type_label` identifies the event type; the choice
trials analysed in the paper have `trial_type_label == "test"`.

**jsPsych bookkeeping** — `rt` (ms, raw event RT), `stimulus`, `response`
(pressed key or survey JSON), `trial_type` (plugin), `trial_index`,
`time_elapsed`, `internal_node_id`, `start_time` (Unix ms), `subject`
(jsPsych-generated 8-character run ID), `source_file`.

**Browser/environment checks** — `success`, `timeout`, `failed_images`,
`failed_audio`, `failed_video`, `width`, `height`, `webaudio`, `browser`,
`browser_version`, `mobile`, `os`, `fullscreen`, `vsync_rate`, `webcam`,
`microphone`, `button_pressed`, `view_history`.

**Task variables (choice trials)** — `trial_type_label` (event type;
`"question"` = comprehension-question attempt, `"test"` = choice trial,
`"demo"` = demographics/feedback survey), `rt_trial` (ms, choice RT used in the
analyses), `feedback`, `after_warning`, `test_part` (block: `Gain`, `Loss`, or
practice), `test_chosen_option`, `risk_index` (left/right coding of which side
holds which option), `optionA_Stimulus` / `optionB_Stimulus` (displayed image
files), `complexity_option` (which option is complex, A or B), `EV_diff_level`,
`SD_diff_level`, `skew` (trial design levels; `skew == "catch"` marks Study 1
EV-dominant trials), `probA1`, `payA1`, `probA2`, `payA2`, `probB1`, `payB1`,
`probB2`, `payB2` (outcome distributions), `F`, `J` (JSON of the gamble mapped
to each response key).

**Study 2 rating phase** — `question_order`, `option_certainty`,
`option_complexity`, `source_pair`, `rated_image`, `rated_filename`,
`complexity_rating`, `confidence_rating` (1–7 Likert responses for perceived
complexity and value certainty).

**Cognitive-ability tests** — `BNT1_answer` … `BNT4_answer`, `accuracy_BNT`
(Berlin Numeracy Test), `option`, `accuracy_HMT` (short Hagen Matrices Test).

**Payment** — `total_bonus`, `total_bonus_no_response` (final bonus in
experimental units/GBP as computed by the experiment).

Demographics (age, gender, education) and free-text feedback are stored as
JSON in the `response` column of the `trial_type_label == "demo"` rows; the
analysis notebooks show how to parse them.

## Stimulus tables

`study1_stimuli.csv`: one row per gamble pair — outcome probabilities/payoffs
for options A and B (`PA1`,`OA1`,…,`PB2`,`OB2`), their moments (`EVA`, `EVB`,
`SDA`, `SDB`, `SkewA`, `SkewB`) and the design levels (`EVD_level`,
`SDD_level`, `Skew_level`). Loss-domain trials are the sign-flipped versions.

`study2_stimuli_*.csv`: one row per trial — risky-option probability/outcome
and sure-option outcome (`P_A1`,`O_A1`,`P_B1`,`O_B1`), the arithmetic-expression
components used for the complex presentation (`complex_*` columns), moments and
design levels. Catch files list the high-EV-difference attention trials.
