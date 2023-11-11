# Game Class Documentation

The `Game` class represents a simulation of a hospital game involving patients and nurses. 

## Game description

A team of nurses is responsible for attending to incoming patients throughout a workday. The timing of patient arrivals follows an exponential distribution, and their stay is uniformly sampled from $\{1,2\}$.

Upon a patient's arrival, each nurse must decide to either accept ($A$) the patient for treatment or reject ($R$) them. The nurses' decision-making order is determined by their experience levels, with higher experience granting greater decision priority (e.g., $E_1 > E_2 > E_3$).

In situations where all nurses reject a patient, a policy of forced assignment is implemented. The patient is then assigned to the nurse with the fewest current patients, and she incurs a penalty proportional to her experience level. In cases of a tie, the patient is assigned to the nurse with the highest level of experience, and she receives the penalty.

## Initialization

The class is initialized with the following parameters:

- `n_patients`: The number of patients arriving at the hospital.
- `n_enf`: The number of nurses.
- `p_short_stay`: The probability that a patient will have a short stay.
- `arrival_rate`: The rate at which patients arrive at the hospital.

## Methods

The class has the following methods:

- `__init__`: Initializes the class with the given parameters.
- `reset_patients`: Generates the patients arriving at the hospital.
- `run_exp`: Executes the nurse game. It takes a function as a parameter which determines the actions of the nurses.
- `fix_utilities`: Calculates the utility of the nurses, which is a combination of the utility over time and the penalty for rejecting patients.
- `summarize_utilities`: Summarizes the utilities of the nurses at each period where a patient assignment decision was made.
- `plot_pagos`: Plots the payment function of the agents over time.
- `plot_pacientes`: Plots the schedule of patients over time.

## Attributes

The class has the following attributes:

- `n_patients`: The number of patients.
- `n_enf`: The number of nurses.
- `p_short_stay`: The probability of a patient having a short stay.
- `arrival_rate`: The patient arrival rate.
- `experience_weight`: The experience weight of the nurses.
- `patient_kind_stay`: The type of stay for each patient (short or long). Created using the `p_short_stay` probabilities.
- `patient_entry`: The entry time for each patient.
- `patient_stay`: The stay length for each patient.
- `patient_exit`: The exit time for each patient.
