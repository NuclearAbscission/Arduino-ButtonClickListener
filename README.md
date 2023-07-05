# Arduino-ButtonClickListener
The ButtonClickListener library provides an object-oriented approach to handle button click events in Arduino. It allows you to easily attach callback functions to individual buttons and execute custom code when a button is clicked.

## Installation

1- Download the ButtonClickListener library.
2- Extract the downloaded zip file.
3- Copy the extracted folder to the Arduino libraries directory.

## Usage
### Creating Button Objects

```cpp
#include <ButtonClickListener.h>

Button button1(c); // Pass the pin value when creating object of such type
Button button2(BUTTON_PIN_2); // Replace BUTTON_PIN_1 and BUTTON_PIN_2 with the actual pin numbers to which your buttons are connected.
```
### Attaching Callback Functions
After creating the button objects, you can attach callback functions to handle button click events.

```cpp
button1.onClick([]() {
  // Code to execute when button 1 is clicked
});

button2.onClick([]() {
  // Code to execute when button 2 is clicked
});
```
Replace the comments eith your desired code for each button.

### Checking Button State
In your main loop, call the checkState() method for each button object to check if a button is clicked.

```cpp
void loop() {
  button1.checkState();
  button2.checkState();

  // Other code in your loop
}
```

### Looping through a vector of your buttons for checking state

It is even better to loop through a ***vector*** of your buttons. But Arduino does not contain standard support for vectors, therefore you are encouraged to use another [library of mine](https://github.com/NuclearAbscission/Vector-library-for-Arduino)

```cpp
Vector<Button> buttons;     // this way we can loop through our vector of buttons
buttons.push_back(Button(pin1)); // our first button
buttons.push_back(Button(pin2)); // our second button and so on..

void loop() {
  for (int i = 0; i < buttons.size(); ++i) {
    auto& x = buttons[i];

    x.checkState();
  }

  // Other code in your loop
}
```

Make sure to replace comments with your existing code or any additional logic you need to run.

## Example
Here's an example usage of the ButtonClickListener library:

```cpp
#include <ButtonClickListener.h>

Button button1(2);
Button button2(3);

void setup() {
  Serial.begin(9600);

  button1.onClick([]() {
    Serial.println("Button 1 clicked");
  });

  button2.onClick([]() {
    Serial.println("Button 2 clicked");
  });
}

void loop() {
  button1.checkState();
  button2.checkState();

  // Other code in your loop
}
```
In this example, button objects are created for pins 2 and 3. Callback functions are attached to each button using lambda functions to print a message when clicked. The button states are checked in the main loop.

## Contributing
Contributions are welcome.

## License
This library is released under the MIT License.
