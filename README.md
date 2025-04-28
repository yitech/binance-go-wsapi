# binance-go-wsapi
The websocket API client in Binance feature

## General API Information

### Base Endpoints
- Production: `wss://ws-api.binance.com:443/ws-api/v3`
  - Alternative port: `9443` is available if you experience issues with port `443`
- Testnet: `wss://ws-api.testnet.binance.vision/ws-api/v3`

### Connection Information
- Connection validity: 24 hours maximum
- Expect disconnection after the 24-hour mark
- Responses are in JSON format by default (SBE format available, see SBE FAQ page)

### WebSocket Protocol Details
- Server sends ping frames every 20 seconds
- Client must respond with a pong frame (with copy of ping's payload) within one minute
- Connection will be disconnected if pong is not received within one minute
- Unsolicited pong frames are allowed but won't prevent disconnection
- Recommended to use empty payload for unsolicited pong frames

### Data Formatting
- Lists are returned in chronological order (unless specified otherwise)
- Timestamps in JSON responses:
  - Default: milliseconds in UTC
  - Microseconds available by adding `timeUnit=MICROSECOND` or `timeUnit=microsecond` parameter
- Timestamp parameters (startTime, endTime, timestamp) accept both milliseconds and microseconds
- All field names and values are case-sensitive

### Additional Information
- For enums and term clarification, please refer to SPOT Glossary
