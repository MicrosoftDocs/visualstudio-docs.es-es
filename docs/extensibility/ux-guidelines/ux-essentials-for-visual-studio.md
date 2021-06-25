---
title: UX Essentials for Visual Studio | Microsoft Docs
description: Revise estos procedimientos recomendados de la experiencia del usuario para conocer las nuevas características que desarrolle para Visual Studio, incluido conocer la resolución de pantalla.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 74b27e87e6f16130573ef6671286501f77e44352
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899425"
---
# <a name="ux-essentials-for-visual-studio"></a>Fundamentos de la experiencia de usuario de Visual Studio

## <a name="best-practices"></a>Procedimientos recomendados

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Sea coherente dentro del entorno Visual Studio de trabajo.

- Siga los patrones [de interacción existentes](interaction-patterns-for-visual-studio.md) en el shell.

- Diseñe características para que sean coherentes con los requisitos de lenguaje visual y [de organización del shell.](evaluation-tools-for-visual-studio.md)

- Use comandos y controles compartidos cuando existan.

- Comprenda la Visual Studio y cómo establece el contexto y dirige la interfaz de usuario.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Use el servicio de entorno para fuentes y colores.

- La interfaz de usuario debe respetar la configuración [de fuente del](fonts-and-formatting-for-visual-studio.md) entorno actual a menos que se exponga para su personalización en la página Fuentes y colores del cuadro de diálogo Opciones.

- Los elementos de la interfaz de usuario deben [usar el servicio VSColor](colors-and-styling-for-visual-studio.md)mediante tokens de entorno compartido o tokens específicos de características.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Haga que todas las imágenes sean coherentes con el nuevo estilo de VS.

- Siga Visual Studio principios de diseño para iconos, glifos y otros gráficos.

- No coloque texto en elementos gráficos.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Diseño desde una perspectiva centrada en el usuario.

- Cree el flujo de tareas antes de las características individuales dentro de él.

- Familiarícese con los usuarios y haga que ese conocimiento sea explícito en la especificación.

- Al revisar la interfaz de usuario, evalúe la experiencia completa, así como los detalles.

- Diseñe la interfaz de usuario para que siga siendo funcional y atractiva, independientemente de la configuración regional o el idioma.

## <a name="screen-resolution"></a>Resolución de pantalla

### <a name="minimum-resolution"></a>Resolución mínima

- La resolución mínima para Visual Studio 2015 es **1280 x 720**. Esto significa que es *posible usar Visual Studio* en esta resolución, aunque podría no ser una experiencia de usuario óptima. No hay ninguna garantía de que todos los aspectos se puedan usar con resoluciones inferiores a 1280 x 720.

- La resolución de destino Visual Studio es **1366 x 768**. Se trata de la resolución más baja en la que se ofrece una *buena experiencia* de usuario.

- El alto inicial del cuadro de diálogo debe ser inferior a **700** píxeles, por lo que se ajusta a la resolución mínima del marco ide a 96 ppp.

### <a name="high-density-displays"></a>Pantallas de alta densidad
 La interfaz Visual Studio debe funcionar bien en todos los factores de escalado de PPP que Windows admite de forma estándar: 150 %, 200 % y 250 %.

## <a name="anti-patterns"></a>Antipatrones
 Visual Studio contiene muchos ejemplos de interfaz de usuario que siguen nuestras directrices y procedimientos recomendados. En un esfuerzo por ser coherentes, los desarrolladores suelen tomar prestada patrones de diseño de interfaz de usuario de producto similares a los que están creando. Aunque este es un buen enfoque que nos ayuda a impulsar la coherencia en la interacción del usuario y el diseño visual, en ocasiones se incluyen características con algunos detalles que no cumplen nuestras directrices debido a restricciones de programación o a la priorización de defectos. En estos casos, no queremos que los equipos copien uno de estos "anti patterns" porque proliferan una interfaz de usuario incoherente o incoherente dentro del entorno Visual Studio usuario.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Campos o valores obligatorios que se muestran en estado de error de forma predeterminada

