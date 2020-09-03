---
title: Conceptos básicos de UX
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f3ed2d3f8bc52b21f6a87ac7d6da00f665f6b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181347"
---
# <a name="ux-essentials-for-visual-studio"></a>Fundamentos de la experiencia de usuario de Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="best-practices"></a>Procedimientos recomendados

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. sea coherente en el entorno de Visual Studio.

- Siga los patrones de interacción existentes dentro del shell.

- Diseñe características para ser coherentes con el idioma visual y los requisitos de artesano del shell.

- Usar controles y comandos compartidos cuando existan.

- Comprenda la jerarquía de Visual Studio y cómo establece el contexto y controla la interfaz de usuario.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Use el servicio de entorno para fuentes y colores.

- La interfaz de usuario debe respetar la configuración de la fuente del entorno actual a menos que se exponga para la personalización en la página fuentes y colores del cuadro de diálogo Opciones.

- Los elementos de la interfaz de usuario deben usar el servicio VSColor, mediante tokens de entorno compartidos o tokens específicos de características.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Haga que todas las imágenes sean coherentes con el nuevo VS Style.

- Siga los principios de diseño de Visual Studio para iconos, glifos y otros gráficos.

- No coloque texto en elementos gráficos.

### <a name="4-design-from-a-user-centric-perspective"></a>4. diseño desde una perspectiva centrada en el usuario.

- Cree el flujo de tareas antes de las características individuales que contiene.

- Familiarícese con los usuarios y haga que el conocimiento sea explícito en sus especificaciones.

- Al revisar la interfaz de usuario, evalúe la experiencia completa, así como los detalles.

- Diseñe la interfaz de usuario para que permanezca funcional y atractiva independientemente de la configuración regional o el idioma.

## <a name="screen-resolution"></a>Resolución de pantalla

### <a name="minimum-resolution"></a>Resolución mínima
 La resolución mínima de Visual Studio Dev14 es 1280x1024. Esto significa que es *posible* usar Visual Studio en esta solución, aunque es posible que no sea una experiencia de usuario óptima. No hay ninguna garantía de que todos los aspectos se puedan usar en resoluciones inferiores a 1280x1024.

 El tamaño inicial del cuadro de diálogo no debe superar los 1000 píxeles de alto para caber dentro del marco del IDE en esta resolución mínima en 96 ppp.

### <a name="high-density-displays"></a>Pantallas de alta densidad
 La interfaz de usuario de Visual Studio debe funcionar bien en todos los factores de escala de PPP que Windows admite de la caja: 150%, 200% y 250%.

## <a name="anti-patterns"></a>Antipatrones
 Visual Studio contiene muchos ejemplos de interfaz de usuario que siguen nuestras instrucciones y prácticas recomendadas. En un esfuerzo por ser coherente, los desarrolladores suelen tomar prestado los patrones de diseño de la interfaz de usuario del producto de forma similar a lo que están creando. Aunque se trata de un buen enfoque que nos ayuda a impulsar la coherencia en la interacción con el usuario y el diseño visual, hacemos en ocasiones enviar características con unos pocos detalles que no cumplen nuestras directrices debido a las restricciones de programación o a la priorización de defectos. En estos casos, no queremos que los equipos copien uno de estos "antipatrones" porque prolifean la interfaz de usuario incorrecta o incoherente dentro del entorno de Visual Studio.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Campos o valores obligatorios mostrados en estado de error de forma predeterminada

#### <a name="feature-team-goals"></a>Objetivos del equipo de características

- Advierta a los usuarios que han agregado un elemento que debe configurarse.

- Dibuje la atención del usuario sobre las áreas que necesitan una entrada.

#### <a name="anti-pattern-solution"></a>Solución antipatrón
 Tan pronto como el usuario haya iniciado una acción y antes de que haya completado la tarea, coloque inmediatamente los iconos de detención crítica junto a las áreas que necesiten configuración.

