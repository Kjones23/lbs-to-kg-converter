# lbs-to-kg-converter
Project 1 CS 454

A simple Node.js web service that converts pounds (lbs) to kilograms (kg). Accepts a `lbs` query parameter and returns JSON with the conversion result.

# Install dependencies
npm install

# Start the server
node server.js

# Test with curl
curl http://3.144.150.134/convert?lbs=150

## Test Cases

- `curl http://3.144.150.134/convert?lbs=0` → `{"lbs":0,"kg":0,"formula":"kg = lbs * 0.45359237"}`
- `curl http://3.144.150.134/convert?lbs=0.1` → `{"lbs":0.1,"kg":0.045359,"formula":"kg = lbs * 0.45359237"}`
- `curl http://3.144.150.134/convert?lbs=-5` → `422 error`
- `curl http://3.144.150.134/convert` → `400 error`
- `curl http://3.144.150.134/convert?lbs=NaN` → `400 error`
- 
## Screenshots
### Successful curl request
![0 lbs](Screenshots/zeroPounds.png)
![Small number](Screenshots/smallNumber.png)

### Error cases
![422 Error](Screenshots/fourTwoTwoError.png)
![400 Error](Screenshots/fourHundredError.png)
![400 Error alternative](Screenshots/fourHundredErrorTwo.png)


## Public Endpoint & Security Group

**Public Endpoint:** `http://3.144.150.134` (your Node.js service runs on port 80/8080)

**Security Group Summary:**

| Protocol | Port | Source    | Purpose                       |
|----------|------|-----------|-------------------------------|
| TCP      | 22   | 0.0.0.0/0 | SSH access (login via PuTTY) |
| TCP      | 80   | 0.0.0.0/0 | HTTP requests to Node service |
| TCP      | 8080 | 0.0.0.0/0 | Alternative Node port (if used) |
