# Una pregunta para Aimet

Experiencia romántica interactiva, independiente de los demás proyectos.

## Arquitectura actual

- Frontend estático publicado con GitHub Pages.
- Backend en Supabase Edge Functions.
- Base de datos con tablas protegidas por RLS y permisos directos denegados a los roles públicos.
- Dos contraseñas distintas: una para Aimet y otra para el propietario.
- El backend identifica el rol comparando la contraseña; no se pide elegir un tipo de cuenta.
- Las contraseñas se guardan como hashes PBKDF2-SHA-256 con sales aleatorias, nunca en texto plano.
- Sesiones opacas temporales, almacenadas como hash y revocables.
- Aimet solo puede enviar una respuesta.
- El propietario puede consultar respuestas y cambiar cualquiera de las dos contraseñas.
- La vista previa del propietario no registra respuestas.

## Configuración inicial pendiente

1. Abrir `setup-access.html` desde GitHub Pages o descargarlo y abrirlo localmente.
2. Crear dos contraseñas diferentes, cada una de al menos 12 caracteres.
3. Copiar el SQL generado por la herramienta local y ejecutarlo en el SQL Editor del proyecto Supabase.
4. Verificar los dos accesos y los permisos antes de compartir el enlace con Aimet.

La herramienta de configuración genera los hashes en el navegador y no transmite las contraseñas.

## Seguridad

- No colocar contraseñas, tokens privados ni claves secretas en este repositorio.
- La clave publishable de Supabase incluida en el frontend es pública por diseño; las operaciones privilegiadas ocurren exclusivamente en la Edge Function.
- La clave service-role solo se utiliza en el entorno de servidor de Supabase.
- Las tablas no conceden acceso directo a `anon` ni `authenticated`; RLS está activado.
- No compartir el enlace de la experiencia hasta completar la configuración inicial y las pruebas de extremo a extremo.

## Experiencia

- Interfaz responsive para iPhone y Android.
- La experiencia de Aimet conserva la estética romántica de neón y partículas.
- El panel del propietario y el configurador de contraseñas usan una interfaz minimalista, sin partículas ni animaciones decorativas; la animación de fondo se pausa mientras el panel está abierto.
- Paleta de neón rosa, fucsia, magenta y rojo.
- Partículas animadas, sin música ni efectos de sonido.
- Recorrido breve con dos posibles respuestas y un mensaje respetuoso en ambos casos.
