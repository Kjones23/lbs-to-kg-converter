# lbs-to-kg-converter - DESIGN

## Overview
This project is a Node.js application deployed on an EC2 instance and reverse-proxied via Nginx. It converts pounds (lbs) to kilograms (kg) using the formula: `kg = lbs * 0.45359237`.

## Architecture
- **Node.js server**: Handles `/convert?lbs=<value>` requests.
- **Nginx**: Reverse proxy listening on ports 80 and forwarding to Node.js on port 8080.
- **AWS EC2**: Hosts the Node.js server and Nginx.

## Endpoints
- `GET /convert?lbs=<value>`  
  - **Success**: Returns JSON with lbs, kg, and formula.
  - **Error Handling**:
    - Missing parameter → 400 Bad Request
    - Non-numeric or negative lbs → 400 or 422

## Security
- **Security Group Rules**:
  - SSH (TCP 22) allowed only from your IP
  - HTTP (TCP 80) open to all
  - Node.js port (TCP 8080) restricted to your IP

## Deployment
1. Install dependencies: `npm install`
2. Start server: `node server.js`
3. Test with curl: `curl http://<EC2-PUBLIC-IP>/convert?lbs=150`

## Notes
- Node.js handles validation and error codes.
- Nginx ensures requests reach Node.js securely.
