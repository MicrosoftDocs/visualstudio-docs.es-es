---
title: Conceptos básicos de UX para Visual Studio | Documentos de Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac8fdabc54965d521df2552ad4f152b53a7be70a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997187"
---
# <a name="ux-essentials-for-visual-studio"></a>Conceptos básicos de UX para Visual Studio
## <a name="best-practices"></a>Procedimientos recomendados  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Ser coherente dentro del entorno de Visual Studio.  
  
-   Siga existente [patrones de interacción](interaction-patterns-for-visual-studio.md) dentro del shell.  
  
-   Diseñar características que se va a ser coherente con el lenguaje visual del shell y [requisitos artesanía](evaluation-tools-for-visual-studio.md).  
  
-   Uso compartido de comandos y controles cuando existen.  
  
-   Comprender la jerarquía de Visual Studio y cómo se establece el contexto y las unidades de la interfaz de usuario.  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Usar el servicio de entorno para las fuentes y colores.  
  
-   Interfaz de usuario debe respetar actual [fuente del entorno](fonts-and-formatting-for-visual-studio.md) configuración a menos que se expone para la personalización en la página fuentes y colores en el cuadro de diálogo Opciones.  
  
-   Elementos de interfaz de usuario deben usar el [VSColor Service](colors-and-styling-for-visual-studio.md), uso compartido de los tokens de entorno o tokens específicos de característica.  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Que sea coherente con el nuevo estilo frente a todas las imágenes.  
  
-   Siga los principios de diseño de Visual Studio para iconos, glifos y otros gráficos.  
  
-   No coloque texto en elementos gráficos.  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4. Diseñar desde una perspectiva centrada en el usuario.  
  
-   Crear el flujo de tareas antes de las características individuales dentro de él.  
  
-   Estar familiarizado con los usuarios y ponen ese conocimiento explícito en su especificación.  
  
-   Al revisar la interfaz de usuario, evaluar la experiencia completa, así como los detalles.  
  
-   Diseñar la interfaz de usuario para que permanezca funcional y atractiva, independientemente del idioma o configuración regional.  
  
## <a name="screen-resolution"></a>Resolución de pantalla  
  
### <a name="minimum-resolution"></a>Resolución mínima  
 - La resolución mínima para Dev14 de Visual Studio es **1280 x 720**. Esto significa que es *posible* a usar Visual Studio con esta resolución, aunque quizás no sea una experiencia de usuario óptima. No hay ninguna garantía de que todos los aspectos podrá utilizarse con resoluciones inferiores a 1280 x 720.  
  
 - La resolución de destino para Visual Studio es **1366 x 768**. Se trata de la resolución más baja en la que le mandaremos un *buena* experiencia del usuario.

 - Alto del cuadro de diálogo inicial debe ser **menor de 700 píxeles**, para que quepa dentro de la resolución mínima del marco del IDE a 96 PPP.
  
### <a name="high-density-displays"></a>Pantallas de alta densidad  
 Interfaz de usuario en Visual Studio debe funcionar bien en todos los factores de escala de PPP que es compatible con Windows de fábrica: 150%, 200% y % de 250.  
  
## <a name="anti-patterns"></a>Los antipatrones  
 Visual Studio contiene muchos ejemplos de interfaz de usuario que siguen nuestras directrices y procedimientos recomendados. En un esfuerzo para ser coherente, los desarrolladores a menudo tomado prestado de patrones de diseño de interfaz de usuario del producto similares a lo que está creando. Aunque esto es un buen enfoque que ayuda a nosotros unidad de coherencia en la interacción del usuario y el diseño visual, en ocasiones enviamos características con algunos detalles que no acordes a nuestras directrices debido a restricciones de programación o dar de baja prioridad. En estos casos, no queremos equipos copiar uno de estos "antipatrones" porque extienden la interfaz de usuario incorrecta o incoherente en el entorno de Visual Studio.  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Los campos/configuración necesaria que se muestra en el estado de error predeterminada  
  
#### <a name="feature-team-goals"></a>Objetivos del equipo de características  
  
-   Advertir a los usuarios que se ha agregado un elemento que se debe configurar.  
  
-   Llame la atención del usuario a las áreas que necesitan la entrada.  
  
