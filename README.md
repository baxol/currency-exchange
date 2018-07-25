# Currency exchange

Project for currency exchange with microservice architecture


##Structure
Whole project is devided into three modules:

- Forex currency microservice ( mock data )
- Currency conversion microservice ( based on forex microservice )
- Eureka server

##Tools used
- **Feign** using for proxing forex services
- **Ribbon** lets distribute one request from currency service to many of forex services
- **Eureka** naming server provide destination handling over all eureka clients 

##Essential advantage

`http://localhost:8100/currency-converter-feign/from/EUR/to/INR/quantity/10000`

######First request result
`{
  id: 10002,
  from: "EUR",
  to: "INR",
  conversionMultiple: 75,
  quantity: 10000,
  totalCalculatedAmount: 750000,
  port: 8000,
}`
######Second request result
`{
  id: 10002,
  from: "EUR",
  to: "INR",
  conversionMultiple: 75,
  quantity: 10000,
  totalCalculatedAmount: 750000,
  port: 8001,
}`

Difference is in port which means that data are taken alternately from forex service instances.