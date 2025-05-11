## Model mikrokontrolera zarządzającego kabiną windy

#### Opis projektu:

System składa się z przycisków windy (piętra, otwieranie/zamykanie drzwi, oraz alarm), multipleksera, sensora odległości na podczerwień zamontowanego w drzwiach, linii telefonicznej do alarmue i sensorów wykrywających usterki, elementu zarządzającego logiką, oraz kontrolera który przetwarza sygnał cyfrowy na działanie silnika windy/silnik podpięty do drzwi.


#### Data [Data]

- `ObjectInDoorData` odczyt wykrywacza obiektów w drzwiach
- `CurrentAltitudeData` obecna wysokość bezwzględna
- `NextStopData` następne piętro do którego jedzie winda
- `FloorsAvailableData` dobrze uporządkowana lista pięter
- `FloorsHeightData` mapuje dane piętro na bezwzględną wysokość
- `FloorsSelectedData` zbiór zawierający wszystkie obecnie aktywne przyciski pięter
- `MainMotorCommandData` w zakresie -1 do 1, napięcie prądu zasilajacego główny silnik windy
- `EmergencyData` boolean, informuje o tym czy winda jest zepsuta i powinna przestać się poruszać

- Cabin motor
Door motor
Floor sensors
Cabin position sensor
Call buttons (on floors)
Cabin buttons (inside the elevator)
Display panel
Alarm system
Weight sensor
Emergency stop button
Threads:
Elevator Movement Thread - Handles the movement of the elevator between floors.
Door Control Thread - Manages the opening and closing of doors.
Request Processing Thread - Processes user requests and updates the request queue.
Sensor Monitoring Thread - Continuously monitors sensors for position and safety.
Display Update Thread - Updates the display with the current floor and direction.
Event Handling Thread - Handles asynchronous events like emergency stops or alarms.
Processes:
Request Handling Process - Adds requests to the queue and prioritizes them.
Movement Control Process - Determines the next floor and controls the motor.
Door Operation Process - Ensures doors open/close safely.
Safety Monitoring Process - Monitors sensors for safety violations (e.g., overload, obstruction).
Event Dispatch Process - Dispatches events to appropriate threads.
Idle State Process - Keeps the elevator idle when no requests are pending.
