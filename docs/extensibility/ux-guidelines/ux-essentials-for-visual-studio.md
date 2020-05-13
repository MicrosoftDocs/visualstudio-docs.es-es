---
title: UX Essentials para Visual Studio ? Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6c329eda477d77ab73be2ad913ac18d67ff3c08
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698328"
---
# <a name="ux-essentials-for-visual-studio"></a>Fundamentos de la experiencia de usuario de Visual Studio

## <a name="best-practices"></a>Procedimientos recomendados

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Sea coherente en el entorno de Visual Studio.

- Siga los patrones de [interacción](interaction-patterns-for-visual-studio.md) existentes dentro del shell.

- Diseño de características para ser coherente con el lenguaje visual de la cáscara y [los requisitos de artesanía.](evaluation-tools-for-visual-studio.md)

- Utilice comandos y controles compartidos cuando existan.

- Comprender la jerarquía de Visual Studio y cómo establece el contexto y controla la interfaz de usuario.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Utilice el servicio de entorno para fuentes y colores.

- La interfaz de usuario debe respetar la configuración de fuente de [entorno](fonts-and-formatting-for-visual-studio.md) actual a menos que se exponga para su personalización en la página Fuentes y colores del cuadro de diálogo Opciones.

- Los elementos de interfaz de usuario deben usar el [servicio VSColor,](colors-and-styling-for-visual-studio.md)mediante tokens de entorno compartido o tokens específicos de la característica.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Haga que todas las imágenes sean coherentes con el nuevo estilo VS.

- Siga los principios de diseño de Visual Studio para iconos, glifos y otros gráficos.

- No coloque texto en elementos gráficos.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Diseño desde una perspectiva centrada en el usuario.

- Cree el flujo de tareas antes de las entidades individuales que contiene.

- Familiarícese con sus usuarios y haga que ese conocimiento sea explícito en sus especificaciones.

- Al revisar la interfaz de usuario, evalúe la experiencia completa, así como los detalles.

- Diseña tu interfaz de usuario para que siga siendo funcional y atractiva independientemente de la configuración regional o el idioma.

## <a name="screen-resolution"></a>Resolución de pantalla

### <a name="minimum-resolution"></a>Resolución mínima

- La resolución mínima para Visual Studio 2015 es **1280x720**. Esto significa que es *posible* usar Visual Studio en esta resolución, aunque podría no ser una experiencia de usuario óptima. No hay garantía de que todos los aspectos sean utilizables en resoluciones inferiores a 1280x720.

- La resolución de destino para Visual Studio es **1366x768**. Esta es la resolución más baja en la que prometemos una *buena* experiencia de usuario.

- La altura inicial del cuadro de diálogo debe ser inferior a **700 píxeles,** por lo que se ajusta a la resolución mínima del marco IDE a 96 ppp.

### <a name="high-density-displays"></a>Pantallas de alta densidad
 La interfaz de usuario de Visual Studio debe funcionar bien en todos los factores de escalado de PPP que Windows admite de forma inmediata: 150%, 200% y 250%.

## <a name="anti-patterns"></a>Antipatrones
 Visual Studio contiene muchos ejemplos de interfaz de usuario que siguen nuestras directrices y procedimientos recomendados. En un esfuerzo por ser coherentes, los desarrolladores a menudo toman prestados de patrones de diseño de interfaz de usuario de productos similares a lo que están creando. Aunque este es un buen enfoque que nos ayuda a impulsar la coherencia en la interacción del usuario y el diseño visual, en ocasiones en ocasiones enviamos características con algunos detalles que no cumplen con nuestras directrices debido a restricciones de programación o priorización de defectos. En estos casos, no queremos que los equipos copien uno de estos "antipatrones" porque proliferan la interfaz de usuario incorrecta o incoherente dentro del entorno de Visual Studio.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Campos/configuraciones obligatorios mostrados en estado de error de forma predeterminada

#### <a name="feature-team-goals"></a>Objetivos del equipo destacado

- Advierta a los usuarios que han agregado un elemento que se debe configurar.

