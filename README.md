# SFML Setup on MacOS - Compile on Command Line - No XCode

### Requirements
1. XCode needs to be installed to get compilers first (ie. clang, g++). It can be installed via AppStore.
2. You need sfml library which you can get the one I uploaded to this repository(v2.6.1)
```bash
$ git clone https://github.com/cakirburak/SFML-Setup-on-MacOS.git
```

### Setup
1. Go into the sfml library
```bash
$ cd SFML-Setup-on-MacOS/sfml/2.6.1/
```
2. Copy the sfml libraries to the folder where standard libraries are;
```bash
$ sudo cp -r lib/* /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk/usr/lib
```
3. Copy the sfml includes to the folder where standard includes are;
```bash
$ sudo cp -r include/* /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk/usr/include
```
After completing these steps you are ready to go!

### Example Code and Compile
- Create a file named `main.cpp` and get the code below
```cpp
#include <SFML/Graphics.hpp>

int main()
{
    sf::RenderWindow window(sf::VideoMode(200, 200), "SFML works!");
    sf::CircleShape shape(100.f);
    shape.setFillColor(sf::Color::Green);

    while (window.isOpen())
    {
        sf::Event event;
        while (window.pollEvent(event))
        {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        window.clear();
        window.draw(shape);
        window.display();
    }

    return 0;
}
```
- Compile and Run
```bash
$ g++ main.cpp -o sfml-app -lsfml-graphics -lsfml-window -lsfml-system -lsfml-audio
$ ./sfml-app
```
## Happy Coding!
