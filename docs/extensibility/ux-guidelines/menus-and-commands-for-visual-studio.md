---
title: "Men&#250;s y comandos de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Men&#250;s y comandos de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Uso del comando  
  
### Información general  
 A diferencia de Microsoft Office, que es un conjunto que consta de muchos productos independientes, Visual Studio contiene muchos productos que cada contribuir sus conjuntos de comandos en el IDE de Visual Studio global. El IDE administra la complejidad de miles de comandos mediante el filtrado de la funcionalidad disponible para el usuario basado en contexto.  
  
 Si cambia el contexto de un usuario: como el cambio de una ventana de diseño a un ventana de edición de código: funcionalidad no está relacionado con el nuevo contexto desaparece. Al mismo tiempo, superficies de funcionalidad nueva junto con información dinámica relacionado, como las opciones del cuadro de herramientas y propiedades. El usuario no debería percibir el intercambio en el conjunto de comandos disponibles. Si el usuario es la distrae o le desconcierta aparezcan o desaparezcan los comandos, el diseño de interfaz de usuario necesita ajuste. Siempre se indica el contexto del usuario actual en una o varias formas, como en la barra de título IDE, la ventana Propiedades o el cuadro de diálogo páginas de propiedades.  
  
 Barras de comandos permiten flexibilidad en la interfaz de usuario. El único comando estructuras inherentes al entorno son el menú principal y la barra de comandos principales que ambos se puede personalizar e incluso oculta de Visual Studio. Otras barras de comando aparecen y desaparecen en función del estado de la aplicación. Ventanas de herramientas y editores de documento también pueden contener las barras de herramientas incrustadas dentro de sus bordes de ventana.  
  
#### Directrices básicas  
  
##### Utilice los comandos compartidos existentes, grupos de comandos y menús siempre que sea posible.  
 Dado que los comandos se muestran normalmente basado en contexto, utilizar grupos de comandos y menús compartidos existentes asegura que la estructura del comando permanece relativamente estable entre los cambios de contexto. Reutilizar comandos compartidos y la colocación de nuevos comandos cerca de comandos compartidos relacionados también reducen la complejidad IDE y crea una experiencia más fácil de usar. Si es necesario definir un nuevo comando, intente colocar en un grupo de comandos compartida existente. Si es necesario definir un nuevo grupo, coloque en un menú compartido existente cerca de un grupo de comandos relacionados antes de crear un nuevo menú de nivel superior.  
  
##### No cree iconos para cada comando.  
 Piénselo bien antes de crear un icono de comando. Se deben crear iconos para los comandos que:  
  
-   aparecen en una barra de herramientas predeterminada.  
  
-   es probable que los usuarios se agregan a una barra de herramientas a través de la **Personalizar...** cuadro de diálogo.  
  
-   tienen un icono asociado con la misma acción en otro producto de Microsoft.  
  
##### Limitar la adición de métodos abreviados de teclado  
 La mayoría de los usuarios emplean una pequeña fracción de todos los accesos directos disponibles. En caso de duda, no se enlaza la característica a un método abreviado de teclado. Trabajo con el usuario experimente equipo antes de agregar nuevos métodos abreviados.  
  
##### Proporcionar comandos en una posición de menú predeterminada.  
 Tenga en cuenta sus comandos se personalizará por otros y diseñarlas según corresponda. No hay nada como un comando oculto. Todos los comandos de Visual Studio aparecen en la **Herramientas \> personalizar** cuadro de diálogo, la ventana de comandos, Autocompletar, el **Herramientas \> Opciones \> teclado** cuadro de diálogo y el entorno de herramientas de desarrollo \(DTE\). Asegúrese de dar a los comandos de un nombre y la información sobre herramientas en el archivo .ctc para que los usuarios puedan encontrarlas fácilmente.  
  
##### No se duplican comandos compartidos en una barra de herramientas incrustada.  
 Es útil para colocar los comandos cerca del área objeto de atención del usuario. Una manera de hacerlo es crear una barra de herramientas incrustada en la parte superior de la ventana de herramientas o el documento editor. Los comandos que se coloca en la barra de herramientas deben ser específicos para el área de contenido dentro de la ventana. No se duplican comandos compartidos en estas barras de herramientas. Por ejemplo, no coloque nunca un icono de "Guardar" dentro de una barra de herramientas incrustada.  
  
