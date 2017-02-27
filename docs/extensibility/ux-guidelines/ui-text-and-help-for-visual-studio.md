---
title: "Texto de la interfaz de usuario y la Ayuda de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: 2
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 2
---
# Texto de la interfaz de usuario y la Ayuda de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_UITextAndTerminology"></a> Terminología y el texto de la interfaz de usuario  
 Texto comprensible es fundamental para la interfaz de usuario eficaz. Los usuarios de software tienden a leer las etiquetas en primer lugar, es decir, los más importantes para completar la tarea en cuestión. Se lee el texto estático con menos frecuencia. Plan para que los usuarios inician sus sesiones de trabajo con un examen rápido de la ventana entera, seguido de una lectura de la interfaz de usuario en un orden aproximado:  
  
1.  Controles interactivos en el centro  
  
2.  Confirmar botones  
  
3.  Controles interactivos que se encuentra en otra parte  
  
4.  Instrucciones principales  
  
5.  Explicaciones adicionales  
  
6.  Título de la ventana  
  
7.  Cualquier otro texto estático en el cuerpo principal  
  
### Patrones de uso para el texto de la interfaz de usuario  
  
#### Texto de la barra de título  
 Texto de la barra de título debe coincidir con el comando que genera la interfaz de usuario.  
  
#### Instrucciones \(texto auxiliar\)  
 En algunos cuadros de diálogo, es útil proporcionar instrucciones principales importantes para explicar qué hacer en la ventana o en la página. Esto se conoce a veces como "texto auxiliar".  
  
##### Escribir reglas de estilo para el texto de ayuda  
  
-   No explique lo obvio. A menos que sea absolutamente necesario, no incluya texto informativo.  
  
-   Texto informativo se coloca siempre en la parte superior del cuadro de diálogo y debe hacer referencia a la tarea que esté realizando.  
  
-   Precisamente explicar a los usuarios que necesitan para hacer. Evitar la redundancia y comunicación excesivo.  
  
-   Revise cada ventana y eliminar las instrucciones y las palabras duplicadas.  
  
-   Mantenga el texto informativo breve. Si más información es necesario para determinados usuarios o escenarios, a continuación, proporcione un vínculo a un tema en línea conceptual detallado.  
  
-   Escriba el texto para que contiene el peso de cada palabra y es necesario.  
  
