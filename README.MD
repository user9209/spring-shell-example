# Spring Shell Example

11.08.2024

## Version

- Intelij Idea 2024.2
- Gradle 8.8
- Spring 3.3.2
- Java 21

## Spring Initializr

````
https://start.spring.io/#!type=gradle-project&language=java&platformVersion=3.3.2&packaging=jar&jvmVersion=21&groupId=com.example&artifactId=demo&name=demo&description=Demo%20project%20for%20Spring%20Boot&packageName=com.example.demo&dependencies=lombok,spring-shell
````


## Enable shell 3.3.x

Add to `src/main/resources/application.properties`

````
# https://docs.spring.io/spring-shell/reference/execution.html
spring.shell.interactive.enabled=true
spring.shell.script.enabled=true
````


## Default BUG

````
> Task :bootRun

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/

 :: Spring Boot ::                (v3.3.2)

2024-08-11T22:28:22.531+02:00  INFO 10524 --- [demo] [           main] com.example.demo.DemoApplication         : Starting DemoApplication using Java 21.0.4 with PID 10524
2024-08-11T22:28:22.531+02:00  INFO 10524 --- [demo] [           main] com.example.demo.DemoApplication         : No active profile set, falling back to 1 default profile: "default"
2024-08-11T22:28:23.113+02:00  WARN 10524 --- [demo] [           main] org.jline                                : Unable to create a system terminal, creating a dumb terminal (enable debug logging for more information)
2024-08-11T22:28:23.345+02:00  INFO 10524 --- [demo] [           main] com.example.demo.DemoApplication         : Started DemoApplication in 1.151 seconds (process running for 1.472)
shell:>
BUILD SUCCESSFUL in 2s
4 actionable tasks: 4 executed
````

### Fix BUG

Add to `build.gradle`

````
bootRun {
	standardInput = System.in
}
````