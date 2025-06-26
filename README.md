
# CoffeeMakerSimulation_Proteus

Project developed during the 3rd Trimester for the Computer Interfaces (https://www.fib.upc.edu/ca/estudis/graus/grau-en-enginyeria-informatica/pla-destudis/assignatures/CI) subject. It was implemented using Proteus 8 Pro and coded in C, applying concepts and elements learned throughout the course.




## Technical Specifications

* Coffee Grinder Digital Output: RA0
* Water Pump Digital Output: RA1
* Fan Digital Output with PWM: RE0
* Temperature Sensor: NTC sensor, connected to pin AN6.
* Water Level Sensor: Simulated with a 1kΩ potentiometer connected between 0V and 5V. Tank is empty when the sensor reads 0V. Low water level alarm triggers when the voltage drops below 1V. Sensor connected to AN7.
* Up Button: RC0 (equivalent to typing 'w' on the virtual terminal)
* Left Button: RC1 (equivalent to typing 'a' on the virtual terminal)
* Right Button: RC2 (equivalent to typing 'd' on the virtual terminal)
* Down Button: RC3 (equivalent to typing 'x' on the virtual terminal)
* Select Button: RC4 (equivalent to typing 's' on the virtual terminal)
* USART Serial Communication Tx1 Line: RC6
* USART Serial Communication Rx1 Line: RC7
* Grinder Activation Time: 10 seconds ± 5 seconds (-5s for mild coffee, +5s for strong coffee).
* Water Injector Activation Time: 15 seconds ± 5 seconds (-5s for short coffee, +5s for long coffee).
* Selected Coffee Temperature: 60ºC ± 10ºC (-10ºC for cold coffee, +10ºC for hot coffee).
* Temperature Error: T_selected - T_measured, (Proportional values are applied between these ranges)

    * If Temperature Error ≤ -5ºC → duty cycle = 100%.
    * If Temperature Error = 0ºC → duty cycle = 50%.
    * If Temperature Error ≥ 5ºC → duty cycle = 0%.



## UserManual

My coffee machine has 3 phases. The first is the initial phase, where you must press any button (if typing through the virtual terminal, only the letters w, a, s, d, x are functional) to proceed to the second phase.


The second phase involves choosing the type of coffee. To maintain a simple design, I decided to divide the coffee selection into 3 screens. In the first, you choose whether you want short or long coffee; in the second, you choose whether you want mild or strong coffee; and finally, you choose whether you want cold or hot coffee.


The third phase is when the coffee is served. On the screen, you can see a bar showing the progress along with a stopwatch indicating the remaining time. To simulate the grinder/water pump turning on, I've placed 2 LEDs where you can see when the grinder is being used and when the pump is in operation.


During Phase 1 and Phase 2, if we have a low water level, a message will appear that will persist as long as the water level is low. If, during Phase 1 and 2, the water level is 0, then everything blocks, and an error message appears. Until the water tank is refilled, we cannot return to the state we were in.

My code is structured using state machines, so that when a button is pressed, it checks which button was pressed, changes states if necessary, and updates the screen.
