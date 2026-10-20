# ATLAS-PROPS-WEB
# ATLAS PROPS WEB — App móvil (versión inicial)

Esta versión reimplementa las funciones centrales de ATLAS PROPS/ATLAS LENS para uso en Safari desde el iPhone, sin Google Colab. Mantiene las cinco secciones: Boleto, Análisis, Datos, Capturas y Metodología.

## Publicar gratis (Render)

1. Crea un repositorio de GitHub. Sube **los archivos dentro de esta carpeta** a la raíz del repositorio (incluye `render.yaml` y `.streamlit/config.toml`). Es más sencillo desde una computadora; GitHub web también permite subir archivos individuales.
2. En https://dashboard.render.com/ selecciona **New > Blueprint** y conecta el repositorio. Render detectará `render.yaml`.
3. Confirma el despliegue. Render te dará un enlace `https://...onrender.com`.
4. Abre el enlace en Safari en tu iPhone. En Compartir, selecciona **Añadir a pantalla de inicio**.

Alternativa: **New > Web Service**, entorno Python, build `pip install -r requirements.txt`, start `streamlit run app.py --server.address 0.0.0.0 --server.port $PORT --server.headless true`, y plan Free si está disponible.

## Ejecutar localmente

```bash
python -m pip install -r requirements.txt
streamlit run app.py
```

## Funciones

- OCR asistido de boletos/capturas con RapidOCR (sin instalar Tesseract).
- Búsqueda de partidos programados y descarga de boxscores históricos de ESPN (cuando ESPN ofrece información compatible).
- Importación CSV con trazabilidad y exportación de informes ZIP.
- Poisson, binomial negativa y normal, backtesting temporal y EV teórico.

## Limitaciones importantes

- Es una adaptación nueva del código compartido en el chat; no es una copia idéntica de la interfaz original, ni se ha sometido todavía a una prueba end-to-end contra partidos reales de ESPN.
- Si ESPN cambia su estructura, alguna liga/estadística puede dejar de funcionar. El OCR puede equivocarse.
- La selección del jugador del boleto NO se vincula automáticamente a un equipo: hay que seleccionar el encuentro/equipo y confirmar el jugador.
- No se confirman automáticamente noticias, alineaciones, minutos, cuotas reales ni reglas específicas de PrizePicks. Los datos importados no se validan independientemente.
- Los planes gratuitos pueden dormir/reiniciarse y borrar el estado de la sesión. Descargar los resultados es importante.
- No se implementó login; quien tenga el enlace podría utilizar la aplicación. No compartas datos privados ni publiques un enlace público para uso sensible.
- No es una herramienta de beneficio garantizado ni coloca apuestas.