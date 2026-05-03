# Puente TikTok → Telegram

Una página HTML ligera que actúa como **puente de redirección** entre un enlace de TikTok y un canal o grupo de Telegram. Detecta automáticamente el dispositivo del usuario (Android, iOS o PC) y aplica la estrategia de redirección más adecuada para abrir Telegram fuera del navegador integrado de TikTok.

---

## Descripción

TikTok abre los enlaces dentro de su propio navegador integrado (in-app browser), lo que impide que las URLs de Telegram (`t.me/...`) inicien la aplicación nativa de Telegram. Esta página resuelve ese problema usando estrategias específicas por plataforma:

| Plataforma | Estrategia |
|------------|------------|
| **Android** | Protocolo `intent://` para forzar la apertura en el navegador externo del sistema, que sí puede lanzar la app de Telegram. |
| **iOS (iPhone / iPad)** | Redirección directa a la URL `https://t.me/...` y muestra un botón de respaldo visible en caso de que la redirección automática no funcione. |
| **PC / Otros** | Redirección estándar a la URL completa de Telegram. |

---

## Tecnologías utilizadas

- **HTML5** — estructura de la página.
- **CSS3** — estilos inline para la pantalla de carga animada.
- **JavaScript (Vanilla)** — detección de User-Agent y lógica de redirección.

No se requieren frameworks, librerías externas ni dependencias de terceros.

---

## Instalación

1. **Clona el repositorio:**

   ```bash
   git clone https://github.com/jf2021070309/puente-tiktok.git
   cd puente-tiktok
   ```

2. **Abre el archivo directamente en tu navegador** (para pruebas locales):

   ```bash
   # Linux / macOS
   open index.html

   # Windows
   start index.html
   ```

3. **O despliégalo en cualquier hosting estático**, por ejemplo:
   - [GitHub Pages](https://pages.github.com/)
   - [Netlify](https://www.netlify.com/)
   - [Vercel](https://vercel.com/)

   Solo necesitas publicar el archivo `index.html` en la raíz del sitio.

---

## Uso

### Cambiar el destino de Telegram

Abre `index.html` y localiza la línea:

```js
const tgLink = "t.me/ericksystem_software";
```

Reemplaza `ericksystem_software` por el username de tu canal, grupo o usuario de Telegram:

```js
const tgLink = "t.me/tu_canal";
```

> **Nota:** No incluyas `https://` en `tgLink`. El script construye la URL completa (`https://t.me/...`) de forma automática mediante la variable `fullTgUrl`.

### Flujo de usuario

1. El usuario hace clic en el enlace de tu bio de TikTok.
2. TikTok abre la página en su navegador integrado.
3. Después de **500 ms**, el script detecta el dispositivo y ejecuta la redirección.
4. En iOS se muestra adicionalmente un botón **"CLIC AQUÍ SI NO ABRE"** como alternativa manual.

---

## Estructura del proyecto

```
puente-tiktok/
└── index.html   # Página única de redirección
```

---

## Variables de entorno

Este proyecto no utiliza variables de entorno. La única configuración requerida es el enlace de Telegram, que se define directamente dentro de `index.html` en la constante `tgLink`.

---

## Contribuciones

¡Las contribuciones son bienvenidas! Para contribuir:

1. Haz un **fork** del repositorio.
2. Crea una rama descriptiva:
   ```bash
   git checkout -b feature/mejora-redireccion-ios
   ```
3. Realiza tus cambios y haz commit:
   ```bash
   git commit -m "feat: mejorar estrategia de redirección en iOS"
   ```
4. Abre un **Pull Request** describiendo los cambios propuestos.

Por favor, asegúrate de probar los cambios en los dispositivos afectados antes de enviar el PR.

---

## Licencia

Este proyecto no incluye un archivo de licencia. Todos los derechos reservados al autor. Contacta al mantenedor del repositorio para consultas sobre uso o distribución.
