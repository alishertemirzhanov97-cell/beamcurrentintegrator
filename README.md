



| Nanoammeter PCB Signal            | STM32 Pin | Function                                                   |
| --------------------------------- | --------- | ---------------------------------------------------------- |
| Comparator Output                 | PB3       | Hardware trigger input for TIM2 one-pulse reset generation |
| Comparator Output (optional copy) | PE11      | Pulse counting input (EXTI interrupt)                      |
| Integrator Reset                  | PA0       | TIM2 CH1 output generating reset pulse                     |
| GND                               | GND       | Common ground                                              |
| USB                               | USB FS    | Data acquisition and control                               |
