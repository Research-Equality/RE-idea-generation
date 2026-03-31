# Experimental Design Patterns

Choose testing strategies that distinguish competing hypotheses, not just generate more data.

## Selection Questions

- Is the hypothesis mechanistic, causal, correlational, or descriptive?
- Is the relevant system in vitro, in vivo, observational, or computational?
- What is the cheapest decisive test?
- What confound could fake the expected effect?

## Common Patterns

### Dose-Response

Use when the mechanism predicts graded effects as input changes.

### Gain / Loss of Function

Use when a component is claimed to be causally necessary or sufficient.

### Time Course

Use when ordering and timing are central to the explanation.

### Between-Subjects or Controlled Intervention

Use when you need a clean comparison between conditions.

### Within-Subjects / Repeated Measures

Use when individuals can serve as their own controls.

### Factorial Design

Use when the hypothesis depends on interactions between factors.

### Cohort / Longitudinal

Use when temporality matters and randomization is impossible.

### Case-Control

Use when outcomes are rare and exposures can be reconstructed.

### Computational or In Silico Testing

Use when the hypothesis is about system dynamics, parameter sensitivity, or large existing datasets.

## What Every Test Should Specify

- comparison or control
- measurement
- expected pattern if the hypothesis is true
- expected pattern if a rival hypothesis is true
- major confounds
- minimum signal that would justify a larger follow-up study
