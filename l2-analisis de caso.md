
# Análisis de caso módulo 3 "Metodología de organización y modularización de estilos"

## Diagnóstico técnico
- Se presentan problemas cuando los estilos no están organizados, tales como reglas duplicadas, dificultad para encontrar/editar estilos, efectos colaterales al cambiar algo, CSS más pesado y lento, poca reutilización e interfaces inconsistentes.
- Al usar clases genéricas/no moduladas en muchos lugares, cualquier cambio afecta partes imprevistas, es difícil saber qué impacta qué y se vuelve casi imposible escalar sin romper vistas.

## Metodologías y elección
- BEM: nombra clases según Bloque–Elemento–Modificador, genera HTML algo verboso pero muy claro y predecible.

- OOCSS: separa estructura (layout) de apariencia (skin), fomenta clases reutilizables pero puede producir muchas clases combinadas.

- SMACSS: organiza el CSS por categorías (base, layout, module, state, theme), ideal para proyectos grandes pero requiere una convención de carpetas/archivos más amplia.

En este caso elgimos trabajar con BEM para PixelPerfect Studio porque:

- Hace muy explícita la relación entre componentes y partes internas.

- Reduce conflictos entre equipos, ya que cada bloque tiene su “espacio de nombres”.

- Es fácil de enseñar y documentar para que todos la apliquen igual.

##  Documentación interna
Organización de la hoja de estilos: 
- Tenemos un main.scss que sólo importa módulos (base/, components/, layout/, etc.), lo que permite localizar rápido los estilos según el tipo de regla.

Propósito de carpetas/archivos:

- Carpeta scss/: contiene los archivos fuente SASS, que luego se compilan a main.css dentro de css/ para usar en producción.

- Subcarpeta blocks/: cada archivo (_alerts.scss, _btn_group.scss, _buttons.scss, _cards.scss, _nav.scss) define los estilos de un bloque/componente independiente siguiendo BEM, evitando mezclar responsabilidades.

- _variables.scss: centraliza colores, tamaños y otros tokens, lo que permite cambiar la apariencia global tocando un solo archivo.

- main.scss: actúa como “orquestador”; sólo importa variables y bloques, generando un CSS final único pero manteniendo el código fuente dividido y legible.

El objetivo de esta organización es:
- Facilitar el mantenimiento: si hay un problema en la navegación, vas directo a _nav.scss sin buscar entre todo el CSS.

- Favorece la escalabilidad: poder agregar nuevos componentes creando más archivos en blocks/ sin romper lo existente.

- Mejorar el trabajo en equipo: cada dev puede encargarse de un bloque distinto, con nombres BEM que reducen conflictos entre estilos.

## Reflexión final
Se presentó un desafío al aplicar la metodología, ya que hay que acostumbrarse a nombres más largos, reestructurar CSS existente y decidir qué es bloque, elemento o modificador, cosa que es difernete a como veníamos trabajando hasta ahora en el curso.
Sin embargo esta medtdología facilita encontrar dónde tocar, reduciendo el “miedo” a romper otras vistas y hace más sencillo agregar variantes del mismo componente.
Finalemnet entrega beneficios útiles ára realizar proyectos más grandes y complejos, ya que todos comparten el mismo lenguaje de clases, se minimizan colisiones, se puede dividir el trabajo por componentes y el onboarding de nuevos devs es más rápido.
