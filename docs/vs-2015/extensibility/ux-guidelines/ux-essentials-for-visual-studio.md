---
title: Conceptos básicos de UX para Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7c9c2fe1c076a8851b1b95a9957cd721c61ae21
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799501"
---
# <a name="ux-essentials-for-visual-studio"></a>Conceptos básicos de UX para Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="best-practices"></a>Procedimientos recomendados  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Ser coherente dentro del entorno de Visual Studio.  
  
-   Seguir los patrones de interacción existente dentro del shell.  
  
-   Diseñar características que se va a ser coherente con los requisitos de idioma y la artesanía visual del shell.  
  
-   Uso compartido de comandos y controles cuando existen.  
  
-   Comprender la jerarquía de Visual Studio y cómo se establece el contexto y las unidades de la interfaz de usuario.  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Usar el servicio de entorno para las fuentes y colores.  
  
-   Interfaz de usuario debe respetar la configuración de fuente del entorno actual, a menos que se expone para la personalización en la página fuentes y colores en el cuadro de diálogo Opciones.  
  
-   Elementos de interfaz de usuario deben usar VSColor Service, mediante los tokens de entorno compartido o tokens específicos de característica.  
  
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
 La resolución mínima para Dev14 de Visual Studio es 1280 x 1024. Esto significa que es *posible* a usar Visual Studio con esta resolución, aunque quizás no sea una experiencia de usuario óptima. No hay ninguna garantía de que todos los aspectos podrá utilizarse con resoluciones inferiores a 1280 x 1024.  
  
 Tamaño inicial del cuadro de diálogo no debe superar los 1000 píxeles de alto con el fin de ajustarse el marco del IDE dentro de esta resolución mínima a 96 PPP.  
  