#### <a name="example-manifest-designer-declarations"></a>Ejemplo: declaraciones del diseñador de manifiestos
 Al agregar una declaración a la lista, se coloca inmediatamente en un estado de error, que se conserva hasta que el usuario establece las propiedades necesarias.

 En este caso, hay un problema adicional debido a que el icono que se usa para la alerta contiene una "x", por lo que no se puede usar el icono de eliminación común junto a él. Como resultado, la interfaz de usuario usa un botón quitar, un control más inadecuadas.

 ![Patrón de&#45;de declaración de error del diseñador de manifiestos](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "Patrón ManifestDesignererrordeclarationsanti")

 **Colocar la interfaz de usuario en un estado de error de forma predeterminada es un anti-patrón de Visual Studio.**

#### <a name="alternatives"></a>Alternativas
 Una solución mucho mejor para este problema sería:

- Permite al usuario agregar una declaración sin advertencia y, a continuación, desplace inmediatamente para establecer las propiedades del elemento.

- Agregue el icono de advertencia (Triángulo Dorado) cuando el foco se desplace del elemento, por ejemplo, para agregar otra declaración a la lista o para intentar cambiar las pestañas dentro del diseñador.

- Si el usuario intenta cambiar las pestañas antes de establecer las propiedades en las declaraciones, abra un cuadro de diálogo en el que se explique que la aplicación no se compilará (o las implicaciones) hasta que se resuelvan las advertencias. Si el usuario descarta el cuadro de diálogo y cambia las pestañas de todos modos, se agrega un icono (crítico o advertencia, según corresponda) a la pestaña declaraciones.

### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>Forzar al usuario a leer texto antes de descartar la interfaz de usuario

#### <a name="feature-team-goals"></a>Objetivos del equipo de características
 No permita que el usuario descarte la interfaz de usuario sin ver primero el texto de la explicación.

#### <a name="anti-pattern"></a>Antipatrón
 El equipo que inserta los vínculos de vídeo en varios lugares dentro de la interfaz de usuario de VS decidió el patrón común de un botón de cierre X y una explicación de la información sobre herramientas según lo especificado por la experiencia del usuario y, en su lugar, implementó un vínculo desplegable y "no volver a mostrar".

 ![El patrón de&#45;de texto explicativo &#45; incorrecto](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")

 **Incorrecto: obligar al usuario a leer texto explicativo antes de descartar la interfaz de usuario es un anti-patrón dentro de Visual Studio.**

#### <a name="result"></a>Resultado
 En lugar de un botón Cerrar simple (un clic), se obliga al usuario a usar dos clics para descartar simplemente la interfaz de usuario en cada lugar en el que aparezcan los vínculos de vídeo.

#### <a name="alternatives"></a>Alternativas
 El diseño correcto de esta situación sería seguir el patrón común a Internet Explorer, Office y Visual Studio: al mantener el mouse, el usuario puede ver la descripción de la información sobre herramientas y un clic para ocultar la interfaz de usuario.

 ![&#45;patrón de texto explicativo &#45; correcto](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-Pattern-correcto")

 **Correcto: como se ha diseñado, los vínculos de vídeo deben mostrar información sobre herramientas con información adicional sobre el mantener el mouse y hacer clic en la "X" debe descartar el mensaje sin necesidad de más interacción.**

### <a name="using-command-bars-for-settings"></a>Usar barras de comandos para la configuración
 ![Patrón de&#45;de la barra de comandos &#45; la figura A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-Pattern-Figuraa")

 **Figura A: Antipatrón de barra de comandos**

 La **figura A** representa este antipatrón: colocar un valor debajo de un botón de comando que se aplica a algo más que simplemente el comando. En este boceto, hay comandos además de iniciar la depuración, como ver en el explorador, iniciar sin depurar y entrar en, que respetará la configuración seleccionada.

 ![Patrón de&#45;de la barra de comandos &#45; la figura B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-Pattern-FigureB")

 **Figura B: mejor, pero todavía un Antipatrón de barra de comandos**

 Algo mejor, pero todavía no deseable, es colocar la configuración de este tipo en las barras de herramientas, como se muestra en la **figura B**. Mientras que los botones de expansión ocupan menos espacio y, por lo tanto, se mejora en las listas desplegables, ambos diseños siguen usando una barra de herramientas para promover algo que realmente no es un comando.

 ![Patrón de&#45;de la barra de comandos &#45; figura C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-Pattern-FigureC")

 **Figura C: uso correcto del patrón de barra de comandos de Visual Studio**

 En la **figura C**, la configuración está asociada a una serie de comandos. No se ha establecido ninguna configuración global y simplemente estamos cambiando entre cuatro comandos. Esta es la única situación en la que los comandos de la barra de herramientas son aceptables.

### <a name="control-anti-patterns"></a>Controlar antipatrones
 Algunos antipatrones son simplemente un uso incorrecto o una presentación de un control o un grupo de controles.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Subrayado usado como etiqueta de grupo, no como hipervínculo
 El texto de subrayado solo debe usarse para hipervínculos.

 **N**

 ![&#45;patrón de subrayado en las etiquetas de grupo](../../extensibility/ux-guidelines/media/0102-g-grouplabelincorrect.png "0102-g_GroupLabelIncorrect")

 **El texto subrayado que no es un hipervínculo es un anti-patrón de Visual Studio.**

 **Apropiado**

 ![&#45;patrón de subrayado en las etiquetas de grupo &#40;correcto&#41;](../../extensibility/ux-guidelines/media/0102-h-grouplabelcorrect.png "0102-h_GroupLabelCorrect")

 **Con el estilo correcto, el texto de hipervínculo no aparece adornado en la fuente del entorno.**

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Al hacer clic en una casilla, se genera un cuadro de diálogo emergente.
 Al hacer clic en la casilla de verificación "habilitar Escritorio remoto para todos los roles" del asistente "publicar Aplicación de Azure de Windows", se abre inmediatamente un cuadro de diálogo emergente, un Antipatrón de Visual Studio. Además, el campo de casilla no rellena con una casilla después de seleccionarse, otro Antipatrón de interacción.

 ![&#45;de pop&#45;patrón](../../extensibility/ux-guidelines/media/0102-i-checkboxpopup.png "0102-i_CheckboxPopup")

 **Abrir un cuadro de diálogo después de hacer clic en una casilla es un anti-patrón de Visual Studio.**

### <a name="hyperlink-anti-patterns"></a>Antipatrones de hipervínculo
 El ejemplo siguiente contiene dos antipatrones.

1. El color de primer plano que gira al mantener el mouse significa que no se está usando el color compartido correcto del servicio de fuentes.

2. "Más información" no es el texto adecuado para un vínculo a un tema conceptual. El objetivo del usuario es no aprender más, es comprender las ramificaciones de su elección.

   ![Patrones de hiper&#45;de hipervínculo](../../extensibility/ux-guidelines/media/0102-j-hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")

   **Omitir el servicio de color y usar "más información" para los hipervínculos son antipatrones de Visual Studio.**

   **Mejor solución:** Supongamos la pregunta que el usuario preguntaría haciendo clic en el vínculo.

- ¿Cómo funcionan los servicios de Windows Azure?

- ¿Cuándo necesito un proyecto de Microsoft Azure Mobile Services?

#### <a name="using-click-here-for-links"></a>Usar "haga clic aquí" para obtener vínculos
 Los hipervínculos deben ser autodescriptivos. Se trata de un anti-patrón para usar "haga clic aquí" o cualquier variación similar.

 **Incorrecto:** "Haga clic aquí para obtener instrucciones sobre cómo crear un nuevo proyecto".

 **Bueno:** "Cómo crear un proyecto nuevo?"
