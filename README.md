# 👨‍💻 Álvaro Murillo Puchalt
> 🎓 Alumno de DAM · 💻 Apasionado por la informática y los coches · 📍 Valencia · 19 años

![banner](./encabezado.png)

---

## 🧠 Quién soy
Hola 👋 — soy **Álvaro Murillo Puchalt**, tengo **19 años** y soy de **Valencia (España)**.  
Actualmente estudio **Desarrollo de Aplicaciones Multiplataforma (DAM)** y me apasiona todo lo relacionado con la informática: cómo funcionan las cosas por dentro, cómo se crean y cómo mejorarlas.  

Además, tengo una gran afición por el **mundo del motor** 🚗 — me fascina la tecnología que hay detrás de los coches, desde su electrónica hasta los sistemas de asistencia o gestión de datos.

Me considero una persona **curiosa, constante y con ganas de aprender**, que disfruta resolviendo problemas reales y mejorando un poco cada día.

---

## ❤️ Qué me gusta
- 💡 Programar y diseñar soluciones útiles.
- 🧩 Entender cómo se conectan las piezas en un sistema.
- 🔧 Experimentar con nuevas tecnologías y aprender de los errores.
- 🚘 Aplicar la informática al mundo del motor y la ingeniería.
- 🤝 Trabajar en equipo, compartir conocimiento y documentar lo aprendido.

---

## ✨ Highlights

### 🧩 Problema a resolver
Crear una pequeña utilidad en **Java** que modele distintos coches y calcule su autonomía y consumo estimado para un viaje.  
Un ejercicio sencillo, pero que demuestra conceptos de **orientación a objetos**, **buenas prácticas** y **claridad en el código**.

---

### ⚙️ Tecnologías utilizadas
- 🟦 **Java 17+**
- ☕ Programación orientada a objetos (POO)
- 📂 Colecciones (`ArrayList`)
- 🧮 Cálculos simples con formatos de salida legibles

---

### 💻 Código (ejemplo en Java)

```java
// src/Main.java
import java.util.ArrayList;
import java.util.List;

/**
 * Ejemplo didáctico: modela coches y calcula autonomía y consumo.
 * Compilar:
 *   javac src/Main.java
 * Ejecutar:
 *   java -cp src Main
 */
class Car {
    private String model;
    private double tankCapacityLiters; // litros
    private double consumptionPer100km; // litros/100 km

    public Car(String model, double tankCapacityLiters, double consumptionPer100km) {
        this.model = model;
        this.tankCapacityLiters = tankCapacityLiters;
        this.consumptionPer100km = consumptionPer100km;
    }

    public String getModel() {
        return model;
    }

    public double rangeKm() {
        return tankCapacityLiters * (100.0 / consumptionPer100km);
    }

    public double litersForDistance(double distanceKm) {
        return (consumptionPer100km / 100.0) * distanceKm;
    }

    @Override
    public String toString() {
        return String.format("%s — tanque: %.1f L · consumo: %.2f L/100km · autonomía: %.0f km",
                model, tankCapacityLiters, consumptionPer100km, rangeKm());
    }
}

public class Main {
    public static void main(String[] args) {
        List<Car> garage = new ArrayList<>();
        garage.add(new Car("Compacto X", 45.0, 6.5));
        garage.add(new Car("Familiar Y", 60.0, 7.8));
        garage.add(new Car("Deportivo Z", 50.0, 9.5));

        System.out.println("=== 🚗 Gestor de coches ===\n");

        for (Car car : garage) {
            System.out.println(car);
        }

        double tripDistance = 420.0; // ejemplo: Valencia -> destino
        System.out.printf("\nEstimación para un viaje de %.0f km:\n", tripDistance);
        for (Car car : garage) {
            double liters = car.litersForDistance(tripDistance);
            System.out.printf(" - %s: %.1f L necesarios (%.1f tanques)\n",
                    car.getModel(), liters, liters / car.tankCapacityLiters);
        }
    }
}
