Estos son los elementos de SEO que están implementados en la web de Quatre Fogons.

### Estructura de la página

- **Un solo H1 por página** y H2/H3 en orden jerárquico.
- **HTML semántico:** `header`, `nav`, `main`, `section`, `footer`, `address` y una tabla de horarios con `caption` y `th scope`.
- **Migas de pan** en las cuatro páginas secundarias.
- **Enlazado interno:** menú en todas las páginas, enlaces dentro de los textos, botones “Reserva taula” y anclas (`cuines.html#catalana`, etc.).

### URLs

- Cortas, en minúsculas y descriptivas: `carta.html`, `cuines.html`, `reserves.html` y `contacte.html`. La página principal es `/`.

### Etiquetas

- **`title` único** en cada página, con la palabra clave y la marca.
- **`meta description` única** en cada página.
- **`canonical`** en todas.
- **Open Graph:** `og:type`, `og:title`, `og:description`, `og:url` y `og:locale`.
- **`lang="ca"`, `charset` y `viewport`.**

### Palabras clave

- “Restaurante de cocina fusión en Barcelona”, “cocina catalana, japonesa, mexicana y marroquina”, “carta” y “reservar mesa”.
- Aparecen en títulos, H1, descripciones, H2 y textos.

### Usabilidad

- **Diseño responsive:** se adapta de móvil a escritorio con las clases `sm:`, `md:` y `lg:` de Tailwind.
- **Navegación clara:** el mismo menú en todas las páginas, con la página actual marcada.
- **Llamada a la acción:** “Reserva taula” en las páginas principales.
- **Formulario de reserva:** tipos de campo adecuados (`email`, `date`, `number`) y `autocomplete`.
- **Footer:** con dirección, teléfono y correo en todas las páginas.

### Accesibilidad

- Enlace “Salta al contingut”.
- `aria-label` en los menús y `aria-current` en la página activa.
- Foco visible con teclado.
- `label` asociado a cada campo del formulario.
- Contraste de color alto.
- Preguntas frecuentes con `details` y `summary`, que funcionan con teclado.
- Respeto a `prefers-reduced-motion`. Esto estaba en el CSS de la versión anterior y no lo trasladé a Tailwind, así que ahora mismo no está.

### Archivos

- **`robots.txt`:** permite rastrear todo e indica la ruta del sitemap.
- **`sitemap.xml`:** las cinco URLs con `lastmod` y `priority`.

### robots.txt

**Para qué sirve:** es el primer archivo que mira un buscador al llegar a tu web. Le dice qué partes puede rastrear y cuáles no. Debe estar en la raíz del dominio (`https://www.quatrefogons.cat/robots.txt`).

**Qué contiene el nuestro:**

```
User-agent: *
Allow: /

Sitemap: https://www.quatrefogons.cat/sitemap.xml
```

- `User-agent: *` significa que las reglas valen para todos los buscadores (Google, Bing…).
- `Allow: /` permite rastrear toda la web.
- `Sitemap:` indica dónde está el mapa del sitio, para que lo encuentren sin que tú se lo envíes.

Si hubiera una zona privada, por ejemplo un panel de administración, se bloquearía con `Disallow: /admin/`. Aquí no hace falta. `robots.txt` no protege contenido: solo pide a los buscadores que no lo rastreen.

### sitemap.xml

**Para qué sirve:** es una lista de las URLs que quieres que Google indexe. Ayuda a que encuentre todas las páginas, sobre todo si están poco enlazadas o la web es nueva.

**Qué contiene el nuestro** (resumido):

xml

```xml
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://www.quatrefogons.cat/</loc>
    <lastmod>2026-11-03</lastmod>
    <priority>1.0</priority>
  </url>
  ...
</urlset>
```

Hay un bloque `<url>` por cada página, y tiene tres datos:

- `loc`: la dirección completa de la página.
- `lastmod`: la fecha de la última modificación.
- `priority`: la importancia relativa de 0 a 1 que tú le das dentro de tu web. En el sitio, la principal tiene 1.0, la carta 0.9, cuines y reserves 0.8 y contacte 0.6. Google la ignora en la práctica, pero es un campo estándar.

