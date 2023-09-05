# Automatic_Solar_Tracker

This project aimed to create an automatic solar tracker using a PID controller to optimize the alignment of a solar panel for maximum efficiency. The PID controller adjusts a PWM signal, which in turn controls the motor's speed and direction, aligning the panel based on feedback from two symmetrical LDRs positioned on either side of the panel. These LDRs detect deviations from the optimal position, enabling dynamic adjustments to enhance solar panel efficiency.

## Functionality

![solartracker_blockdiagram](https://github.com/Nuthya27/Automatic_Solar_Tracker/assets/111232856/612ec7e8-848e-4285-aa8b-78d53a77fdb2)

### Input
The solar tracker utilizes two LDR sensors positioned at opposite ends of the panel. These sensors measure the light intensity they receive, and the potential at the midpoint between them changes accordingly. By comparing this value to a set point (the value when both LDRs receive equal light), the system calculates the difference (error) between the two readings using a differential amplifier.

![st_input](https://github.com/Nuthya27/Automatic_Solar_Tracker/assets/111232856/d153d9c4-ee2c-4f13-9f87-bb3710b568d1)

### PID Control
The error obtained is fed into the PID control circuit. The PID control circuit acts as a feedback system that will adjust the panel’s orientation depending on the error calculated. It comprises of 3 operational amplifiers configured to perform proportional, integral and derivative operations.

  1. **Propotional** - The proportional part employs an inverting op-amp configuration with variable resistors to achieve the necessary gain for the error signal.
     
      ![st_p](https://github.com/Nuthya27/Automatic_Solar_Tracker/assets/111232856/f0baaf98-5446-493b-8d4b-37a3165a5f26)

  2. **Integral** - The integral part diminishes steady-state error by accumulating the error over time through an op-amp integrator with variable resistors.
     
     ![st_i](https://github.com/Nuthya27/Automatic_Solar_Tracker/assets/111232856/b3f0779f-6d30-40f3-af8b-a422b8cf9453)

  3. **Derivative** - The derivative component generates an output signal in proportion to the error's rate of change, effectively reducing overshoot and providing a smoother control signal. This is accomplished through an op-amp differentiator circuit with adjustable resistors.
     
     ![st_d](https://github.com/Nuthya27/Automatic_Solar_Tracker/assets/111232856/63253f59-4c65-4f29-8c04-fc1a5d2af5bb)

### Triangular Waveform Generation

The motor's rotation is controlled by a PWM signal, generated from a triangular waveform. This waveform creation involves first producing a square wave and then passing it through an integrator circuit. The circuit comprises a schmitt trigger circuit, functioning as a comparator, which provides saturated supply voltage outputs when the non-inverting input surpasses the inverting input. These outputs are then integrated for a finite duration in the integrator circuit. The integrator circuit's output is looped back into the schmitt trigger as input.

![st_triangle](https://github.com/Nuthya27/Automatic_Solar_Tracker/assets/111232856/f87ad1bc-3625-4485-a767-6f0ec4a9797e)

### Motor Dirve

The PID circuit output is compared with a triangular wave using two comparators to produce two PWM signals that vary in pulse width based on the error, and these inverted signals are then supplied to the motor driver.

![st_pwm](https://github.com/Nuthya27/Automatic_Solar_Tracker/assets/111232856/ff952823-3b21-418e-bae1-a5c993c8057f)

## Breadboard Implementation

![st_bb](https://github.com/Nuthya27/Automatic_Solar_Tracker/assets/111232856/6277ba81-fb20-4cc2-bfa1-6576ec66ca7c)

## Our Prototype

![20230227_134705](https://github.com/Nuthya27/Automatic_Solar_Tracker/assets/111232856/858cf0ef-411c-4a11-852d-cc1a49b5a3b5)


