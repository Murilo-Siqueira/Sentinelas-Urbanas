# Arduino BME280 Environmental Monitor

Sentinelas Urbanas

This project displays environmental data (temperature, humidity, and pressure) from a BME280 sensor connected to Arduino in a web interface. The Arduino also displays the data on a 16x2 LCD screen.

## Project Structure

- `index.js` - Node.js API that communicates with Arduino via serial port
- `index.html` - Web interface that displays the sensor data
- `BME280-LCD16x2/BME280-LCD16x2.ino` - Arduino code for the BME280 sensor with LCD display

## Requirements

1. Node.js installed
2. Arduino with BME280 sensor and 16x2 LCD connected
3. Adafruit BME280 library installed in Arduino IDE
4. LiquidCrystal_I2C library for LCD

## Configuration

1. **Install Node.js dependencies:**
   ```bash
   npm install
   ```

2. **Upload code to Arduino:**
   - Open `BME280-LCD16x2/BME280-LCD16x2.ino` in Arduino IDE
   - Select the correct board and port
   - Upload the code to Arduino

3. **Configure COM port:**
   - Check the COM port of your Arduino in Arduino IDE (Tools > Port)
   - Update the COM port in `index.js` if necessary (default is COM8)

## Execution

1. **Start the server:**
   ```bash
   node index.js
   ```

2. **Access the web interface:**
   - Open the browser at `http://localhost:3000`

## Development Mode

To test without Arduino connected:
1. In `index.js`, change `modoDesenvolvimento` to `true`
2. Start the server normally
3. The system will generate simulated environmental data

## Functionality

- The Arduino reads temperature, humidity, and pressure from the BME280 sensor every 4 seconds
- The data is displayed on the 16x2 LCD, alternating between temperature/humidity and pressure screens
- The server Node.js listens to the serial port and updates the sensor values
- The web interface updates automatically every 2 seconds
- Data is sent via serial in the format: "temperature,humidity,pressure"
