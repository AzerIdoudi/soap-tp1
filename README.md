implement the new functions (Modulo, Power, and TemperatureService) in this lab, we followed a three-step process to extend the existing SOAP service:

1. WSDL Update (calculator.wsdl)
We first modified the service contract to declare the new operations. For each function, we defined:

Messages: Input and output structures (e.g., ModuloRequest and ModuloResponse).
PortType: Added the new operation names so the server and client know they exist.
Binding: Mapped these operations to the SOAP protocol.
2. Server Logic (server.js)
We expanded the calculatorService object in the server code to include the actual JavaScript logic:

Modulo: Used the % operator and added a check to prevent division by zero (throwing a SOAP Fault).
Power: Implemented using Math.pow(args.a, args.b) or the ** operator.
TemperatureService: 
F = C × 9/5 + 32
C = (F - 32) × 5/9
K = C + 273.15

3. Client Consumption (client.js)
Finally, we updated the client to test the new functionality:

We used await client.OperationNameAsync({ ... }) to call the new endpoints.
We logged the results to the console to verify that the server was correctly processing the new math and conversion logic.

"
You can test your SOAP service using Postman:
• Create a new POST request
• URL: http://localhost:8000/calculator
• Header: Content-Type: text/xml
Body (raw XML) pour l'addition :
<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:tns="http://example.com/calculator">
 <soap:Body>
 <tns:CalculatorRequest>
 <tns:a>15</tns:a>
 <tns:b>7</tns:b>
 </tns:CalculatorRequest>
 </soap:Body>
</soap:Envelope>
"
