# Parapentitis

Landing en español para la escuela de parapente de Salvador Lara en Fortín de las Flores, Veracruz, aliada con Basecamp 420.

HTML5 semántico y Tailwind CSS compilado localmente, sin JavaScript ni CDN de estilos en producción. Incluye navegación adaptable, vuelos tándem, cursos APPI A1/A2/avanzado, equipo, contacto directo, avisos legales y metadatos OpenGraph/Twitter.

## Desarrollo local

Requisitos: Node.js 22 LTS o posterior, npm y Python 3 para el servidor local de ejemplo.

```sh
git clone https://github.com/karla266/parapentitis.com.git
cd parapentitis.com
npm ci
npm run build
python3 -m http.server 8080 --directory dist
```

Abre <http://localhost:8080>. Para editar con recompilación de estilos, ejecuta `npm run dev` en una terminal y `python3 -m http.server 8080` en otra desde la raíz. Recarga el navegador después de guardar. Para comprobar la versión final, vuelve a compilar y sirve `dist`.

## Estructura

```text
index.html                 Contenido, contacto, avisos y SEO
src/styles.css             Tailwind y estilos de la marca
public/logo.svg            Identidad gráfica inicial
public/flight-landscape.svg Ilustración original de respaldo
public/og-cover.jpg         Tarjeta social local, 1200 × 630
public/styles.css          Generado por Tailwind (ignorado en Git)
robots.txt / sitemap.xml   Indexación
vercel.json / netlify.toml Despliegue estático
dist/                      Sitio compilado (ignorado en Git)
```

`npm run build` regenera `dist`; solo copia los archivos públicos, no fuentes, dependencias ni archivos de configuración. No existe infraestructura de tests o lint. La verificación básica es compilar y revisar el sitio servido en escritorio/móvil, enlaces, anclas, teclado y vistas previas sociales.

## Publicación

### Vercel

Importa este repositorio en Vercel. `vercel.json` establece `npm run build` como comando de compilación y `dist` como directorio público. No requiere framework ni variables de entorno. Selecciona Node.js 22 o posterior.

### Netlify

Importa el repositorio. `netlify.toml` define automáticamente compilación y publicación desde `dist`. Selecciona Node.js 22 o posterior.

### Hostinger u otro hosting estático

Ejecuta `npm ci && npm run build` localmente. Sube **el contenido de `dist/`**, incluido `public/`, al directorio web (`public_html` en Hostinger). No subas `node_modules/`, archivos `.env` ni el repositorio completo. No se necesita un servidor Node en producción. Publica en la raíz del dominio, no en un subdirectorio.

### Dominio personalizado

1. Añade `parapentitis.com` y `www.parapentitis.com` en el panel de dominios del proveedor.
2. En la zona DNS del registrador, aplica los registros A/ALIAS/CNAME **exactos que indique ese proveedor**, eliminando únicamente los registros web que entren en conflicto. Conserva los registros de correo (MX/TXT).
3. Espera la propagación y activa/verifica el certificado HTTPS.
4. Redirige `www` a `https://parapentitis.com` como dominio principal.
5. Si usas otro dominio, actualiza canonical, `og:url`, `og:image`, `twitter:image`, enlaces para compartir, `robots.txt` y `sitemap.xml`.
6. Comprueba `/`, `/public/styles.css`, `/public/og-cover.jpg`, `/robots.txt` y `/sitemap.xml` en producción. Actualiza la caché de previsualización con Facebook Sharing Debugger al cambiar la tarjeta OG.

## Contenido y medios

- Todos los botones de reserva usan WhatsApp `522727258748`; el enlace de llamada usa `+522727258748`. No hay pagos ni reservas automáticas: fechas, requisitos y meteorología se confirman con el piloto.
- La fotografía de fondo es **ilustrativa de Iquique, Chile**, no se presenta como fotografía de Fortín: [Paragliding (4532267391)](https://commons.wikimedia.org/wiki/File:Paragliding_(4532267391).jpg), de **Mr Hicks46**, [CC BY-SA 2.0](https://creativecommons.org/licenses/by-sa/2.0/). Se carga desde Wikimedia sin modificaciones al archivo; se acredita junto al hero. Las capas de color son estilos de la página.
- La descarga de fotografías estuvo bloqueada por DNS en el entorno de creación. Si Wikimedia no responde, aparece la ilustración original local `public/flight-landscape.svg`; no hay un recurso local faltante. La tarjeta OG es una composición original local para no depender de esa fuente.
- **Pendiente editorial:** sustituir el fondo por una fotografía propia o autorizada de vuelos en Fortín/Pico de Orizaba. Guárdala optimizada en `public/`, cambia `background-image` en `src/styles.css` y el preload en `index.html`, y ajusta el crédito a su licencia. Elimina la conexión externa a Wikimedia si ya no se usa.
- El logotipo SVG es una propuesta inicial, no una reproducción de un logotipo oficial.
- Basecamp 420 enlaza a su perfil público de Instagram y a una búsqueda en Maps de la dirección proporcionada: Oriente 27 y Norte 10, Orizaba. Confirma la ubicación con la tienda antes de acudir.
- El pie ofrece enlaces para **compartir** por Facebook y WhatsApp. No se inventaron perfiles propios de Parapentitis; añádelos cuando se proporcionen las URLs oficiales.
- Antes de recibir pagos o datos personales, valida con el responsable los datos de certificación, condiciones comerciales y el aviso de privacidad integral. Los textos actuales no sustituyen asesoría jurídica.

El sitio no incorpora cookies de analítica ni formularios. La fotografía remota comunica al servidor de imágenes los datos técnicos habituales de una solicitud; los enlaces de WhatsApp, Instagram, Facebook y Maps llevan a servicios externos con sus propias políticas.
