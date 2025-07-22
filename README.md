# Calculadora de Pedidos

Este proyecto es una aplicación Java básica que calcula el total de un pedido aplicando descuentos y costos de envío, utilizando **JUnit 5** y **Mockito** para las pruebas automatizadas.

## Tecnologías Utilizadas

- Java 17
- Maven
- JUnit 5.13.4
- Mockito 5.18.0

## Estructura del Proyecto

```bash
../calculadora-pedidos/
├── pom.xml
├── README.md
├── src
│   ├── main
│   └── test
└── target
    ├── classes
    ├── generated-sources
    ├── generated-test-sources
    ├── maven-status
    ├── surefire-reports
    └── test-classes
```

## Pruebas Automatizadas

Las pruebas están escritas con **JUnit 5** y utilizan **Mockito** para simular dependencias.

### Ejecutar pruebas

```bash
mvn clean test
```

## Cómo compilar el proyecto

```bash
mvn clean package
```

## Dependencias principales (`pom.xml`)

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.ejemplo</groupId>
  <artifactId>calculadora-pedidos</artifactId>
  <packaging>jar</packaging>
  <version>1.0-SNAPSHOT</version>
  <name>calculadora-pedidos</name>
  <url>http://maven.apache.org</url>

  <properties>
    <maven.compiler.source>17</maven.compiler.source>
    <maven.compiler.target>17</maven.compiler.target>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  </properties>
  
  <dependencies>
    <!-- JUnit Jupiter API -->
    <dependency>
      <groupId>org.junit.jupiter</groupId>
      <artifactId>junit-jupiter-api</artifactId>
      <version>5.13.4</version>
      <scope>test</scope>
    </dependency>

    <!-- JUnit Jupiter Engine -->
    <dependency>
      <groupId>org.junit.jupiter</groupId>
      <artifactId>junit-jupiter-engine</artifactId>
      <version>5.13.4</version>
      <scope>test</scope>
    </dependency>

    <!-- Mockito Core -->
    <dependency>
      <groupId>org.mockito</groupId>
      <artifactId>mockito-core</artifactId>
      <version>5.18.0</version>
      <scope>test</scope>
    </dependency>
</dependencies>

</project>
```

## Preguntas Finales - Calculadora de Pedidos

### 1. ¿Qué te ayudaron a identificar las pruebas unitarias?

Las pruebas unitarias ayudaron a identificar si los métodos individuales del servicio (`PedidoService`) funcionan correctamente de forma aislada. En particular, permitieron detectar errores de lógica en el cálculo total, aplicar correctamente los descuentos y verificar los valores esperados frente a una entrada conocida. Además, permitieron validar los resultados ante diferentes combinaciones de entradas sin depender de componentes externos.

---

### 2. ¿Cuál fue el beneficio de usar un mock para simular una dependencia?

El uso de un mock, específicamente de `DescuentoRepository`, permitió simular el comportamiento de una dependencia externa de forma controlada y predecible. Esto trajo beneficios clave:

- **Aislamiento**: Se puede probar `PedidoService` sin necesidad de una implementación real del repositorio.
- **Rapidez**: Las pruebas se ejecutan más rápido al no depender de consultas reales ni operaciones complejas.
- **Estabilidad**: Evita efectos secundarios o comportamientos inesperados del entorno real.

---

### 3. ¿Qué pasaría si se modifica la lógica de descuentos sin actualizar las pruebas?

Si se modifica la lógica de descuentos (por ejemplo, cambiando el algoritmo o el porcentaje aplicado) y no se actualizan las pruebas, estas probablemente **fallarán** al ejecutarse, indicando que los resultados esperados ya no coinciden con la nueva lógica. Esto es útil porque actúa como una red de seguridad para detectar **regresiones**. También puede provocar **falsos negativos** si no se ajustan correctamente las expectativas del test.

---

### 4. ¿Cómo escalamos esta estrategia para un sistema más grande?

Para escalar esta estrategia en sistemas más complejos, se deben seguir buenas prácticas como:

- **Separación de responsabilidades**: Mantener bien definidos los límites de cada clase o módulo.
- **Cobertura amplia**: Aumentar la cantidad y diversidad de pruebas (unitarias, de integración, E2E).
- **Mocks y stubs estratégicos**: Simular dependencias como servicios externos, bases de datos o APIs para pruebas rápidas y confiables.
- **Automatización**: Integrar las pruebas en un pipeline de CI/CD para ejecutarlas automáticamente ante cada cambio.
- **Uso de frameworks de testing** adecuados para cada capa del sistema.

Esto permite mantener calidad, rendimiento y confianza en sistemas grandes y distribuidos.

---

### Autor

Cristian Araya  
Proyecto de aprendizaje y automatización de pruebas Java.
