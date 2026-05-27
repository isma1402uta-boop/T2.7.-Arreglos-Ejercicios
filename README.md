# Sistema de Gestión y Análisis de Calificaciones (C++) 📊🎓

[cite_start]Este repositorio contiene el diseño, pseudocódigo e implementación en **C++** de una herramienta interactiva por consola desarrollada para la automatización, procesamiento estadístico y consulta de calificaciones de exámenes finales en el ámbito educativo[cite: 144, 148].

[cite_start]El proyecto integra de forma progresiva todas las fases de la metodología de desarrollo de software estructurado: análisis del problema, diseño lógico mediante diagramas de flujo y pseudocódigo (PSeInt), codificación modular y validación con pruebas de escritorio[cite: 150, 155].

---

## 🏛️ Información Institucional
* [cite_start]**Institución:** Universidad Técnica de Ambato (UTA) [cite: 130]
* [cite_start]**Facultad:** Facultad de Ingeniería en Sistemas, Electrónica e Industrial [cite: 130]
* [cite_start]**Carrera:** Carrera de Software [cite: 131]
* [cite_start]**Asignatura:** Algoritmos y Lógica de Programación [cite: 143]
* [cite_start]**Ciclo Académico:** Enero 2026 - Julio 2026 [cite: 132]
* **Docente:** Ing. [cite_start]José Caiza, Mg. [cite: 143]
* [cite_start]**Estudiante:** Sánchez Lema Isaac Adrián [cite: 142]

---

## 🚀 Características Principales (Módulos)

[cite_start]El sistema está estructurado mediante un menú principal interactivo controlado por consola que gestiona tres funcionalidades esenciales de manera independiente[cite: 149, 183]:

1. **Módulo 1: Registrar Calificaciones (`registrarCalificaciones`)** 📝
   * [cite_start]Permite el ingreso dinámico del número total de alumnos ($n \le 50$)[cite: 222, 417].
   * [cite_start]Almacena simultáneamente los nombres completos y las calificaciones finales en **arreglos paralelos** (`nombres[]` y `notas[]`)[cite: 173, 416].
   
2. **Módulo 2: Reporte Estadístico (`mostrarReporte`)** 📈
   * [cite_start]Procesa automáticamente la información recopilada mediante métricas de estadística descriptiva elemental[cite: 198].
   * [cite_start]Calcula y despliega el **promedio general del grupo** ($\overline{x}=\Sigma notas[i]/n$)[cite: 31, 304].
   * [cite_start]Determina la frecuencia absoluta con el número total de estudiantes **aprobados** (nota $\ge 7.0$) y **reprobados** (nota $< 7.0$)[cite: 31, 423].

3. **Módulo 3: Búsqueda Secuencial (`buscarEstudiante`)** 🔍
   * [cite_start]Implementa un algoritmo de **búsqueda lineal/secuencial** para localizar la información de un alumno específico ingresando su nombre completo[cite: 188, 189].
   * [cite_start]Muestra ordenadamente el nombre, la nota obtenida y el estado académico ("Aprobado" o "Reprobado") del estudiante, gestionando de forma correcta los casos en los que el alumno no se encuentre registrado[cite: 219, 403].

---

## 📐 Análisis del Problema

### Entradas del Sistema
| # | Dato | Tipo | Descripción |
|---|---|---|---|
| 1 | `n` | `int` | [cite_start]Número total de estudiantes a registrar [cite: 41] |
| 2 | `nombres[i]` | `string` | [cite_start]Nombre completo de cada estudiante [cite: 41] |
| 3 | `notas[i]` | `float` | [cite_start]Calificación del examen final (rango: 0.0 - 10.0) [cite: 41] |
| 4 | `nombreBuscar` | `string` | [cite_start]Nombre del estudiante a localizar en la búsqueda [cite: 41] |
| 5 | `opcion` | `int` | [cite_start]Selección del menú principal (0-3) [cite: 41] |

### Restricciones del Sistema
* [cite_start]El tamaño máximo del arreglo se fija en $MAX=50$ estudiantes[cite: 47].
* [cite_start]Las calificaciones válidas están estrictamente en el rango $[0.0, 10.0]$[cite: 48].
* [cite_start]La búsqueda es *case-sensitive* (distingue mayúsculas de minúsculas)[cite: 48].
* [cite_start]No se puede mostrar el reporte ni realizar búsquedas sin haber registrado datos previamente[cite: 49].

---

## 📝 Algoritmo en Pseudocódigo (PSeInt)

```pascal
Proceso GestionCalificaciones
    // Definición e inicialización de variables
    Definir n, i, aprobados, reprobados Como Entero
    Definir suma, promedio, notas Como Real
    Definir nombres Como Cadena
    Definir buscar Como Cadena
    Definir encontrado Como Logico
    
    Dimension nombres [100]
    Dimension notas[100]
    
    suma <- 0
    aprobados <- 0
    reprobados <- 0
    
    Escribir "Ingrese la cantidad de estudiantes:"
    Leer n
    
    // Ciclo para registrar los datos
    Para i<-1 Hasta n Hacer
        Escribir "Ingrese el nombre del estudiante ", i, ":"
        Leer nombres[i]
        Escribir "Ingrese la nota del estudiante ", i, ":"
        Leer notas[i]
        suma <- suma + notas[i]
        
        // Validación de aprobación (nota mínima: 7)
        Si notas[i] >= 7 Entonces
            aprobados <- aprobados + 1
        Sino
            reprobados <- reprobados + 1
        FinSi
    FinPara
    
    promedio <- suma / n
    
    // Despliegue de resultados estadísticos
    Escribir ""
    Escribir "====== REPORTE ESTADISTICO ======"
    Escribir "Promedio general: ", promedio
    Escribir "Aprobados: ", aprobados
    Escribir "Reprobados: ", reprobados
    Escribir "================================="
    Escribir ""
    
    // Módulo de búsqueda de estudiantes
    Escribir "Ingrese el nombre del estudiante a buscar:"
    Leer buscar
    encontrado <- Falso
    
    Para i <- 1 Hasta n Hacer
        Si nombres[i] = buscar Entonces
            encontrado <- Verdadero
            Escribir ""
            Escribir "--- Estudiante Encontrado ---"
            Escribir "Nombre: ", nombres[i]
            Escribir "Nota: ", notas[i]
            Si notas[i] >= 7 Entonces
                Escribir "Estado: Aprobado"
            Sino
                Escribir "Estado: Reprobado"
            FinSi
            Escribir "-----------------------------"
        FinSi
    FinPara
    
    Si encontrado = Falso Entonces
        Escribir "El estudiante no se encuentra registrado."
    FinSi
FinProceso
