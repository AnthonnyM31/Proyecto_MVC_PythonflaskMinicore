# 🏢 Sistema Core de Comisiones Pro - Flask MVC (Tarea 4: Ingeniería Web)

## 👤 Información del Proyecto
| Concepto | Detalle |
| :--- | :--- |
| **Desarrollador:** | Anthonny Mosquera y Juanjose Villalba|
| **Universidad / Curso:** | UDLA / Ingeniería Web |
| **Proyecto Base:** | Minicore - Sistema de Comisiones de Ventas Flask MVC |
| **Link del Deploy (Render):** | **[PENDIENTE: Insertar URL Pública de Render aquí]** |
| **Link Video Explicativo:** | **[PENDIENTE: Insertar URL de YouTube aquí]** |

---

## 📋 Arquitectura MVC Implementada

El proyecto sigue el patrón **Modelo-Vista-Controlador (MVC)** utilizando Python Flask.

| Componente | Archivos Clave | Función Principal |
| :--- | :--- | :--- |
| **📊 MODEL (Lógica y Datos)** | `app.py` (Lógica de `calcular_comision`), `ventas.db` | Contiene la lógica de negocio (reglas de comisión) y gestiona la persistencia de datos en SQLite. |
| **🎮 CONTROLLER (Rutas y API)** | `app.py` (Rutas Flask) | Actúa como intermediario, manejando las rutas (`@app.route`), coordinando la solicitud de datos al Modelo y preparando la respuesta para la Vista. |
| **🎨 VIEW (Interfaz de Usuario)** | `index.html`, `styles.css`, `script.js` | Presenta los datos al usuario. `script.js` maneja la interacción AJAX (filtrado y adición de ventas). |

---

## 🚀 Personalización y Aporte Individual (Requisito Tarea 4)

### 1. Funcionalidad: Regla "Premium Plus" (Modificación en `app.py`)
Se modificó la lógica de negocio para incluir un nuevo nivel de incentivo al vendedor:
* **Nueva Regla:** **Premium Plus (18% de comisión para ventas superiores a $15,000)**.
* **Impacto:** Se ajustó la regla anterior (`Premium`) y se codificó la nueva regla dentro de la función `calcular_comision`.

### 2. Diseño y Branding (Modificación en `index.html` y `styles.css`)
* Se agregó un **Banner de Bienvenida** (`.welcome-banner`) en la parte superior de la interfaz para personalizar el *branding*.
* El banner incluye la autoría: **Desarrollado por Anthonny Mosquera**.

---

## 🎯 Guía de Uso Local (Para Colaboradores y Pruebas)

### 1. Estructura Requerida
Asegúrese de que el proyecto tenga esta estructura exacta (importante para evitar errores de mayúsculas/minúsculas):

comisiones-flask-mvc/
├── app.py                 # (Controlador/Modelo): Aplicación principal Flask.
├── requirements.txt       # (Dependencias): Lista de librerías Python necesarias (Flask, gunicorn).
├── Procfile               # (Deploy): Comando de inicio para el servidor en Render.
├── ventas.db              # (Modelo): Base de datos SQLite que almacena Vendedores, Reglas y Ventas.
├── templates/             # (Vista): Contiene las plantillas HTML (Jinja2).
│   └── index.html         # Plantilla principal de la interfaz de usuario.
└── static/                # (Vista): Contiene los recursos estáticos.
    ├── styles.css         # Estilos CSS de la interfaz (incluyendo tu personalización).
    └── script.js          # JavaScript del lado cliente (maneja la lógica de la vista y AJAX).



### 2. Instalación y Ejecución
1.  **Abrir Terminal:** Navegue a la carpeta principal del proyecto (`comisiones-flask-mvc`).
2.  **Instalar Dependencias:** Ejecute (solo una vez):
    ```bash
    pip install -r requirements.txt
    ```
3.  **Ejecutar la Aplicación:** Ejecute Flask:
    ```bash
    python app.py
    ```
4.  **Abrir:** Acceda a `http://localhost:5000` en su navegador.

### 3. Pruebas de Comisiones Clave
Para verificar la regla personalizada, siga estos pasos:
1.  Vaya a **"Agregar Nueva Venta"**.
2.  Agregue una venta con un **Monto de $20,000** (y cualquier fecha reciente).
3.  Filtre las ventas para ese rango.
4.  La fila de la venta de $20,000 debe mostrar: **Comisión: $3,600.00** y **Regla Aplicada: Premium Plus**.

---

## 📝 Retrospectiva y Proceso de Desarrollo (Post-Mortem)

Este proyecto implicó la adaptación de un código base, enfrentando desafíos comunes en la configuración de entornos.

### Desafíos Superados
| Desafío / Problema | Causa Raíz | Solución Aplicada | Lección Aprendida |
| :--- | :--- | :--- | :--- |
| **Errores de Comandos** | Sintaxis incorrecta de `mkdir` y `touch` en PowerShell, generando errores `PositionalParameterNotFound`. | Se optó por la **creación manual de carpetas/archivos** y el uso exclusivo de `pip install` en la terminal, minimizando errores. | La creación de proyectos debe ser robusta ante las idiosincrasias de la terminal (PowerShell vs. Bash). |
| **Configuración para Render** | Necesidad de preparar el entorno para un servidor de producción (Gunicorn) y el puerto dinámico. | Se agregó `gunicorn` a `requirements.txt` y se creó el `Procfile` (`web: gunicorn app:app`). En `app.py`, se implementó `os.environ.get('PORT', 5000)`. | El *deploy* en la nube requiere comandos de inicio explícitos y manejo del puerto del host. |

### Conclusión

El proyecto es una demostración exitosa de la aplicación del patrón MVC en Flask. Se logró implementar una mejora funcional compleja (Regla de Negocio) y se superaron los desafíos de configuración de entorno, dejando el sistema listo para el entorno de producción en Render.

---