Las cinco URLs listadas son `/`, `cuines.html`, `carta.html`, `reserves.html` y `contacte.html`.

### Cómo se relacionan

`robots.txt` indica qué puede rastrear el buscador y apunta al sitemap. `sitemap.xml` lista lo que quieres que indexe. Una vez publicada la web, el sitemap también se puede enviar directamente en Google Search Console.
### Schema.org (JSON-LD)

- **`Restaurant`:** en inicio y contacto, con cocinas, dirección, teléfono, horarios y rango de precios.
- **`Menu`:** en la carta, con secciones, platos y precios.
- **`FAQPage`:** en reservas.
- **`BreadcrumbList`:** en las cuatro secundarias.

### Lo que no está implementado

- Imágenes con `alt`: no hay ninguna.
- `hreflang`, porque la web tiene un solo idioma.
- Página 404 y favicon.
- HTTPS, que depende del hosting.

| Index.html                |                                                                                           |
| ------------------------- | ----------------------------------------------------------------------------------------- |
| @type                     | Restaurant                                                                                |
| name                      | Quatre Fogons                                                                             |
| url                       | https://www.quatrefogons.cat/                                                             |
| image                     | https://www.quatrefogons.cat/img/quatre-fogons.jpg                                        |
| description               | Restaurant de cuina fusió que combina la cuina catalana, japonesa, mexicana i marroquina. |
| servesCuisine             | Catalana                                                                                  |
| servesCuisine             | Japonesa                                                                                  |
| servesCuisine             | Mexicana                                                                                  |
| servesCuisine             | Marroquina                                                                                |
| servesCuisine             | Fusió                                                                                     |
| priceRange                | €€                                                                                        |
| telephone                 | +34 930 000 000                                                                           |
| email                     | reserves@quatrefogons.cat                                                                 |
| acceptsReservations       | http://schema.org/True                                                                    |
| address                   |                                                                                           |
| @type                     | PostalAddress                                                                             |
| streetAddress             | Carrer del Mar, 12                                                                        |
| addressLocality           | Barcelona                                                                                 |
| postalCode                | 08003                                                                                     |
| addressCountry            |                                                                                           |
| @type                     | Country                                                                                   |
| name                      | ES                                                                                        |
| openingHoursSpecification |                                                                                           |
| @type                     | OpeningHoursSpecification                                                                 |
| dayOfWeek                 | http://schema.org/Tuesday                                                                 |
| dayOfWeek                 | http://schema.org/Wednesday                                                               |
| dayOfWeek                 | http://schema.org/Thursday                                                                |
| dayOfWeek                 | http://schema.org/Friday                                                                  |
| dayOfWeek                 | http://schema.org/Saturday                                                                |
| dayOfWeek                 | http://schema.org/Sunday                                                                  |
| opens                     | 13:00                                                                                     |
| closes                    | 16:00                                                                                     |
| openingHoursSpecification |                                                                                           |
| @type                     | OpeningHoursSpecification                                                                 |
| dayOfWeek                 | http://schema.org/Thursday                                                                |
| dayOfWeek                 | http://schema.org/Friday                                                                  |
| dayOfWeek                 | http://schema.org/Saturday                                                                |
| opens                     | 20:00                                                                                     |
| closes                    | 23:30                                                                                     |
| hasMenu                   |                                                                                           |
| @type                     | Menu                                                                                      |
| @id                       | https://www.quatrefogons.cat/carta.html                                                   |

| Cuines.html     |                                          |
| --------------- | ---------------------------------------- |
| @type           | BreadcrumbList                           |
| itemListElement |                                          |
| @type           | ListItem                                 |
| position        | 1                                        |
| name            | Inici                                    |
| item            |                                          |
| @type           | Thing                                    |
| @id             | https://www.quatrefogons.cat/            |
| itemListElement |                                          |
| @type           | ListItem                                 |
| position        | 2                                        |
| name            | Les quatre cuines                        |
| item            |                                          |
| @type           | Thing                                    |
| @id             | https://www.quatrefogons.cat/cuines.html |

