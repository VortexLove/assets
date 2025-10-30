# Index de imágenes / GIFs

Este archivo `index.html` genera dinámicamente un listado visual de todas las imágenes y GIFs del repositorio `VortexLove/assets` usando la API pública de GitHub.

Cómo funciona
- El script consulta el árbol del repositorio y filtra archivos por extensiones comunes de imágenes (.png, .jpg, .jpeg, .gif, .webp, .svg).
- Muestra vistas previas usando los archivos crudos en raw.githubusercontent.com.
- Por defecto asume que la rama principal es `main`. Si tu rama por defecto es otra, o quieres indexar una carpeta específica, edita las constantes OWNER, REPO y PATH en `index.html`.

Consideraciones
- Peticiones anónimas a la API de GitHub tienen límites de rate-limit. Si el índice no carga correctamente por límite, puedes generar un token personal de GitHub y añadirlo a la variable `GITHUB_TOKEN` dentro de `index.html`. Ten cuidado: no es seguro subir tokens en repositorios públicos.
- Para repos grandes, es más eficiente generar un índice estático (por ejemplo un JSON o un README) mediante un script (GitHub Action o local) y commitearlo al repo para que el HTML lo lea sin llamar a la API.

Uso
1. Coloca `index.html` en la raíz del repo (o en la carpeta que prefieras).
2. Abre `index.html` en el navegador (si lo abres directamente como archivo local, las llamadas fetch a la API siguen funcionando porque van al dominio api.github.com).
3. Si necesitas indexar solo `assets/images/`, asigna PATH = "assets/images" en el script.