### Visibilidad de comandos y contenida  
 Existen comandos en los siguientes ámbitos: **entorno**, **jerarquía**, y **documento**. Conocer cada ámbito para tener confianza en la colocación del comando.  
  
 Comandos en el **entorno** ámbito establecer contexto principal y se comparten entre varios contextos. Se modifica la visibilidad o la disposición de los documentos y ventanas de herramientas. Entre los comandos en el entorno de ámbito es **nuevo proyecto**, **Conectar con el servidor**, **el proceso de adjuntar**, **Cortar**, **copia**, **Pegar**, **Buscar**, **opciones**, **Personalizar**, **nueva ventana**, y **Ver Ayuda**.  
  
 Comandos en el **jerarquía** ámbito administrar jerarquías de Visual Studio, como **proyecto**, **equipo**, y **datos**. Se relacionan con subcontexto del proyecto: por ejemplo, **Depurar**, **Generar**, **prueba**, **arquitectura**, o **analizar**. Entre los comandos en la jerarquía de ámbito es **Agregar nuevo elemento**, **nueva consulta**, **Configuración del proyecto**, **Agregar nuevo origen de datos**, **Iniciar Asistente de rendimiento**, y **nuevo diagrama**.  
  
 Comandos en el **documento** act de ámbito en el contenido de un documento, como una consulta de elementos de trabajo \(WIQ\), diseño o código. También se actuar en la vista de una ventana de herramientas o de lo contrario, son específicos de esa ventana de herramienta. Comandos de ámbito de documento también actúan sobre los objetos de archivo que son específicas de la jerarquía, como **Quitar del proyecto**. Entre los comandos en el documento de ámbito es **Refactorizar \> cambiar el nombre de**, **Crear copia del elemento de trabajo**, **Expandir todo**, **Contraer todo**, y **Crear tarea de usuario**.  
  