### <a name="high-density-displays"></a>Pantallas de alta densidad  
 Interfaz de usuario en Visual Studio debe funcionar bien en todos los factores que es compatible con Windows de fábrica para PPP: 150%, 200% y % de 250.  
  
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
  
 En este caso, hay una preocupación adicional porque el icono utilizado para la alerta contiene una "x", para quitar el común no se puede utilizar el icono junto a él. Como resultado, la interfaz de usuario usa un botón de quitar un control más rudimentarias.  
  
 ![Manifiesto de la declaración de error de diseñador anti&#45;patrón](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti patrón")  
  
 **Colocar la interfaz de usuario en un estado de error de forma predeterminada es un antipatrón de Visual Studio.**  
  
#### <a name="alternatives"></a>Alternativas  
 Una mejor solución a este problema sería:  
  
-   Permitir que el usuario agregue una declaración sin previo aviso y, a continuación, mover inmediatamente establecer propiedades en el elemento.  
  
-   Agregar el icono de advertencia (triángulo gold) al desplazar el foco desde el elemento, como agregar otra declaración a la lista o se intenta cambiar pestañas dentro del diseñador.  
  
-   Si el usuario intenta cambiar pestañas antes de establecer las propiedades en las declaraciones, mostrar un cuadro de diálogo que explica que no se compilará la aplicación (o cualquier las implicaciones) hasta que se resuelven las advertencias. Si el usuario descarte el cuadro de diálogo y cambia las tabulaciones de todos modos, a continuación, un icono (crítico o advertencia, según corresponda) se agrega a la pestaña declaraciones.  
  
### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>Hace que el usuario para leer el texto antes de descartar la interfaz de usuario  
  
#### <a name="feature-team-goals"></a>Objetivos del equipo de características  
 No permita que el usuario descartar la interfaz de usuario sin tener que ver primero el texto de explicación.  
  
#### <a name="anti-pattern"></a>Antipatrón  
 El equipo de insertar los vínculos de vídeo en varios lugares de la interfaz de usuario de VS pronunciado contra el modelo común de una X cierre botón e información sobre herramientas explicación según lo especificado por la experiencia de usuario e implementa en su lugar una lista desplegable y el vínculo "No volver a mostrar".  
  
 ![Texto explicativo anti&#45;patrón &#45; incorrecto](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")  
  
 **Incorrecto: forzar al usuario leer el texto explicativo antes de descartar la interfaz de usuario es un antipatrón dentro de Visual Studio.**  
  
#### <a name="result"></a>Resultado  
 En lugar de un botón Cerrar (un solo clic) simple, se obliga al usuario para usar dos clics para descartar simplemente la interfaz de usuario en todos los lugares que aparecen los vínculos de vídeo.  
  
#### <a name="alternatives"></a>Alternativas  
 El diseño correcto para esta situación sería siguen el patrón común para Internet Explorer, Office y Visual Studio: al mantener el mouse, el usuario puede ver la descripción de la información sobre herramientas y un solo clic oculta la interfaz de usuario.  
  
 ![Texto explicativo anti&#45;patrón &#45; correcta](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti patrón correctas")  
  
 **Correcto: según lo previsto, vínculos de vídeo deben mostrar una información sobre herramientas con información adicional al mantener el mouse y haga clic en la "X" debería descartar el mensaje sin necesidad de intervención.**  
  
### <a name="using-command-bars-for-settings"></a>Uso de las barras de comandos para la configuración  
 ![Barra de comandos anti&#45;patrón &#45; figura A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-patrón-FigureA")  
  
 **Figura A: antipatrón de barra comando**  
  
 **Figura A** representa este antipatrón: poner un valor por debajo de un botón de comando que se aplica a algo más que el comando. En este esquema, hay comandos además de iniciar la depuración, como la vista de explorador, iniciar sin depurar y paso a paso, que respetará la configuración seleccionada.  
  
 ![Barra de comandos anti&#45;patrón &#45; figura B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-patrón-FigureB")  
  
 **Figura B: mejor, pero todavía un antipatrón de barra de comandos**  
  
 Un poco mejor, pero aún indeseable, es colocar la configuración de este tipo en las barras de herramientas, como se muestra en **figura B**. Aunque los botones de expansión ocupen menos espacio y son, por tanto, una mejora a través de listas desplegables, ambos diseños todavía usa una barra de herramientas para promocionar algo que no es realmente un comando.  
  
 ![Barra de comandos anti&#45;patrón &#45; figura C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-patrón-FigureC")  
  
 **Usar figura C: correcta del patrón de barra de comandos de Visual Studio**  
  
 En **figura C**, la configuración está asociada a una serie de comandos. No hay ninguna configuración global que se va a establecer y nos estamos sólo se intercambia entre cuatro comandos. Esta es la única situación en la que los comandos en la barra de herramientas son aceptables.  
  
### <a name="control-anti-patterns"></a>Antipatrones de control  
 Algunos antipatrones son un uso incorrecto simplemente o la presentación de un control o un grupo de controles.  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Subrayado que se utiliza como una etiqueta de grupo, no un hipervínculo  
 Texto subrayado debe usarse solo para los hipervínculos.  
  
 **Erróneo:**  
  
 ![Subrayado&#45;patrón en las etiquetas de grupo](../../extensibility/ux-guidelines/media/0102-g-grouplabelincorrect.png "0102 g_GroupLabelIncorrect")  
  
 **Texto subrayado que no es un hipervínculo es un antipatrón de Visual Studio.**  
  
 **Buena:**  
  
 ![Subrayado&#45;patrón en las etiquetas de grupo &#40;correcta&#41;](../../extensibility/ux-guidelines/media/0102-h-grouplabelcorrect.png "0102 h_GroupLabelCorrect")  
  
 **Estilo correctamente, no hipervínculo texto aparece sin adornar de la fuente del entorno.**  
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Al hacer clic en los resultados de una casilla de verificación en un cuadro de diálogo emergente  
 Al hacer clic en la casilla de verificación "Habilitar Escritorio remoto para todos los roles" en el Asistente "Publicar aplicación de Windows Azure" inmediatamente, se abrirá un cuadro de diálogo emergente, un antipatrón de Visual Studio. Además, el campo de casilla de verificación no rellena con una casilla de verificación después de haberse seleccionado, otro antipatrón de interacción.  
  
 ![Casilla de verificación pop&#45;anti arriba&#45;patrón](../../extensibility/ux-guidelines/media/0102-i-checkboxpopup.png "0102 i_CheckboxPopup")  
  
 **Al abrir un cuadro de diálogo después de hacer clic en una casilla de verificación es un antipatrón de Visual Studio.**  
  
### <a name="hyperlink-anti-patterns"></a>Antipatrones de hipervínculo  
 El siguiente ejemplo contiene dos antipatrones.  
  
1. El primer plano activar rojo al mantener el mouse significa que no se está usando el color correcto compartido desde el servicio de la fuente.  
  
2. "Más" no es el texto adecuado para un vínculo a un tema conceptual. Objetivo del usuario no es más, que consiste en comprender las ramificaciones de su elección.  
  
   ![Hipervínculo anti&#45;patrones](../../extensibility/ux-guidelines/media/0102-j-hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")  
  
   **Omitiendo el servicio de color y el uso de "Obtener más información" para los hipervínculos son antipatrones de Visual Studio.**  
  
   **Una mejor solución:** suponer la pregunta al usuario haría que se esté preguntando si hace clic en el vínculo.  
  
-   ¿Cómo funcionan los servicios de Windows Azure?  
  
-   ¿Cuándo es necesario un proyecto de Windows Azure Mobile Services?  
  
#### <a name="using-click-here-for-links"></a>Uso de "Haga clic aquí" para vínculos  
 Los hipervínculos deben ser autodescriptivos. Es un antipatrón para usar "Haga clic aquí" o cualquier variación similar.  
  
 **Incorrecto:** "Haga clic aquí para obtener instrucciones sobre cómo crear un nuevo proyecto".  
  
 **Bueno:** "¿Cómo creo un nuevo proyecto?"

