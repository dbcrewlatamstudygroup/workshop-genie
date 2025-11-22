# 🚀 AI/BI en acción con Databricks: Potencia tus datos con Genie y AI Gen

Este repositorio acompaña el workshop **AI/BI en acción con Databricks**, un espacio práctico para descubrir cómo **Databricks AI/BI**, impulsado por **Genie** y **AI Gen**, transforma la forma en que interactuamos con los datos.

A lo largo del taller, aprenderás a:

- Usar **Genie** para realizar análisis conversacionales sobre datos gobernados en Unity Catalog.
- Aprovechar **AI Gen** para generar descripciones semánticas, metadatos y tableros inteligentes de manera automática.
- Construir tableros interactivos que combinan IA, automatización y gobernanza en el Lakehouse.

---

## 🧠 Agenda del Workshop

1. Bienvenida y visión AI/BI
2. De BI tradicional a AI/BI en Databricks
3. **Genie**: análisis conversacional sobre tus datos
4. **AI Gen**: generación automática de descripciones y dashboards
5. Construcción de un tablero AI/BI paso a paso
6. Cierre y recursos adicionales

---

## ✅ Prerrequisitos

Antes de comenzar, asegúrate de tener:

- Una cuenta activa en **Databricks Free Edition**
- Navegador web moderno (Chrome o Edge recomendado)
- Conocimientos básicos de SQL o Python

No necesitas instalar nada localmente. Todo se hará desde el entorno web de Databricks.

---

## 🪄 Parte 1 – Crear tu cuenta en Databricks Free Edition