### Decisiones de selección de ubicación de comando  
 Una vez que ha decidido crear un comando, debe determinar su posición adecuada y si va a crear un método abreviado de teclado. Siga esta ruta de acceso de decisión para establecer dónde colocar el comando:  
  
 ![Command placement decision chart](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501\-a\_CommandPlacement")  
  
 **Ruta de acceso de decisión de selección de ubicación de comando en Visual Studio**  
  
### Selección de ubicación de comando en menús  
  
#### Barra de menús principal  
 La barra de menús principal debe ser la ubicación estándar para los comandos de los paquetes de menú específicas del contexto que contribuyen a la interfaz de usuario. La barra de menús principal difiere de otras estructuras de comando en que el entorno utiliza para controlar qué comandos están visibles. Todas las otras barras de comando simplemente deshabilitar los comandos que están fuera de contexto, si se colocan en un menú o barra de herramientas.  
  
 El entorno define un conjunto de comandos integrada en la barra de menús principales que son comunes a todo el IDE y varios dominios de tarea. Estos comandos están siempre visibles independientemente de los cuales VSPackages se cargan en el entorno. Aunque VSPackages puede extender este conjunto de comandos, el comando de cada producto y la colocación de los comandos es responsabilidad de cada equipo.  
  
 La estructura del menú principal de Visual Studio puede dividirse en las siguientes categorías de menú:  
  
##### Menús principales  
  
-   Archivo  
  
-   Editar  
  
-   Ver  
  
-   Herramientas  
  
-   Ventana  
  
-   Ayuda  
  
##### Menús específicos del proyecto  
  
-   Proyecto  
  
-   Compilar  
  
-   Depuración  
  
##### Menús específicos del contexto  
  
-   Equipo  
  
-   Datos  
  
-   Prueba  
  
-   Arquitectura  
  
-   Analizar  
  
##### Menús específicos del documento  
  
-   Formato  
  
-   Tabla  
  
##### Al diseñar los menús principales, seguir estas reglas:  
  
-   No supere los 25 elementos de nivel superior en un contexto determinado  
  
-   Menús nunca deben superar 600 píxeles de alto.  
  
-   Evaluar un menú principal en varios contextos, como en la SKU de Ultimate y el perfil General.  
  
-   Menús desplegables son aceptables.  
  
-   Menús desplegables deben contener al menos tres elementos y no más de siete.  
  
-   Menús desplegables deben ir sólo un nivel de profundidad: algunos elementos de menú de Visual Studio tienen submenús en cascada, pero no se recomienda este patrón.  
  
-   Utilice los separadores de no más de seis. Agrupaciones deben respetar la siguiente ilustración:  
  
     ![Guidelines for main menu grouping](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501\-b\_MainMenus")  
  
-   Aunque no es necesario tener cada agrupación en la ilustración, agregar grupos adicionales está restringido.  
  
-   Cada agrupación debe tener de dos a siete elementos de menú.  
  
#### Orden del menú principal  
 Antes de agregar un nuevo elemento de nivel superior, considere la posibilidad de colocar el comando en un menú de nivel superior existente. Al agregar un nuevo menú de nivel superior, asegúrese de colocar en la ubicación correcta. Decidir si el menú es específico para el proyecto, el contexto o el documento. Que el nombre del menú de nivel superior sea conciso y utilizar sólo una palabra.  
  
 Los menús principales deben delimitador el resto de los comandos. Archivo, editar y ver siempre deben ser a la izquierda y herramientas de la ventana, y siempre debe ser la ayuda a la derecha.  
  
#### Menús contextuales  
 Colocar demasiada funcionalidad dentro de los menús contextuales da como resultado una interfaz difícil de aprender. Todas las funciones principales deben estar disponible a través de la barra de menús principal. Ubicación de los comandos deben reconciliarse con los comandos existentes para evitar comandos duplicados. Menús contextuales, el shell define los grupos de menú estándar que se deben incluidos dependiendo de si es el menú contextual para la solución, un nodo de proyecto o un elemento de proyecto.  
  
 Al diseñar los menús contextuales, cumplir las mismas reglas que para el menú principal y, además:  
  
-   No supere los 25 elementos de menú de nivel superior.  
  
-   Menús desplegables son aceptables, pero debe no superan un nivel de profundidad: nunca use menús emergentes en cascada.  
  
-   Utilice los separadores de no más de seis.  
  
### Selección de ubicación de comando en las barras de herramientas  
  
#### Barras de herramientas generales  
 Al diseñar y organizar las barras de herramientas, siga estos estándares:  
  
-   No utilice más de un verbo por cada botón. Un botón \= una acción.  
  
-   Utilizar texto junto con el icono únicamente si necesita reforzada con la etiqueta.  
  
-   Utilice un cuadro combinado exclusivamente para las propiedades que se desactivará varias veces en una sesión. De lo contrario, exponer la propiedad en otro lugar.  
  
-   El ancho de un cuadro combinado debe coincidir con el ancho del elemento más largo en el cuadro \+ 30%. Por ejemplo, si el elemento más largo es de 200 píxeles, del cuadro combinado debe ser 260 píxeles de ancho.  
  
-   Limitar el uso de separadores. El uso de un separador situado junto a una lista desplegable es un antipatrón, porque la forma de la lista desplegable propio actúa como un separador visual.  
  
-   Deben contener grupos de icono de tres a seis iconos.  
  
-   Si se producen varios comandos útiles calificadores, use un botón de división que almacena el último valor:  
  
     ![Split buttons in Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501\-c\_SplitButtons")  
  
     **Ejemplo de un botón de división. En su lugar pueden incluir los comandos de seis a la izquierda en un solo botón.**  
  
#### Barras de herramientas específicas del producto  
 Cada producto puede proporcionar una barra de herramientas predeterminada que contiene frecuente y comandos importantes y barra de herramientas de cada producto predeterminada deben aparecer la primera vez que se inicia Visual Studio después de que el producto está instalado.  
  
 Productos también deben aprovechar grupos de comandos compartida y menús proporcionados por el IDE. Cada grupo de comandos compartida se coloca en un menú compartido pretende organizar comandos relacionados de manera significativa para el usuario. Es importante aprovechar esta estructura de comando compartido con el fin de reducir la complejidad.  
  
#### Barras de herramientas globales  
 Barras de herramientas globales son necesarios para que se ajuste a la derecha de una fila de fábrica. Al crear una nueva barra de herramientas global, siga las instrucciones para ese tipo de barra de herramientas.  
  
 **Directrices generales de la barra de herramientas:**  
  
-   Cada barra de herramientas tiene 24 píxeles en controles comunes \(agarrador, desbordamiento\).  
  
-   Cada botón de barra de herramientas es 22 píxeles de ancho de espaciado. Hacer que el icono de un botón de división, agrega otro 11 píxeles de ancho.  
  
-   Se permite la duplicación de comandos en las barras de herramientas.  
  
 **Las barras de herramientas específica del documento** aparecen cuando un tipo de archivo determinado está activo y desaparecen cuando se activa un tipo de archivo diferente.  
  
-   Barras de herramientas específica del documento no pueden tener más de 12 botones.  
  
-   El ancho total de la barra de herramientas no puede tener más de 300 píxeles.  
  
-   Cada tipo de archivo puede tener una barra de herramientas incrustada o una barra de herramientas global del específica del documento, pero no ambos.  
  
 **Las barras de herramientas específicas del contexto** aparecen cuando un contexto determinado está establecido y tienden a permanecer activas durante largos períodos.  
  
-   El límite de botón para todas las barras de herramientas específicas del contexto es 18.  
  
-   Si la mayoría de los usuarios no emplean constantemente los comandos de esta barra de herramientas cuando el contexto está activo, no asociar esta barra de herramientas con un contexto.  
  
-   Asegúrese de que la barra de herramientas desaparece al salir de contexto. Ninguna de estas barras de herramientas debe aparecer en el inicio.  
  
 **Barras de herramientas con ningún contexto** nunca aparecen automáticamente. Estos muestran solo cuando el usuario activa. Conservar el ancho máximo por debajo de 200 píxeles.  
  
### Organización general y grupos definidos por el shell  
 Utilice los comandos compartidos existentes, grupos de comandos y menús. Si es necesario definir un nuevo comando, intente colocar en un grupo de comandos compartida existente. Si debe definirse un grupo nuevo, pruebe a colocar en un menú compartido existente cerca de un grupo de comandos relacionados antes de crear un nuevo menú de nivel superior. Esto reduce la complejidad de comandos durante la colocación del comando coherente en el IDE.  
  
 El recurso compartido **formato** menú, normalmente se muestra en el contexto del Diseñador de estilo de ventana de documento, se muestra en la siguiente imagen:  
  
 ![Visual Studio Format menu with callouts](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501\-d\_FormatMenu")  
  
 **Grupos de menús de Visual Studio**  
  
### Reducir y reutilización de comandos  
 Comandos normalmente aparecen basados en contexto, para reducir el número de comandos que el usuario ve en un momento dado. Sin embargo, también debe volver a usar los menús compartidos existentes y los grupos de comandos para asegurarse de que la estructura del comando permanece relativamente estable entre los cambios de contexto.  
  
 Reutilizar comandos compartidos y la colocación de nuevos comandos cerca de comandos compartidos relacionados reducen la complejidad IDE y crea una experiencia más fácil de usar.  
  
## Comandos de nomenclaturas  
  
### Convenciones de nomenclatura  
 Comando coherente de nomenclatura es fundamental para que los usuarios pueden buscar y ejecutar comandos, ya sea mediante la línea de comandos o enlace a un método abreviado de teclado. Nombres de comando ayudar al usuario a entender qué propósito sirve de un comando cuando se muestra en una barra de herramientas o en un menú contextual o en cascada.  
  
#### Nomenclatura comandos cuando:  
  
-   Construcción de texto para que sea fácilmente localizable. Para obtener más información acerca de cómo localizar texto, consulte [preparación del mundo para Visual Studio](http://msdn.microsoft.com/es-es/1cc35051-8126-441f-bea9-059245a47b1d).  
  
-   Ser conciso. Comandos deben utilizar no más de tres palabras.  
  
-   Utilice mayúsculas y minúsculas de mayúscula inicial: debe estar en mayúsculas la primera letra de cada palabra. Para obtener más información sobre el formato de texto en Visual Studio, consulte [Text style](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
-   Tenga en cuenta dónde se colocará el comando. ¿Está en un menú de nivel superior o un flotante? Por ejemplo, cuando los comandos de alineación de agrupación en una ventana flotante, el comando de nivel superior deben ser "Alinear" y los comandos de menú desplegable debe ser "Left" "Derecha", "Center", "Justify" y así sucesivamente. Sería redundante con el nombre de los comandos de menú desplegable "Alinear a la izquierda" o "Alinear derecha".  
  
     ![Visual Studio Format menu](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502\-a\_FormatMenu")  
  
### Uso de iconos con comandos  
 Se ahorra en el uso del icono de emparejamiento con comandos. Aunque asociar una imagen única a un comando apresura la capacidad del usuario para identificar dicho comando, falta de eficiencia y desorden visual se producen con el uso excesivo de la imagen. Ayuda de las reglas siguientes al decidir si desea crear un icono de comando.  
  
#### Utilice un icono con un comando sólo si:  
  
-   El mismo comando tiene un icono asociado a ella en otro producto destacado de Microsoft, como una de las aplicaciones de Microsoft Office.  
  
-   El comando se colocará en una barra de herramientas predeterminada.  
  
-   El comando es un comando de especialidad que los usuarios puedan agregar a una barra de herramientas mediante el **"Personalizar..."** cuadro de diálogo.  
  
## Teclas de acceso y de método abreviado  
  
### Información general  
 Hay dos tipos de asignaciones de teclas del teclado:  
  
-   **Las claves de acceso** \(también conocido como aceleradores\) permiten el acceso mediante teclado a través de los menús para comandos y a cada etiqueta en la interfaz de usuario del cuadro de diálogo. Teclas de acceso son principalmente con fines de accesibilidad, se asignan a todos los menús y la mayoría de los controles de cuadro de diálogo, no están diseñadas para ser memorizado, afectan sólo a la ventana actual y están localizadas.  
  
-   **Teclas de método abreviado** principalmente utilizar Control \(Ctrl\) y secuencias de teclas de función \(Fn\). Están diseñadas más para usuarios avanzados y ayuda en la productividad. Que sólo se asignan a los comandos utilizados con más frecuencia y permiten el acceso rápido al omitir el menú principal. Teclas de método abreviado están diseñados para ser memorizado y para ese motivo debe asignarse coherente con el esquema de perfil. Combinaciones de claves de acceso directo pueden variar para cada perfil. Un usuario puede personalizar teclas de método abreviado a través de **Herramientas \> Opciones \> teclado**.  
  
### Asignar teclas de acceso  
 Teclas de acceso constan de las teclas Alt más alfanuméricas. Asignar una tecla de acceso a cada elemento de menú sin excepciones. Siga las convenciones comunes para asignar teclas de acceso y Windows. Por ejemplo, la clave de acceso para **archivo \> nuevo** debe ser siempre **Alt, F, N**.  
  
 No utilice letras de ancho de píxel único como 'i' \(en mayúsculas o minúsculas\) o minúscula 'l' y evite utilizar caracteres con trazos descendentes \(g, j, p, q e y\), ya que son difíciles de distinguir.  
  
 Evite utilizar claves duplicadas cuando sea posible. En casos donde la desduplicación es inevitable, el sistema de menús controla los conflictos a través de todos los comandos que utilizan la clave. Por ejemplo, para un hipotético "Number" comando en el menú archivo, que duplica la clave de acceso "N", **Alt, F, N** crearía un nuevo archivo y **Alt, F, N, N** realizaría el comando "Número".  
  
### Asignar teclas de método abreviado  
 Evite asignar teclas de método abreviado nuevo, ya que no son necesarios para todos los comandos y el sistema \(y la memoria de usuario\) de impuestos si sobreutilizados. Datos del programa para la mejora de la experiencia del usuario \(CEIP\) indican que los usuarios de Visual Studio utilizan sólo un pequeño subconjunto de los métodos abreviados integrados.  
  
 Al definir accesos directos, siga estas reglas:  
  
-   **Usar el Control \(Ctrl\) y secuencias de teclas de función \(Fn\).**  
  
-   **Conservar los métodos abreviados utilizados con frecuencia.** Mantener los accesos directos más populares.  
  
-   **Facilitar el tipo de accesos directos del editor.** Enlazar métodos abreviados\-tipo a los comandos que los desarrolladores necesitan más al escribir código. Por ejemplo, **Edit.InvokeSmartTag** debe tener una clave de acceso directo rápido como Ctrl \+ \/ y no Alt \+ Mayús \+ F10.  
  
-   **El objetivo es métodos abreviados de forma coherente con temas.**  
  
-   **Siga las directrices de Windows para determinar qué modificador claves emplear.** Usar combinaciones de teclas Ctrl para los comandos que tienen efectos a gran escala, como los comandos que se aplican a todo el documento. Usar combinaciones de teclas de desplazamiento para los comandos que amplían o complementan las acciones de tecla de método abreviado estándar. No use combinaciones Ctrl \+ Alt.  
  
-   **Quitar accesos directos extraños.** Si tiene una función heredada, considere la posibilidad de quitar los accesos directos que se utilizan con poca extreme \(menos de 10 veces desde los datos del CEIP\) o poca moderada \(menos de 100 veces desde los datos del CEIP\) si una tecla de acceso proporciona acceso rápido al mismo comando. Por ejemplo: C Alt, H, abrirá el contenido de ayuda.  
  
 No hay una manera sencilla de comprobar la disponibilidad de acceso directo. Si desea agregar un acceso directo, siga estos pasos:  
  
1.  Compruebe la lista de [accesos directos de Visual Studio 2013](http://visualstudioshortcuts.com/2013/) para determinar si existen comandos similares a la suya con de grupo.  
  
2.  Vaya a **Herramientas \> Opciones \> entorno \> teclado** y probar el acceso directo. Compruebe cada combinación de asignación de teclado que aparecen bajo "Aplicar la siguiente combinación de asignación de teclado adicional". Comprobar los perfiles de General, C\#, VB y C\+\+, como recurso compartido de los accesos directos únicos. El acceso directo está disponible si no está asignada en cualquiera de esos sitios.