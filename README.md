
# **Proyecto RAG: Recuperación y Generación de Respuestas**

## Descripción del Proyecto

Este proyecto implementa un sistema de **Retrieval Augmented Generation (RAG)** utilizando **OpenAI GPT-4** para la generación de respuestas basadas en fragmentos recuperados de un conjunto de datos. El sistema sigue estos pasos principales:

1. **Carga de Datos**: Los datos se cargan desde una fuente externa (p. ej., un blog) utilizando **WebBaseLoader** de LangChain.
2. **División de Documentos**: Los documentos se dividen en fragmentos más pequeños, para hacerlos más manejables.
3. **Indexación**: Los fragmentos de texto se convierten en **embeddings** (representaciones vectoriales) utilizando **OpenAIEmbeddings** y se almacenan en un **VectorStore**.
4. **Recuperación de Información**: Se recuperan los fragmentos más relevantes basados en la consulta del usuario.
5. **Generación de Respuestas**: Se genera una respuesta utilizando el modelo **GPT-4** de OpenAI, basado en los fragmentos recuperados.
6. **Orquestación**: **LangGraph** se utiliza para gestionar y coordinar todos los pasos.

## Requisitos

Este proyecto depende de las siguientes bibliotecas:

- **LangChain**: Para el procesamiento de lenguaje natural.
- **LangGraph**: Para la orquestación de flujos de trabajo.
- **OpenAI**: Para interactuar con **GPT-4**.
- **BeautifulSoup4**: Para analizar el HTML de las páginas web.
- **python-dotenv**: Para manejar variables de entorno de manera segura.

### Instalación

1. **Clonar el repositorio**:

   Si aún no lo has hecho, clona el repositorio en tu máquina local:

   ```bash
   git clone https://github.com/tu_usuario/tu_repositorio.git
   cd tu_repositorio
   ```

2. **Instalar las dependencias**:

   Para instalar todas las dependencias necesarias, puedes usar el siguiente comando:

   ```bash
   !pip install -r requirements.txt
   ```

3. **Requisitos adicionales**:

   - **Clave de API de OpenAI**: Necesitarás una clave de API de OpenAI para interactuar con **GPT-4**. Puedes obtenerla en [OpenAI](https://platform.openai.com/account/api-keys).
   
   - **Configuración de la clave de API**: Asegúrate de configurar la clave de API antes de ejecutar el código. Puedes hacerlo de dos maneras:

     - Usando **variables de entorno**:
       - En **Windows**:
         ```bash
         set OPENAI_API_KEY="tu_clave_de_api_aqui"
         ```
       - En **macOS/Linux**:
         ```bash
         export OPENAI_API_KEY="tu_clave_de_api_aqui"
         ```

     - O directamente en el código (no recomendado por razones de seguridad):
       ```python
       openai.api_key = "tu_clave_de_api_aqui"
       ```

4. **Archivos de configuración**:

   Si prefieres utilizar un archivo `.env` para manejar la clave de API de manera más segura, crea un archivo llamado `.env` en la raíz de tu proyecto con el siguiente contenido:

   ```
   OPENAI_API_KEY=tu_clave_de_api_aqui
   ```

   Luego, usa **python-dotenv** para cargar esta variable de entorno:

   ```bash
   !pip install python-dotenv
   ```

   Y en tu código:

   ```python
   from dotenv import load_dotenv
   load_dotenv()
   
   import openai
   openai.api_key = os.getenv("OPENAI_API_KEY")
   ```

## Ejecución en Jupyter Notebook

Este proyecto está diseñado para ejecutarse en **Jupyter Notebooks**. Cada paso del proceso se organiza en celdas secuenciales.

1. **Configura tu clave de API de OpenAI**: Ejecuta la celda que configura la clave de API en tu entorno.

2. **Carga los datos**: Ejecuta la celda que carga los datos desde la URL proporcionada (por ejemplo, el blog de ejemplo).

3. **Divide los documentos**: Ejecuta la celda que divide los documentos en fragmentos pequeños.

4. **Indexación de los fragmentos**: Ejecuta la celda que convierte los fragmentos en embeddings y los almacena en un **VectorStore**.

5. **Recuperación de fragmentos**: Ejecuta la celda que busca los fragmentos más relevantes según la consulta del usuario.

6. **Generación de la respuesta**: Ejecuta la celda que genera la respuesta utilizando el modelo **GPT-4**.

### Ejemplo de Consulta

Puedes realizar consultas dentro del notebook con el siguiente código:

```python
query = "What is Task Decomposition?"
response = graph.invoke({"question": query})
print(f"Respuesta generada: {response['answer']}")
```


## Licencia

Este proyecto está licenciado bajo la **MIT License**. Consulta el archivo **LICENSE** para más detalles.