#### <a name="feature-team-goals"></a>Objetivos del equipo de características

- Advertir a los usuarios de que han agregado un elemento que se debe configurar.

- Dibuje la atención del usuario en las áreas que necesitan entrada.

#### <a name="anti-pattern-solution"></a>Solución anti pattern
 En cuanto el usuario haya iniciado una acción y antes de completar la tarea, coloque inmediatamente los iconos de parada crítica junto a las áreas que necesitan configuración.

#### <a name="example-manifest-designer-declarations"></a>Ejemplo: Declaraciones del Diseñador de manifiestos
 Al agregar una declaración a la lista, se coloca inmediatamente en un estado de error, que se conserva hasta que el usuario establece las propiedades necesarias.

 En este caso, hay un problema adicional porque el icono usado para la alerta contiene un icono " ", por lo que el icono de eliminación común no se &times; puede usar junto a él. Como resultado, la interfaz de usuario usa un botón Quitar, un control más desordenado.

 ![Colocar la interfaz de usuario en un estado de error de forma predeterminada es Visual Studio anti-patrón.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-pattern")<br />Colocar la interfaz de usuario en un estado de error de forma predeterminada es Visual Studio anti-patrón.

#### <a name="alternatives"></a>Alternativas

Una mejor solución a este problema es:

- Permita al usuario agregar una declaración sin advertencia y, a continuación, moverse inmediatamente para establecer propiedades en el elemento.

- Agregue el icono de advertencia (triángulo dorado) cuando el foco se mueva desde el elemento, como agregar otra declaración a la lista o intentar cambiar las pestañas dentro del diseñador.

- Si el usuario intenta cambiar las pestañas antes de establecer las propiedades en cualquier declaración, abre un cuadro de diálogo que explica que la aplicación no se compilará (ni las implicaciones) hasta que se resuelvan las advertencias. Si el usuario descarta el cuadro de diálogo y cambia las pestañas de todos modos, se agrega un icono (crítico o de advertencia, según corresponda) a la pestaña Declaraciones.

### <a name="multiple-clicks-to-dismiss-ui"></a>Varios clics para descartar la interfaz de usuario

#### <a name="feature-team-goals"></a>Objetivos del equipo de características
 No permita que el usuario descarte la interfaz de usuario sin ver primero el texto de la explicación.

#### <a name="anti-pattern"></a>Anti pattern
 El equipo que inserta los vínculos de vídeo en varios lugares dentro de la interfaz de usuario de VS decidió en contra del patrón común del botón "" cerrar y la explicación de la información sobre herramientas según lo especificado por la experiencia de usuario, y en su lugar implementó un menú desplegable y el vínculo "No volver &times; a mostrar".

#### <a name="example-video-links-in-team-explorer"></a>Ejemplo: Vínculos de vídeo en Team Explorer
Forzar al usuario a leer texto explicativo antes de descartar la interfaz de usuario es un anti pattern dentro de Visual Studio. Diseñados correctamente, los vínculos de vídeo deben mostrar una información sobre herramientas con información adicional al mantener el puntero y hacer clic en " " debe descartar el mensaje sin necesidad &times; de interacción adicional.

 ![Patrón de anties&#45;texto explicativo &#45; incorrecto](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Patrón de vínculo de vídeo incorrecto

En lugar de un botón cerrar simple (un clic), el usuario se ve obligado a usar dos clics para descartar simplemente la interfaz de usuario en cada lugar en el que aparecen los vínculos de vídeo.

El diseño correcto para esta situación es seguir el patrón común a Internet Explorer, Office y Visual Studio: al mantener el puntero, el usuario puede ver la descripción de la información sobre herramientas y un clic oculta la interfaz de usuario.

 ![Patrón de anties&#45;texto explicativo &#45; correcto](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-pattern-correct")<br />Patrón de vínculo de vídeo correcto

### <a name="using-command-bars-for-settings"></a>Uso de barras de comandos para la configuración

**La figura A** representa este anti-patrón: colocar una configuración debajo de un botón de comando que se aplica a algo más que al comando. En este boceto, hay comandos además de Iniciar depuración , como Ver en el explorador, Iniciar sin depurary Depurar paso a paso por instrucciones, que respetarán la configuración seleccionada.

![Figura A: Anti pattern de la barra de comandos](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-pattern-FigureA")<br />Figura A: Anti pattern de la barra de comandos

Algo mejor, pero aún no deseado, es colocar valores de este tipo en las barras de herramientas, como se muestra en la **figura B.** Aunque los botones de división toman menos espacio y, por lo tanto, son una mejora con respecto a los menús desplegables, ambos diseños siguen usando una barra de herramientas para promover algo que no es realmente un comando.

![Figura B: Mejor, pero sigue siendo un anti pattern de la barra de comandos](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-pattern-FigureB")<br />Figura B: Mejor, pero sigue siendo un anti pattern de la barra de comandos

En el enfoque correcto que se muestra **en la figura C,** la configuración está asociada a una serie de comandos. No se establece ninguna configuración global y solo estamos cambiando entre cuatro comandos. Esta es la única situación en la que los comandos de la barra de herramientas son aceptables.

![Figura C: Uso correcto de un Visual Studio de la barra de comandos](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-pattern-FigureC")<br />Figura C: Uso correcto del patrón Visual Studio de la barra de comandos

### <a name="control-anti-patterns"></a>Control de anti patterns
 Algunos anti patterns son simplemente un uso incorrecto o una presentación de un control o grupo de controles.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Sublineado usado como etiqueta de grupo, no como hipervínculo
 El texto de sublineado solo se debe usar para hipervínculos.

 **Malo:**\
 ![El texto subrayado que no es un hipervínculo es un Visual Studio anti-patrón.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />El texto subrayado que no es un hipervínculo es un Visual Studio anti-patrón.

 **bien:**\
 ![Con el estilo correcto, el texto que no es de hipervínculo aparece sin color en la fuente del entorno.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Con el estilo correcto, el texto que no es de hipervínculo aparece sin color en la fuente del entorno.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Al hacer clic en una casilla, se genera un cuadro de diálogo emergente.
 Al hacer clic en la casilla "Habilitar Escritorio remoto para todos los roles" del asistente "Publicar Windows Aplicación de Azure", se abre inmediatamente un cuadro de diálogo emergente, un Visual Studio anti-patrón. Además, el campo de casilla no se rellena con una casilla después de seleccionarse, otro anti pattern de interacción.

 ![Abrir un cuadro de diálogo después de hacer clic en una casilla es Visual Studio anti-patrón.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />Abrir un cuadro de diálogo después de hacer clic en una casilla es Visual Studio anti-patrón.

### <a name="hyperlink-anti-patterns"></a>Antipatrones de hipervínculo
 El ejemplo siguiente contiene dos anti patterns:

1. El cambio de color rojo en primer plano al mantener el puntero significa que no se está utilizando el color compartido correcto del servicio de fuentes.

2. "Más información" no es el texto adecuado para un vínculo a un tema conceptual. El objetivo del usuario no es obtener más información, es comprender las ramificaciones de su elección.

   ![Omitir el servicio de color y usar "Más información" para hipervínculos son Visual Studio anti-patrones.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />Omitir el servicio de color y usar "Más información" para hipervínculos son Visual Studio anti-patrones.

**Mejor solución:** Haga clic en el vínculo para plantear la pregunta que el usuario haría. Por ejemplo:

- ¿Cómo funcionan los servicios de Windows Azure?

- ¿Cuándo necesito un proyecto de Mobile Services Windows Azure?

#### <a name="using-click-here-for-links"></a>Uso de "Haga clic aquí" para los vínculos
 Los hipervínculos deben ser autodescriptibles. Es un anti pattern usar "Haga clic aquí" o cualquier variación similar.

 **No está bien:** "Haga clic aquí para obtener instrucciones sobre cómo crear un nuevo proyecto".

 **Bueno:** "¿Cómo crear un nuevo proyecto?"
