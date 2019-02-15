# spring-cloud-circuitbreaker-demo
Samples demonstrating how to using Spring Cloud Circuitbreaker

## Circuit Breaker Pattern

The basic idea behind the circuit breaker is very simple. You wrap a protected function call in a circuit breaker object, 
which monitors for failures. Once the failures reach a certain threshold, the circuit breaker trips, and all further calls
to the circuit breaker return with an error, without the protected call being made at all. 
Usually you'll also want some kind of monitor alert if the circuit breaker trips.


### States of the Circuit Breaker

The circuit breaker has three distinct states: Closed, Open, and Half-Open:

* Closed – When everything is normal, the circuit breaker remains in the closed state and all calls pass through to the services.
  When the number of failures exceeds a predetermined threshold the breaker trips, and it goes into the Open state.
* Open – The circuit breaker returns an error for calls without executing the function.
* Half-Open – After a timeout period, the circuit switches to a half-open state to test if the underlying problem still exists. 
  If a single call fails in this half-open state, the breaker is once again tripped. If it succeeds, the circuit breaker resets back to
  the normal, closed state. 


![Alt Text](https://www.ebayinc.com/assets/Uploads/Blog/2015/08/circuit_breaker_state_diagram.gif)

### Spring Circuit Breaker

* 1 Add the springframework.cloud:spring-cloud-starter-hystrix dependency to your build file.
* 2 Add the @EnableCircuitBreaker annotation to your main application class (typically the class with the @SpringBootApplication annotation on it).
* 3 Annotate with @HystrixCommand the methods in your @Service or @Component classes that you wish to protect.




---------------------------------------------------------------------

- https://spring.io/guides/gs/circuit-breaker/
- https://microservices.io/patterns/reliability/circuit-breaker.html
- https://martinfowler.com/bliki/CircuitBreaker.html
- https://techblog.constantcontact.com/software-development/circuit-breakers-and-microservices/
-
