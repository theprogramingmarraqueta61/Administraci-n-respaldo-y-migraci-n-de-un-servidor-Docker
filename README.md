# Administraci-n-respaldo-y-migraci-n-de-un-servidor-Docker

¿Por qué el control de versiones no sustituye un respaldo Docker?

Git y GitHub guardan únicamente el código fuente del sitio y su historial de cambios. No guardan el entorno en el que ese código se ejecuta. Un respaldo Docker, en cambio, conserva el servicio completo. Las diferencias principales son:

Alcance: Git guarda los archivos del sitio (HTML, CSS). La imagen Docker guarda además el sistema base Alpine, Nginx 1.31.9, sus dependencias y la configuración (default.conf).
Reproducibilidad: con el archivo .tar generado con docker save, el servicio se restaura en otro servidor con docker load y docker run, exactamente igual que el original. Con Git, habría que reinstalar y configurar Nginx manualmente, con riesgo de que cambien versiones o ajustes.
Configuración fuera del código: los cambios hechos dentro del contenedor, como la configuración de Nginx, no están en el repositorio si no se subieron. Quedan solo en el contenedor.
Disponibilidad: el respaldo Docker es un archivo local y transportable que no depende de internet ni de un servicio externo. El repositorio depende de GitHub.
Propósito distinto: Git sirve para versionar y colaborar. El respaldo Docker sirve para recuperar y migrar el servicio ante una falla o un traslado de servidor.

Conclusión: ambas herramientas son complementarias. Git protege el código y su historia, y la imagen Docker protege el entorno de ejecución completo. Para una recuperación total se necesitan las dos.
