# Mission board

[English](README.md) | [Português (Brasil)](README.pt-BR.md) | [Español (España)](README.es-ES.md)

![Un tablón de misiones de un gremio pirata con el sombrero de Chopper y los libros de arqueología de Robin.](docs/assets/mission-board.png)

Un asistente de carrera profesional con archivos locales, creado con skills y
archivos sencillos. Registra tu experiencia, encuentra oportunidades y prepara
candidaturas adaptadas a cada oferta.

## Estado

La skill `career-record` mantiene el perfil, el registro de experiencias y los
objetivos profesionales en `~/.local/share/mission-board/`. La skill `job-search`
evalúa una oferta que aporta la persona basándose en ese registro y hace un
seguimiento de su estado. La skill `job-snapshot` reúne esas ofertas en una
página HTML que se puede compartir. La búsqueda en portales de empleo, la
adaptación de currículos, las cartas de presentación y la exportación a PDF
aún no están implementadas.

## Skills disponibles

[Ideal work](.agents/skills/ideal-work/SKILL.md) guía una conversación sobre el
trabajo que te gusta hacer, cómo quieres colaborar y tus próximos objetivos
profesionales. Elige una descripción breve, unos párrafos o una reflexión
personal más completa.

Para empezar, pide a tu agente que use `ideal-work` en este repositorio. Por
ejemplo:

> Usa ideal-work para ayudarme a descubrir cómo quiero trabajar y qué explorar a continuación.

El ejercicio se queda en la conversación, salvo que pidas guardarlo en
`~/.local/share/mission-board/`, fuera de este repositorio.

## Alcance previsto

- Registrar el trabajo diario, las responsabilidades, los proyectos y los resultados.
- Revisar currículos para mejorar la claridad, detectar afirmaciones sin pruebas e información desactualizada.
- Adaptar currículos a una oferta de empleo basándose en la experiencia real de la persona.
- Buscar ofertas de empleo según las preferencias de la persona y devolver enlaces a las fuentes.
- Redactar cartas de presentación basadas en la experiencia de la persona y en el puesto.
- Exportar currículos y cartas de presentación a PDF cuando sea necesario.

Los registros de carrera profesional son el material de partida. Los currículos
y las cartas son documentos adaptados a cada candidatura. La persona revisa
cada candidatura y decide qué enviar.

## Límites

Sin candidaturas automáticas, contacto masivo, spam en LinkedIn ni automatización
de interacciones. Nunca inventar experiencia, cualificaciones ni resultados
para ajustarse a la descripción de una oferta.

## Archivos públicos y privados

Este repositorio está destinado a skills reutilizables, plantillas,
documentación y ejemplos ficticios. Los datos personales, los registros de
carrera profesional, las ofertas guardadas, las notas sobre candidaturas y
los documentos generados se almacenan en `~/.local/share/mission-board/`, fuera
del repositorio. Nunca copies esos datos al repositorio, los incluyas en
commits ni publiques su contenido.

El uso de archivos locales describe dónde se almacenan. Un proveedor de IA
puede seguir procesando el contenido que se facilite al asistente.

## Desarrollo

Consulta el trabajo en [GitHub Issues](https://github.com/momoi-labs/mission-board/issues).
Lee los [principios de ingeniería](docs/PRINCIPLES.md) antes de contribuir.