1. Ingresa a 👉 [Databricks Free Edition](https://www.databricks.com/learn/free-edition)
2. Selecciona **Sing up for Free Edition**
3. Regístrate con tu correo personal

![step_1](img/step_1.png)

---

## 🧰 Parte 2 – Clonar este repositorio en Databricks

1. Dentro de tu workspace, abre el menú lateral y selecciona:
   **Workspace → Repos → Add Repo**
2. En el campo de URL, ingresa:

   ```bash
   https://github.com/dbcrewlatamstudygroup/workshop-genie
   ```

3. Cambia el nombre local del repositorio a algo como:

   ```bash
   ai-bi-databricks
   ```

4. Haz clic en **Create**.

![step_2](img/step_2.png)

Una vez clonado, verás los archivos en tu entorno de trabajo. Solo usaremos la carpeta y notebooks relacionados con **Databricks (Genie y AI Gen)**.

---

## 🧱 Parte 3 – Configuración del entorno en Databricks

### 1. Crear un catálogo

- Navega a **Catalog → Add data → Create a catalog**
  - Nombre: `ai_bi_workshop`
  - Tipo: `Standard`
  - Ubicación: predeterminada
  - Clic en **Create**

![step_3](img/step_3.png)

---

### 2. Crear un esquema

- Dentro del catálogo creado, haz clic en **Create Schema**
  - Nombre: `demo_v01`
  - Ruta de almacenamiento: automática

![step_4](img/step_4.png)

---

### 3. Subir datos de ejemplo

1. Entra a tu catálogo → esquema `demo_v01`
2. Crea una tabla con **Upload → File**
3. Sube los archivos desde la carpeta `/data/canada_sales/`:
   - `products.csv`
   - `customers.csv`
   - `orders.csv`
   - `opportunities.csv`
4. Verifica que las tablas se creen correctamente:

   ```sql
   SHOW TABLES IN ai_bi_workshop.demo_v01;
   ```

---

### 4. Ejecutar consultas de prueba

En el **SQL Editor** o un **Notebook**, ejecuta:

```sql
SELECT * FROM ai_bi_workshop.demo_v01.products LIMIT 5;
```

También puedes usar un Notebook con celdas SQL o Python:

```python
%sql
SHOW TABLES IN ai_bi_workshop.demo_v01;
```

o

```python
display(spark.sql("SELECT * FROM ai_bi_workshop.demo_v01.products LIMIT 5"))
```

---

## 🤖 Parte 4 – Explorando Genie y AI Gen

### 🔹 Genie: análisis conversacional

1. En el menú de Databricks, abre la aplicación **Genie**.
2. Conecta tu **catalog/schema** (`ai_bi_workshop.demo_v01`).
3. Haz preguntas como:
```
¿Cuál es el producto con mayor precio promedio?
```
```
“Muestra las ventas totales por región.”
```

### 📊📉 Crea Dashboards

#### Crea el dashboard y carga la data

1. Selecciona la opción de `Dashboards` en le menú de la izquierda

![dash1](img/dash0.png)

2. Da clic en `Crear Dashboard` en la parte superior derecha

![dash1](img/dash1.png)

3. Ya creaste un nuevo dashboard!

![dash2](img/dash2.png)

Primero cambia el título `New Dashboard` al nombre que tu quieras por ejemplo
```
Análisis de ordenes y oportunidades
```
Luego da clic en `Data`


4. Ahora vamos a cargar la data, para esto da clic en `+ Add data source`

![dash3](img/dash3.png)

5. Selecciona todas las tablas del catálogo que creamos en los pasos anteriores y da clic en `confirm`

![dash4](img/dash4.png)

6. Verás los datos en la parte izquierda y podrás crear nuevos conjuntos de datos o explorar los datos. Para iniciar a crear el tablero da clic en `Untitle page`

![dash5](img/dash5.png)

#### Contruyamos el dashboard

Ya estás listo para empezar a crear visualizaciones!!

El propósito de este análisis será:
- Entender comportamiento comercial
- Evaluar desempeño por representante
- Identificar oportunidades ganadas/perdidas
- Analizar ventas históricas

Nuestro resultado será algo así:

![dash6](dashboard/final_result.png)

En la parte inferior encontrarás este menú mediante el cual crearas los diferentes objetos: títulos, gráficos, filtros, etc.

![dash6](img/dash6.png)

1. Iniciemos con el título de nuestro tablero dando `clic en el cuadro con la T`. 
Tendrás un cuadro sombreado que indicará el lugar donde pondrás el título. Ubicalo en la parte superior

![dash7](img/dash7.png)

El título será 
```
Desempeño de ventas y oportunidades
```
Puedes añadir el logo que está en la carpeta dashboard/logo cargando la imagen

![dash8](img/dash8.png)

Primero creemos los KPI:

2. Añade una visualización desde el menú de la parte inferior

![dash9](img/dash9.png)

Situala debajo del título. Tendras un cuadro donde hacer las preguntas en lenguaje natural y aparecerá también un panel a la derecha

![dash10](img/dash10.png)

Selecciona el dataset `orders`. En el cuadro de la gráfica puedes escribir lo que quieres graficar o utilizar las opciones sugeridas por Genie. En este caso selecciona `Total Order Amount`

![dash11](img/dash11.png)

Ajusta el tamaño de esta card, lo más pequeño que sea posible.

2. Ahora añade otra visualización pero esta vez selecciona el dataset `opportunities`

Esta vez vamos a escribir
````
Total oportunidades
````
Una vez nos muestre el valor da clic en `aceptar`.

🤫 Pista: Debería ser 342

Ajusta el tamaño y ubicala continua a la anterior.

3. Añade otra visualización, selecciona el dataset `orders`
y escribe 
```
Total ordenes
```
El resultado sería `15.54 k` recuerda dar clic en `aceptar`.

Ajusta el tamaño y ubicala continua a la anterior.

🎉 Este será nuestro primer checkpoint. Hasta aquí ya está construida la primera parte del dashboard. Ahora crearemos las gráficas

4. Ahora vamos a crear las gráficas de línea. Ahora añade una visualización, situala debajo de los KPI.
selecciona el dataset `opportunities` y escribe:
```
Oportunidades por mes en un gráfico de línea
```

✨ Tips: 
- Es importante indicar solo lo que quieres calcular (Ej: total ventas, oportunidades por año) porque será utilizado como título del gráfico. Evita frases que inicien con "quiero ver", "muestrame", "cuales fueron"
- Por defecto siempre realiza un gráfico de barras, si quieres un gráfico diferente debes indicarlo.

Ajusta el tamaño y ubicalo debajo de los kpi

5. Ahora añade otra visualización, situala junto a la anterior
selecciona el dataset `orders` y escribe:
```
ordenes por mes en un gráfico de línea
```

🎉 Hasta aquí el segundo Checkpoint. Ahora creemos las gráficas de barras

6. Ahora añade otra visualización, debajo de las anteriores,
selecciona el dataset `orders` y escribe:
```
ordenes por vendedor
```

Da clic en aceptar y ajusta el tamaño

7. Crea la última visualización, ubicala al lado de la anterior, selecciona el dataset `opportunities` y escribe
```
grafica de oportunidades por fase
```
Da clic en aceptar y ajusta el tamaño

8. Si quieres personalizar algún gráfico, solo debes seleccionarlo y modificar las opciones que te aparecen en el panel de la izquierda.

![dash12](img/dash12.png)

9. Cuando ya el tablero esté listo, solo debes dar clic en la parte superior derecha y publicarlo

![dash13](img/dash13.png)

🎉 Felicitaciones!!! Has creado tu primer dashboard!

---

### 🔹 AI Gen: metadatos y tableros inteligentes

1. Dirígete al **Unity Catalog → Tables**
2. Selecciona una tabla (por ejemplo `products`)
3. En la descripción automática sugerida por IA, haz clic en **Generate AI Summary**
4. AI Gen analizará los datos y creará descripciones y metadatos enriquecidos.
5. Usa estos datos para construir un tablero inteligente en Genie.

---

## 🎯 Resultado esperado

Al finalizar el workshop habrás:

- Creado un entorno gobernado con Unity Catalog
- Cargado y explorado tus datos
- Realizado análisis conversacionales con Genie
- Generado descripciones automáticas con AI Gen
- Construido un tablero AI/BI impulsado por IA

---

## 📚 Recursos adicionales

- [Databricks AI/BI](https://learn.microsoft.com/en-us/azure/databricks/ai-bi/)
- [Databricks Genie](https://learn.microsoft.com/en-us/azure/databricks/genie/)
- [AI Gen Documentation](https://learn.microsoft.com/en-us/azure/databricks/ai-bi/genie-ai-gen/)
- [Unity Catalog](https://learn.microsoft.com/azure/databricks/data-governance/unity-catalog/)
- [Databricks Dashboards](https://learn.microsoft.com/en-us/azure/databricks/dashboards/)

---

✨ ¡Ahora estás listo para explorar el poder del AI/BI en Databricks! ✨