- Atraiga la atención del usuario sobre las áreas que necesitan entrada.

#### <a name="anti-pattern-solution"></a>Solución anti-patrón
 Tan pronto como el usuario haya iniciado una acción y antes de que haya completado la tarea, coloque inmediatamente iconos de parada crítica junto a las áreas que necesitan configuración.

#### <a name="example-manifest-designer-declarations"></a>Ejemplo: Declaraciones de Manifest Designer
 Agregar una declaración a la lista la coloca inmediatamente en un estado de error, que persiste hasta que el usuario establece las propiedades necesarias.

 En este caso, hay una preocupación adicional porque el&times;icono utilizado para la alerta contiene un icono " ", por lo que el icono de eliminación común no se puede utilizar junto a él. Como resultado, la interfaz de usuario usa un botón Quitar, un control más torpe.

 ![Colocar la interfaz de usuario en un estado de error de forma predeterminada es un antipatrón de Visual Studio.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-pattern")<br />Colocar la interfaz de usuario en un estado de error de forma predeterminada es un antipatrón de Visual Studio.

#### <a name="alternatives"></a>Alternativas

Una mejor solución a este problema es:

- Permitir al usuario agregar una declaración sin advertencia y, a continuación, mover inmediatamente para establecer propiedades en el elemento.

- Agregue el icono de advertencia (triángulo dorado) cuando el foco se mueva desde el elemento, como agregar otra declaración a la lista o intentar cambiar las pestañas dentro del diseñador.

- Si el usuario intenta cambiar las pestañas antes de establecer propiedades en cualquier declaración, haga clic en un cuadro de diálogo que explique que la aplicación no se compilará (o cualquiera que sean las implicaciones) hasta que se resuelvan las advertencias. Si el usuario descarta el cuadro de diálogo y cambia las pestañas de todos modos, se agrega un icono (crítico o de advertencia, según corresponda) a la pestaña Declaraciones.

### <a name="multiple-clicks-to-dismiss-ui"></a>Múltiples clics para descartar la interfaz de usuario

#### <a name="feature-team-goals"></a>Objetivos del equipo destacado
 No permita que el usuario descarte la interfaz de usuario sin ver primero el texto de explicación.

#### <a name="anti-pattern"></a>Anti-patrón
 El equipo que inserta los vínculos de vídeo en varios lugares dentro de la interfaz de usuario de VS decidió en contra del patrón común del botón "&times;" cerrar y la explicación de información sobre herramientas según lo especificado por LA experiencia de usuario, y en su lugar implementó un menú desplegable y "No volver a mostrar".

#### <a name="example-video-links-in-team-explorer"></a>Ejemplo: Enlaces de vídeo en Team Explorer
Obligar al usuario a leer texto explicativo antes de descartar la interfaz de usuario es un antipatrón dentro de Visual Studio. Correctamente diseñados, los enlaces de vídeo deben mostrar una&times;información sobre herramientas con información adicional al mantener el mouse, y al hacer clic en el botón " " debe descartar el mensaje sin necesidad de más interacción.

 ![Texto explicativo anti patrón de&#45;&#45; incorrecto](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Patrón de enlace de vídeo incorrecto

En lugar de un simple botón de cierre (un clic), el usuario se ve obligado a usar dos clics para simplemente descartar la interfaz de usuario en cada lugar en el que aparezcan los vínculos de vídeo.

El diseño correcto para esta situación es seguir el patrón común a Internet Explorer, Office y Visual Studio: al mantener el mouse, el usuario puede ver la descripción de información sobre herramientas y un clic oculta la interfaz de usuario.

 ![Texto explicativo anti patrón&#45;&#45; correcto](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explicativoanti-patrón-correcto")<br />Corregir el patrón de enlace de vídeo

### <a name="using-command-bars-for-settings"></a>Uso de barras de comandos para la configuración

**La figura A** representa este antipatrón: colocar una configuración debajo de un botón de comando que se aplica a algo más que el comando. En este boceto, hay comandos además de Iniciar depuración, como Ver en el navegador, Iniciar sin depurar y Paso a paso, que respetarán la configuración seleccionada.

![Figura A: Barra de comandos antipatrón](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-pattern-FigureA")<br />Figura A: Barra de comandos antipatrón

Ligeramente mejor, pero todavía indeseable, es poner la configuración de este tipo en las barras de herramientas, como se muestra en **la figura B**. Mientras que los botones divididos toman menos espacio y, por lo tanto, son una mejora sobre los menús desplegables, ambos diseños todavía están utilizando una barra de herramientas para promover algo que no es realmente un comando.

![Figura B: Mejor, pero sigue siendo una barra de comandos anti-patrón](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-pattern-FigureB")<br />Figura B: Mejor, pero sigue siendo una barra de comandos anti-patrón

En el enfoque correcto que se muestra en **la figura C**, la configuración está vinculada a una serie de comandos. No hay ninguna configuración global que se establece y sólo estamos cambiando entre cuatro comandos. Esta es la única situación en la que los comandos de la barra de herramientas son aceptables.

![Figura C: Uso correcto del patrón de barra de comandos de Visual Studio](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-pattern-FigureC")<br />Figura C: Uso correcto del patrón de barra de comandos de Visual Studio

### <a name="control-anti-patterns"></a>Controlar antipatrones
 Algunos antipatrones son simplemente un uso incorrecto o la presentación de un control o grupo de controles.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Subrayado utilizado como etiqueta de grupo, no como hipervínculo
 El texto subrayado solo debe utilizarse para hipervínculos.

 **Malo:**\
 ![El texto subrayado que no es un hipervínculo es un antipatrón de Visual Studio.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />El texto subrayado que no es un hipervínculo es un antipatrón de Visual Studio.

 **bien:**\
 ![Con el estilo correcto, el texto que no es de hipervínculo aparece sin adornos en la fuente del entorno.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Con el estilo correcto, el texto que no es de hipervínculo aparece sin adornos en la fuente del entorno.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Al hacer clic en una casilla de verificación, aparece un cuadro de diálogo emergente
 Al hacer clic en la casilla de verificación "Habilitar Escritorio remoto para todos los roles" en el asistente "Publicar aplicación de Windows Azure" aparece inmediatamente un cuadro de diálogo emergente, un antipatrón de Visual Studio. Además, el campo de casilla de verificación no se rellena con una casilla de verificación después de haber sido seleccionado, otro antipatrón de interacción.

 ![Al abrir un cuadro de diálogo después de hacer clic en una casilla de verificación, es un antipatrón de Visual Studio.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />Al abrir un cuadro de diálogo después de hacer clic en una casilla de verificación, es un antipatrón de Visual Studio.

### <a name="hyperlink-anti-patterns"></a>Antipatrones de hipervínculo
 El ejemplo siguiente contiene dos antipatrones:

1. El primer plano que se vuelve rojo al mantener el mouse significa que no se está utilizando el color compartido correcto del servicio de fuentes.

2. "Aprender más" no es el texto adecuado para un enlace a un tema conceptual. El objetivo del usuario no es aprender más, es entender las ramificaciones de su elección.

   ![Ignorar el servicio de color y usar "Más información" para hipervínculos son antipatrones de Visual Studio.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />Ignorar el servicio de color y usar "Más información" para hipervínculos son antipatrones de Visual Studio.

**Mejor solución:** Haga la pregunta que el usuario estaría haciendo haciendo clic en el enlace. Por ejemplo:

- ¿Cómo funcionan los servicios de Windows Azure?

- ¿Cuándo necesito un proyecto de Windows Azure Mobile Services?

#### <a name="using-click-here-for-links"></a>Uso de "Haga clic aquí" para enlaces
 Los hipervínculos deben ser autodescriptivos. Es un anti-patrón para utilizar "Haga clic aquí" o cualquier variación similar.

 **Malo:** "Haga clic aquí para obtener instrucciones sobre cómo crear un nuevo proyecto."

 **Bien:** "¿Cómo puedo crear un nuevo proyecto?"