-   Siga las instrucciones de Microsoft existente para [texto de la interfaz de usuario](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) y [estilo y el tono](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### Instrucciones adicionales  
 Instrucciones adicionales proporcionan información adicional que ayuda al usuario a entender los controles o agrupaciones de control. Esto puede incluir también el necesaria para comprender qué formato está esperando el control de entrada de texto de sugerencia. Debe utilizar instrucciones adicionales. Reservarlos para casos donde es probable que el usuario no comprenden completamente las consecuencias de la elección que están haciendo.  
  
 ![Supplemental text in Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601\-b\_SupplementalText1")  
  
 **Texto complementario en Visual Studio**  
  
 ![Supplemental text in Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601\-c\_SupplementalText2")  
  
 **Texto complementario en Visual Studio**  
  
#### Recuadros informativos  
 A menudo, el texto informativo puede ser demasiado largo para colocar en lugar de la interfaz de usuario o puede ser útil para los nuevos usuarios, se siente como confusión a los usuarios experimentados. En este caso, debe colocarse el texto informativo informativo como una información sobre herramientas en un recuadro informativo.  
  
 Recuadros informativos deben colocarse cerca de los controles que están relacionados con y que debe usar el icono de recuadro informativo específico, que aún es discreto apreciable.  
  
 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601\-d\_InfoTip")  
  
 **Ejemplo de un recuadro informativo en Visual Studio**  
  
##### Reglas de estilo de escritura de recuadros informativos  
  
-   Escribir recuadros informativos como frases completas. Requieren verbos específicos, en caso de frase y puntuación de cierre.  
  
-   Use recuadros informativos para complementar la instrucción principal o la información. Si simplemente está utilizando palabras distintas para volver a plantear la idea principal, no es necesario un recuadro informativo.  
  
-   Mantener recuadros informativos breve y elegante. Utilice palabras pequeño y simple, lenguaje cotidiano que admite y favorece el usuario.  
  
-   Siga las instrucciones de Microsoft existente para [texto de la interfaz de usuario](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) y [estilo y el tono](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### Etiquetas de control  
 Etiquetas de control deben ser breve y concisa y seguir el [orientación de escritorio de Windows para los controles](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx).  
  
 Para obtener más información acerca de cómo controlar el formato de etiqueta y la ubicación dentro de la interfaz de usuario, consulte [Diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### Vínculos de ayuda  
 Vínculos de ayuda o bien pueden colocarse dentro de texto informativo o en el cuerpo de la interfaz de usuario. Pueden ser vínculos a la Ayuda o inician cuadros de diálogo internos.  
  
##### Reglas de estilo visual de los vínculos de ayuda  
  
-   Utilice los colores del entorno correcto para los hipervínculos. Un hipervínculo con estilo correctamente no parpadeará brevemente en rojo cuando se hace clic. Si ve esto, es una indicación de que no se usan colores del entorno.  
  
-   Subrayados sólo deben utilizarse en al mantener el mouse o cuando el vínculo se incrusta en un párrafo.  
  
-   Para obtener más información sobre los estilos visuales y de interacción para los hipervínculos, consulte botones e hipervínculos.  
  
##### Escribir reglas de estilo para los vínculos de ayuda  
  
-   Al iniciar los cuadros de diálogo, mantener los estándares para los puntos suspensivos: no hay puntos suspensivos para la exploración, elipses, si la tarea requiere la interfaz de usuario adicional.  
  
     ![Help link in Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601\-e\_HelpLink")  
  
     **Puntos suspensivos \(...\) en la Ayuda de un vínculo indica que la tarea requiere la interfaz de usuario adicional.**  
  
-   Vínculos no deben comenzar con "Aprender", ya no es la intención del usuario. El usuario desea responder a una pregunta específica, no reciben una educación general.  
  
-   Ayuda de frase vínculos para que le piden a la pregunta que responderá el tema.  
  
     Correcto:  
     "Más información sobre los precios de servicios móviles de Azure"  
  
     Corregir:  
     "¿Qué opciones de precios están disponibles para servicios móviles de Windows Azure?"  
  
-   Nunca use *haga clic en...* para el texto del vínculo.  
  
-   Nunca vincule la palabra "aquí". Esto es problemático para algunos lectores de pantalla que se voz solo la palabra hipervinculada.  
  
     Correcto:  
     "Buscar información en los servicios móviles de Windows Azure **aquí**"  
  
     Corregir:  
     "¿Qué opciones de precios están disponibles para servicios móviles de Windows Azure?"  
  
-   Para obtener más información sobre el estilo de escritura correcta para los vínculos de ayuda, consulte el [orientación de escritorio de Windows para obtener ayuda](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742494\(v=vs.85\).aspx).  
  
#### Texto de sugerencia  
 Texto de sugerencia aparece como una marca de agua en un control o debajo del control. Se aplicará el formato correcto mediante el token adecuado de VSColors, `Environment.GrayText`.  
  
 Pueden aparecer en varios formatos.  
  
-   En lugar de la etiqueta de control:  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601\-f\_HintText1")  
  
-   Con un verbo que dé instrucciones:  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601\-g\_HintText2")  
  
-   Con el texto que indica una entrada requerida:  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601\-h\_HintText3")  
  
#### Texto de marca de agua  
 En una superficie de diseño vacía, el texto debe indicar qué hacer así como proporcionar vínculos para abrir otras ventanas relacionadas, si procede:  
  
 ![Watermark text in Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601\-i\_WatermarkText")  
  
 **Ejemplo de texto de marca de agua en Visual Studio**  
  
### Terminología común  
  
|Término|Explicación|Comentario|  
|-------------|-----------------|----------------|  
|Iniciar sesión \/ cerrar sesión|Verbos utilizados como sinónimo de la web para representar la autenticación en una propiedad de la web. Dentro de los clientes, usamos esta vez como una noción de nivel superior para firmar dentro y fuera de conexión de usuario IDE, que representa una identidad de nivel superior que proporciona capacidades de nivel superior como la itinerancia y licencias que no están disponibles con todas las otras conexiones.|El usuario de IDE es la única característica que se debe representar un inicio de sesión \/ cerrar sesión verbo, que representa el usuario IDE de nivel superior.|  
|Conectar \/ desconectar|Utilizar en lugares donde una característica mantiene una única conexión a un servicio en línea.|Explorador de servidores, donde solo puede tener una conexión activa de Azure a la vez, es un ejemplo de conectar o desconectar.|  
|Agregar o quitar|No destructiva. Utilice al agregar o quitar elementos de una lista.|El cuadro de diálogo de lista de servidor TFS Connection Manager es un ejemplo de agregar o quitar.|  
|Eliminar|Destructiva. Utilice únicamente cuando se descarta permanentemente el elemento que se quita o elimina del disco.|En general, "Delete" requiere un símbolo del sistema si el resultado elimina un archivo de disco.|  
  
## Mensajes de error  
  
### Información general  
 Se producen errores. Establecer limitaciones en lo que puede hacer el usuario es el primer paso para evitar que los mensajes de error evitables sensato. Sin embargo, cuando se produce un error, un mensaje de error bien escrito puede ir un largo camino para mitigar el problema. Mensajes de error son probablemente uno de los tipos más importantes de notificación que ve el usuario, ya que son sincrónicas e indican un problema que debe resolverse. Mensajes de error mal escrita dejar a los usuarios en sus propias para decidir la causa de los errores y las posibles soluciones.  
  
 Los usuarios pueden dejar de prestar atención al sobreutilizado o confusos mensajes de error, por lo que la experiencia de los mensajes de escritura solo es necesario que agregan valor al usuario. Si el mensaje es simplemente una notificación, utilice una presentación alternativa.  
  
### Reglas para crear un mensaje de error  
  
-   Al construir los mensajes de error, elija el nivel de error adecuado para la audiencia. El objetivo es sencillos resúmenes que proporcionan una acción que puede realizar el usuario, si procede. Estado de no todo lo que el usuario no necesita saber.  
  
-   Proporcionar asistencia implícita. Es más fácil de leer y actuar en un mensaje de error que contiene la instrucción.  
  
-   No utilice negativos dobles.  
  
-   Realizar ambos automáticamente y comprobación una ortografía y la gramática manual en cualquier mensaje de error que se escribe.  
  
-   Mensajes de error complejo, evitar comunicaciones secuenciales. Nunca utilice un enlace de F1 para el mensaje de error. El propio mensaje debería ser suficiente.  
  
-   Utilice el icono adecuado.  
  
-   Realizar preguntas fáciles de entender y usar los botones que tienen opciones claras, como "Delete" y "Cancelar".  
  
-   Para las advertencias, tener claro cuál será la desventaja de continuar. Los botones deberían indicar el resultado.  
  
-   Para errores, se describe lo que el usuario puede hacer para solucionar el problema. Botones deben acciones o diga "Cerrar". No use un botón "Aceptar" para un mensaje de error.  
  
-   Algunas preguntas que preguntarse al construir un mensaje de error:  
  
    -   ¿Puede averiguar el usuario de cómo resolver el problema con este error solo?  
  
    -   ¿El usuario utiliza el vocabulario del mismo que este error?  
  
    -   ¿Se esta ambiguo de error o se comparte en varias situaciones? ¿Si es así, cómo guía a los usuarios a la solución que necesitan?  
  
#### Errores de compilación  
 Puesto que Visual Studio es una herramienta de desarrollo de software, muchos de sus componentes tienen una compilación, convertir o codificación de paso para convertir el trabajo del desarrollador en formato binario. Estas conversiones pueden producir errores cuando el compilador no puede procesar archivos creados de forma incorrecta o cuando las opciones del compilador no se han establecido correctamente.  
  
 Usuarios de Visual Studio pueden pasar un número enorme de horas de desarrollo resolver errores de compilación. Este tiempo de resolución aumenta cuando los errores tienen dependencias o cuando los mensajes de error mal escritos, lo que puede dificultar a descubrir el origen del error.  
  
 Los errores de compilación mejor son aquellos que no se producen en primer lugar, razón por la cual Visual Studio proporciona la función Autocompletar y líneas en zigzag IntelliSense. Controles de validación de esquema y herramientas similares ofrecen el mismo tipo de comentarios. Estos mecanismos proactivamente guiarán al usuario para construir código correcto, lo que reduce la posibilidad de errores de compilación.  
  
 Visual Studio proporciona una ventana de herramientas que los usuarios pueden leer y desplazarse por los errores que se produjeron en las ventanas de documento. Métodos abreviados de teclado se proporcionan para que el usuario rápidamente puede navegar por grandes cantidades de código e ir directamente a la ubicación del problema. Visual Studio también permite a cada error de compilación para vincularse a un identificador de palabra clave y el contexto de ayuda determinado para que el usuario puede ir directamente a un tema de ayuda que proporciona información más detallada sobre el error.  
  
 Errores de compilación clara y concisa de escribir:  
  
-   **Utilizar un lenguaje claro** que explica el problema con poca o ninguna jerga de compilador. El texto de un error de compilación no debe ser demasiado técnico.  
  
-   **Describir las causas posibles.** Por ejemplo, "faltan dos puntos entre la propiedad y valor en el ' \(propiedad\): \(valor\)' declaración."  
  
-   Proporciona detalles acerca de posibles correcciones. Si no hay espacio suficiente, se pueden poner detalles adicionales en el tema de ayuda correspondiente.  
  
### Componentes de un mensaje de error bien escritos  
  
#### Usar el servicio de cuadro de diálogo de shell para mensajes de error.  
 Mediante el servicio de cuadro de diálogo de shell le permite controlar la apariencia del mensaje: fuentes en particular, sin cambios importantes en los elementos individuales. Utilice la **IErrorInfo** mecanismos y registrarlos mediante **IVsUIShell::SetErrorInfo\/ReportErrorInfo**.  
  
#### Elija una presentación eficaz y adecuada de notificación.  
 Utilice un cuadro de diálogo modal con una advertencia crítica si se requiere una acción inmediata para evitar la pérdida de datos \(notificación sincrónica\). Iconos críticos están reservados para las situaciones en que al cerrar el mensaje sin leer pueden producir consecuencias negativas. Pérdida de datos es una situación crítica que requiere una respuesta de nivel de alarma. El uso excesivo del icono crítico desensitizes a los usuarios de su importancia. Si el mensaje de error es de naturaleza informativa, considere alternativas a un cuadro de diálogo modal \(notificación asincrónica\).  
  
#### Proporcionar una explicación limpia y concisa de la causa del problema en lugar de una explicación técnica.  
 Sobrecargar los usuarios con los detalles técnicos en la explicación se hacerlos más probable pasar por alto los mensajes de error. Ejemplos de buenas mensajería:  
  
-   "No se puede abrir el archivo solicitado."  
  
-   "No se puede conectar a Internet."  
  
#### Proporciona información sobre cómo corregir el problema.  
 Ofrecen las sugerencias de usuario para resolver el problema. Ser honesto con el usuario si no hay ninguna sugerencia. Proporcionar vínculos directos a los orígenes en línea alternativos, como el soporte técnico o soporte de la Comunidad. Pruebe a dirigir a los usuarios a información en línea específica pertinente para el problema. Para un identificador de error, considere la posibilidad de vincular los usuarios a un subproceso de discusión acerca del error específico. Ejemplos de buenas mensajería:  
  
-   "Asegúrese de que está conectado a Internet y vuelva a intentarlo".  
  
-   "Asegúrese de que el archivo existe y que tiene permiso para abrirlo".  
  
#### Escribir un mensaje breve y al punto.  
 Puede notificar un mensaje de error, explicar y ofrecen una solución, pero todavía se omite si es demasiado verboso. Una solución consiste en usar revelación progresiva con un botón de detalles. Por ejemplo, proporcionar una descripción corta o solución y coloque más detalles en un botón de detalles. Si los usuarios deciden obtener más información sobre el error, pueden hacerlo.  
  
 El idioma en el mensaje debe ser:  
  
-   **Dominio adecuado.** Usar lenguaje que comprenderá el usuario. Aunque nuestros clientes son los desarrolladores, a menudo no tienen el contexto y la terminología que tenemos.  
  
-   **Específica.** Evite redacción imprecisa y asigne nombres específicos y ubicaciones de los objetos implicados. Por ejemplo, un mensaje de error como"carácter no válido" no es útil. ¿El carácter? "Archivo no encontrado". ¿Qué archivo?  
  
-   **Correcto.** No es culpa del usuario. Evitar lenguaje ofensivo u hostil \(eliminar, ejecutar, finalizar, grave, no válido\). Evite el texto en mayúsculas, que a menudo se ve como gritar y no es legible como. No utilice el humor.  
  
-   **Corregir.** Usar la gramática y la ortografía correcta \(incluso en premultiplicadas\). Si hay errores ortográficos son profesional e incómodo.  
  
-   **Contexto apropiado.** Utilice el texto del botón correspondiente. Evite el botón "Aceptar" y en su lugar, use "Continue" o "Sí\/No".  
  
### Ejemplos de mensajes de error  
  
|Bueno|Incorrecta|  
|-----------|----------------|  
|"El número marcado ya no está en servicio. Compruebe el número y vuelva a marcar o marcar 0 para el operador."|-   "Error \(449\): número no válido"<br />-   "Este error de excepción no controlada indica que la operación se completó correctamente".<br /><br /> ![Bad error message in Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602\-a\_ErrorDialog")|  
  
## Acceso a la Ayuda  
  
### Información general  
 Además de la documentación de MSDN, un usuario de Visual Studio tiene varios puntos de acceso para ayudar al usuario en la interfaz de usuario. Para asegurarse de que estos puntos de acceso están disponibles de forma coherente, equipos de características necesitan aprovechar el sistema de ayuda que ofrece el entorno. Estos puntos de acceso son:  
  
-   **Texto informativo y adicional en los cuadros de diálogo.** Texto estático que proporciona la dirección o la explicación, en la interfaz de usuario disponible al mantener el mouse sobre un icono de recuadro informativo o superficie.  
  
-   **Ayuda F1** \(solo editor\). En el editor de Visual Studio, un usuario puede confiar en que en cualquier momento, al presionar F1, se abrirá un tema de ayuda específica para la selección actual. Asegúrese de que los temas asociados con F1 adecuado e informativos.  
  
-   **Hipervínculos a temas de ayuda.** Un hipervínculo dentro de un cuadro de diálogo, la ventana de herramientas o la superficie de diseño que inicia un tema para ayudar al usuario obtener más información acerca de una tecnología, la capacidad o la información acerca de cómo realizar una tarea.  
  
-   **Mecanismos de interfaz de usuario de auxiliar, como etiquetas inteligentes y cuadros de diálogo de creación.** Estos mecanismos de ayudar al usuario a la descripción de un elemento de interfaz de usuario o facilitan una tarea, como las etiquetas inteligentes o los cuadros de diálogo del generador.  
  
-   **Botones de Ayuda de la interfaz de usuario** \(en desuso\). Un indicador visible en la barra de título que proporciona acceso al tema de Ayuda de F1 relacionado.  
  
### Texto  
  
#### Texto informativo y adicional en los cuadros de diálogo  
 En los cuadros de diálogo que admiten tareas complejas, puede ser necesario para proporcionar texto informativo en la interfaz de usuario, a menudo en la parte superior del cuadro de diálogo o cerca de controles complejos. Consulte [Terminología y el texto de la interfaz de usuario](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) para obtener detalles sobre el estilo de escritura.  
  
#### Recuadros informativos  
 A menudo, el texto informativo puede ser demasiado largo para colocar en lugar de la interfaz de usuario o puede ser útil para los nuevos usuarios, se siente como confusión a los usuarios experimentados. En este caso, debe colocarse el texto informativo informativo como una información sobre herramientas en un recuadro informativo.  
  
 Recuadros informativos deben colocarse cerca de los controles que están relacionados con y que debe usar el icono de recuadro informativo específico, que aún es discreto apreciable.  
  
 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601\-d\_InfoTip")  
  
 **Ejemplo de un recuadro informativo en Visual Studio**  
  
### Mecanismos de Ayuda interactiva  
  
#### F1 Ayuda  
 Se requiere la Ayuda F1 en un editor o la superficie de diseño, pero no en otro lugar en el entorno de Visual Studio.  
  
#### Hipervínculos a temas de ayuda  
 Hipervínculos pueden utilizarse para realizar una acción, navegar en el IDE o iniciar la Ayuda en un explorador. Consulte [Terminología y el texto de la interfaz de usuario](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) para obtener más información sobre el lenguaje y 07.10.01 botones e hipervínculos para instrucciones visuales y de diseño.  
  
#### Botones de Ayuda \[?\] de barras de título del cuadro de diálogo \(en desuso\)  
 En su mayor parte, los botones de Ayuda \[?\] en la barra de título de cuadros de diálogo están en desuso. Temas de la interfaz de usuario ya no forman parte de nuestro modelo de documento y, por tanto, no puede haber un tema correspondiente para vincular a. En esencia, el botón de la barra de título se lo mismo que la Ayuda F1, y que ya no es necesaria en los cuadros de diálogo. En algunos casos, esto todavía sirve como un indicador de que hay más información conceptual o de procedimiento disponibles, aunque normalmente se usan hipervínculos en la interfaz de usuario más reciente.  
  
##### Diálogos creados a través del entorno  
 Muchos de los cuadros de diálogo de shell se crean a través de la **VBDialogBoxParam** \(función\). Esta función compartida se ha actualizado para ayudar a mover el **Ayuda** botón desde el cuadro de diálogo para el **?** botón manteniendo una arquitectura que es con versiones anteriores compatible y extensible.  
  
 En concreto, el **VBDialogBoxParam** función examina la plantilla de cuadro de diálogo para un botón cuyo identificador es **IDHELP** \(9\) o una etiqueta **Ayuda** o **& Ayuda**. Si se encuentra un botón de ayuda, está oculta y la **WS\_EX\_CONTEXTHELP** estilo se agrega al cuadro de diálogo, que coloca el **?** botón de barra de título del cuadro de diálogo.  
  
 Cuando se crea el cuadro de diálogo, inserta el procedimiento de cuadro de diálogo en una pila y se invoca el cuadro de diálogo con un procedimiento de cuadro de diálogo procesamiento previo denominado **DialogPreProc**. Cuando el **?** se hace clic en el botón, envía una **mensaje WM\_SYSCOMMAND** de **SC\_CONTEXTHELP** en el cuadro de diálogo. El **DialogPreProc** captura este comando y lo cambia a un **WM\_HELP** mensaje, que se pasa en el procedimiento de cuadro de diálogo original.  
  
 Creado por el entorno de la mayoría de los cuadros de diálogo tienen un botón de ayuda en el cuadro de diálogo. Cuando se muestre el cuadro de diálogo, el botón de ayuda está oculta automáticamente y sólo el **?** funciona el botón. Si el **?** botón nunca se quita o cambia en Windows, esta solución le permite mover rápidamente a los botones de ayuda originales.  
  
 Esta solución realiza cuatro suposiciones que podrían provocar errores:  
  
-   Botón de Ayuda del cuadro de diálogo está **IDHELP** \(9\).  
  
-   El cuadro de diálogo es correcta cuando se oculta el botón Ayuda.  
  
-   El cuadro de diálogo no sustituir su winproc.  
  
-   El cuadro de diálogo no se incrusta dentro de otro cuadro de diálogo.  
  
 Si el cuadro de diálogo se encuentra en msenv y no usa **VBDialogBoxParam**, investigar el aprovechamiento de **VBDialogBoxParam** antes de implementar su propio controlador.  
  
##### Diálogos creados a través de otros paquetes  
 Puede implementar su propia solución para cuadros de diálogo que residan fuera msenv. Para una clase de diálogo compartidos en el paquete VSPackage, considere la posibilidad de mover el botón a la barra de título o la implementación de un controlador en cada cuadro de diálogo. El código siguiente es un esqueleto de una implementación que le ayudarán a empezar a trabajar:  
  
```  
struct DLGPROCITEM { FARPROC proc; // The info used to create the dialog. DLGPROCITEM* procPrev; }; DLGPROCITEM* g_dlgProcStack = NULL; // A dialog starter/wrapper function is used to push the new // dialog proc to the top of our dialog proc stack. int SomeDialogStarterFunction(hinst, id, proc, etc) { if (g_dlgProcStack == NULL) { g_dlgProcStack = new DLGPROCITEM; g_dlgProcStack->procPrev = NULL; } else { DLGPROCITEM* procItem = new DLGPROCITEM; g_dlgProcStack->procPrev = g_dlgProcStack; g_dlgProcStack = procItem; } } // Pop this dialog proc off the dialog proc stack. DialogBoxIndirectParam...(...) { DLGPROCITEM* procItem = g_dlgProcStack->procPrev; delete g_dlgProcStack; g_dlgProcStack = procItem; } // A wrapper dialog procedure will allow us to capture the // SC_CONTEXTHELP button on the title bar from Windows and // forward it as a simple WM_HELP message back to the dialog. INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg, WPARAM wParam, LPARAM lParam) { if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP) { uMsg = WM_HELP; wParam = 0; lParam = 0; } return CallWindowProc((WNDPROC)g_dlgProcStack->proc, hwndDlg, uMsg, wParam, lParam); }  
```  
  
##### Botones de ayuda en código administrado  
 Invalidar el comportamiento predeterminado de la ventana título de la Ayuda del botón de barra es fácil en código administrado. A continuación se muestra una aplicación de demostración completo que muestra este comportamiento. En esencia, es necesario reemplazar el formulario **WndProc** método y fire, a continuación, desactivar la Ayuda de F1 cuando solicita una **SC\_CONTEXTHELP** intercepta el mensaje.  
  
```  
using System; using System.Windows.Forms; public class HelpForm : Form { private const int SC_CONTEXTHELP = 0xF180; private const int WM_SYSCOMMAND = 0x0112; public HelpForm() { this.ClientSize = new System.Drawing.Size(300, 250); this.HelpButton = true; this.MaximizeBox = false; this.MinimizeBox = false; this.Name = "HelpForm"; this.Text = "Help Form"; } protected override void WndProc(ref Message m) { if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam) ShowHelp(); else base.WndProc(ref m); } private void ShowHelp() { MessageBox.Show("F1 Help goes here."); } [STAThread] static void Main() { Application.EnableVisualStyles(); Application.EnableRTLMirroring(); Application.Run(new HelpForm()); } }  
```  
  
## Vea también  
 [Fuentes y formato de Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Las notificaciones y el progreso de Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)