#### <a name="anti-pattern-solution"></a>Antipatrón de solución  
 Tan pronto como el usuario ha iniciado una acción y antes de que ha completado la tarea inmediatamente coloque iconos de parada crítica junto a las áreas que necesitan una configuración.  
  
#### <a name="example-manifest-designer-declarations"></a>Ejemplo: Las declaraciones del Diseñador de manifiestos  
 Agregar una declaración a la lista inmediatamente, coloca en un estado de error, lo que se mantiene hasta que el usuario establece las propiedades necesarias.  
  
 En este caso, hay una preocupación adicional porque el icono utilizado para la alerta contiene un "&times;" icono de, por lo que no se puede usar el icono de eliminación común está junto a ella. Como resultado, la interfaz de usuario usa un botón de quitar un control más rudimentarias.  
  
 ![Colocar la interfaz de usuario en un estado de error de forma predeterminada es un antipatrón de Visual Studio. ](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti patrón")<br />Colocar la interfaz de usuario en un estado de error de forma predeterminada es un antipatrón de Visual Studio.
  
#### <a name="alternatives"></a>Alternativas  
 Una mejor solución a este problema sería:  
  
-   Permitir que el usuario agregue una declaración sin previo aviso y, a continuación, mover inmediatamente establecer propiedades en el elemento.  
  
-   Agregar el icono de advertencia (triángulo gold) al desplazar el foco desde el elemento, como agregar otra declaración a la lista o se intenta cambiar pestañas dentro del diseñador.  
  
-   Si el usuario intenta cambiar pestañas antes de establecer las propiedades en las declaraciones, mostrar un cuadro de diálogo que explica que no se compilará la aplicación (o cualquier las implicaciones) hasta que se resuelven las advertencias. Si el usuario descarte el cuadro de diálogo y cambia las tabulaciones de todos modos, a continuación, un icono (crítico o advertencia, según corresponda) se agrega a la pestaña declaraciones.  
  
### <a name="multiple-clicks-to-dismiss-ui"></a>Varios clics para descartar la interfaz de usuario  
  
#### <a name="feature-team-goals"></a>Objetivos del equipo de características  
 No permita que el usuario descartar la interfaz de usuario sin tener que ver primero el texto de explicación.  
  
#### <a name="anti-pattern"></a>Antipatrón  
 El equipo de insertar los vínculos de vídeo en varios lugares de la interfaz de usuario de VS decidió contra el modelo común de la "&times;" cerrar explicación botón e información sobre herramientas como especificado por la experiencia de usuario y en su lugar implementa una lista desplegable y "No volver a mostrar" vincula.  

#### <a name="example-video-links-in-team-explorer"></a>Ejemplo: vínculos a vídeos en Team Explorer
Hace que el usuario para leer el texto explicativo antes de descartar la interfaz de usuario es un antipatrón dentro de Visual Studio. Vínculos correctamente diseñado, vídeo deben mostrar una información sobre herramientas con información adicional de mantener el mouse y haga clic en el "&times;" debe descartar el mensaje sin necesidad de intervenciones del usuario.


 ![Texto explicativo anti&#45;patrón &#45; incorrecto](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Patrón de vínculo de vídeo incorrecto
  
#### <a name="result"></a>Resultado  
 En lugar de un botón Cerrar (un solo clic) simple, se obliga al usuario para usar dos clics para descartar simplemente la interfaz de usuario en todos los lugares que aparecen los vínculos de vídeo.  
  
#### <a name="alternatives"></a>Alternativas  
 El diseño correcto para esta situación sería siguen el patrón común para Internet Explorer, Office y Visual Studio: al mantener el mouse, el usuario puede ver la descripción de la información sobre herramientas y un solo clic oculta la interfaz de usuario.  
  
 ![Texto explicativo anti&#45;patrón &#45; correcta](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti patrón correctas")<br />Patrón de vínculo de vídeo correcto
  
### <a name="using-command-bars-for-settings"></a>Uso de las barras de comandos para la configuración  
 **Figura A** representa este antipatrón: poner un valor por debajo de un botón de comando que se aplica a algo más que el comando. En este esquema, hay comandos además de iniciar la depuración, como la vista de explorador, iniciar sin depurar y paso a paso, que respetará la configuración seleccionada.  

  ![Figura A: Antipatrón de barra de comandos](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-patrón-FigureA")<br />Figura A: Antipatrón de barra de comandos
  
 Un poco mejor, pero aún indeseable, es colocar la configuración de este tipo en las barras de herramientas, como se muestra en **figura B**. Aunque los botones de expansión ocupen menos espacio y son, por tanto, una mejora a través de listas desplegables, ambos diseños todavía usa una barra de herramientas para promocionar algo que no es realmente un comando.  
 
 ![Figura B: Mejor, pero todavía un antipatrón de barra de comandos](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-patrón-FigureB")<br />Figura B: Mejor, pero todavía un antipatrón de barra de comandos
 
  En el enfoque correcto que se muestra en **figura C**, la configuración está asociada a una serie de comandos. No hay ninguna configuración global que se va a establecer y nos estamos sólo se intercambia entre cuatro comandos. Esta es la única situación en la que los comandos en la barra de herramientas son aceptables. 

 ![Figura C: Corrija el uso del patrón de barra de comandos de Visual Studio](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-patrón-FigureC")<br />Figura C: Uso correcto de patrón de barra de comandos de Visual Studio
   
### <a name="control-anti-patterns"></a>Antipatrones de control  
 Algunos antipatrones son un uso incorrecto simplemente o la presentación de un control o un grupo de controles.  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Subrayado que se utiliza como una etiqueta de grupo, no un hipervínculo  
 Texto subrayado debe usarse solo para los hipervínculos.  
  
 **Erróneo:**    
 ![Texto subrayado que no es un hipervínculo es un antipatrón de Visual Studio. ](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 g_GroupLabelIncorrect")<br />Texto subrayado que no es un hipervínculo es un antipatrón de Visual Studio.
  
 **Buena:**   
 ![Estilo correctamente, no hipervínculo texto aparece sin adornar de la fuente del entorno. ](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 h_GroupLabelCorrect")<br />Estilo correctamente, no hipervínculo texto aparece sin adornar de la fuente del entorno.
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Al hacer clic en los resultados de una casilla de verificación en un cuadro de diálogo emergente  
 Al hacer clic en la casilla de verificación "Habilitar Escritorio remoto para todos los roles" en el Asistente "Publicar aplicación de Windows Azure" inmediatamente, se abrirá un cuadro de diálogo emergente, un antipatrón de Visual Studio. Además, el campo de casilla de verificación no rellena con una casilla de verificación después de haberse seleccionado, otro antipatrón de interacción.  
  
 ![Al abrir un cuadro de diálogo después de hacer clic en una casilla de verificación es un antipatrón de Visual Studio. ](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 i_CheckboxPopup")<br />Al abrir un cuadro de diálogo después de hacer clic en una casilla de verificación es un antipatrón de Visual Studio.
  
### <a name="hyperlink-anti-patterns"></a>Antipatrones de hipervínculo  
 El siguiente ejemplo contiene dos antipatrones.  
  
1. El primer plano activar rojo al mantener el mouse significa que no se está usando el color correcto compartido desde el servicio de la fuente.  
  
2. "Más" no es el texto adecuado para un vínculo a un tema conceptual. Objetivo del usuario no es más, que consiste en comprender las ramificaciones de su elección.  
  
   ![Omitiendo el servicio de color y el uso de "Obtener más información" para los hipervínculos son antipatrones de Visual Studio. ](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")<br />Omitiendo el servicio de color y el uso de "Obtener más información" para los hipervínculos son antipatrones de Visual Studio.  
  
   **La mejor solución:** Suponer la pregunta al usuario haría que se esté preguntando si hace clic en el vínculo.  
  
-   ¿Cómo funcionan los servicios de Windows Azure?  
  
-   ¿Cuándo es necesario un proyecto de Windows Azure Mobile Services?  
  
#### <a name="using-click-here-for-links"></a>Uso de "Haga clic aquí" para vínculos  
 Los hipervínculos deben ser autodescriptivos. Es un antipatrón para usar "Haga clic aquí" o cualquier variación similar.  
  
 **Erróneo:** "Haga clic aquí para obtener instrucciones sobre cómo crear un nuevo proyecto".
  
 **Buena:** "¿Cómo creo un nuevo proyecto?"