| Carta.html     |                                                     |
| -------------- | --------------------------------------------------- |
| @type          | Menu                                                |
| name           | Carta de Quatre Fogons                              |
| inLanguage     | ca                                                  |
| hasMenuSection |                                                     |
| @type          | MenuSection                                         |
| name           | Per començar                                        |
| hasMenuItem    |                                                     |
| @type          | MenuItem                                            |
| name           | Croqueta d’arròs de sushi                           |
| description    | Dues unitats, amb sobrassada i alvocat.             |
| offers         |                                                     |
| @type          | Offer                                               |
| price          | 7                                                   |
| priceCurrency  | EUR                                                 |
| hasMenuItem    |                                                     |
| @type          | MenuItem                                            |
| name           | Tacos de bacallà a la llauna                        |
| description    | Amb guacamole de wasabi i tortilla de blat de moro. |
| offers         |                                                     |
| @type          | Offer                                               |
| price          | 11                                                  |
| priceCurrency  | EUR                                                 |
| hasMenuItem    |                                                     |
| @type          | MenuItem                                            |
| name           | Hummus d’escalivada amb miso                        |
| description    | Amb pa pita torrat.                                 |
| offers         |                                                     |
| @type          | Offer                                               |
| price          | 8                                                   |
| priceCurrency  | EUR                                                 |
| hasMenuSection |                                                     |
| @type          | MenuSection                                         |
| name           | Plats principals                                    |
| hasMenuItem    |                                                     |
| @type          | MenuItem                                            |
| name           | Arròs de rap amb ras el hanout                      |
| description    | Arròs melós amb peix de roca.                       |
| offers         |                                                     |
| @type          | Offer                                               |
| price          | 19                                                  |
| priceCurrency  | EUR                                                 |
| hasMenuItem    |                                                     |
| @type          | MenuItem                                            |
| name           | Tagine de xai amb romesco                           |
| description    | Cocció lenta, amb tortillas de blat de moro.        |
| offers         |                                                     |
| @type          | Offer                                               |
| price          | 21                                                  |
| priceCurrency  | EUR                                                 |
| hasMenuItem    |                                                     |
| @type          | MenuItem                                            |
| name           | Ramen de fideuà                                     |
| description    | Fideus fins, brou de peix i allioli de safrà.       |
| offers         |                                                     |
| @type          | Offer                                               |
| price          | 17                                                  |
| priceCurrency  | EUR                                                 |
| hasMenuSection |                                                     |
| @type          | MenuSection                                         |
| name           | Postres                                             |
| hasMenuItem    |                                                     |
| @type          | MenuItem                                            |
| name           | Crema catalana de te matcha                         |
| description    | Amb sucre cremat al moment.                         |
| offers         |                                                     |
| @type          | Offer                                               |
| price          | 6.50                                                |
| priceCurrency  | EUR                                                 |
| hasMenuItem    |                                                     |
| @type          | MenuItem                                            |
| name           | Xurros amb xocolata negra                           |
| description    | Amb canyella i dàtils.                              |
| offers         |                                                     |
| @type          | Offer                                               |
| price          | 6                                                   |
| priceCurrency  | EUR                                                 |

| Reserves.html  |                                                                                                    |
| -------------- | -------------------------------------------------------------------------------------------------- |
| @type          | FAQPage                                                                                            |
| mainEntity     |                                                                                                    |
| @type          | Question                                                                                           |
| name           | Cal reservar?                                                                                      |
| acceptedAnswer |                                                                                                    |
| @type          | Answer                                                                                             |
| text           | Recomanem reservar els caps de setmana. Els dies feiners també hi ha taules sense reserva.         |
| mainEntity     |                                                                                                    |
| @type          | Question                                                                                           |
| name           | Teniu opcions vegetarianes?                                                                        |
| acceptedAnswer |                                                                                                    |
| @type          | Answer                                                                                             |
| text           | Sí. Gairebé tots els entrants tenen versió vegetariana i el hummus d’escalivada ho és per defecte. |
| mainEntity     |                                                                                                    |
| @type          | Question                                                                                           |
| name           | Es poden fer reserves de grup?                                                                     |
| acceptedAnswer |                                                                                                    |
| @type          | Answer                                                                                             |
| text           | Sí, per a grups de més de 8 persones escriu-nos a reserves@quatrefogons.cat.                       |