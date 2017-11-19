---
title: "Menús y comandos de Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 408a496b78defbca928420f39ebdf9e9de718019
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="menus-and-commands-for-visual-studio"></a>Menús y comandos de Visual Studio
## <a name="command-usage"></a>Uso del comando  
  
### <a name="overview"></a>Información general  
 A diferencia de Microsoft Office, que es un conjunto que consta de muchos productos independientes, Visual Studio contiene muchos productos que cada uno de ellos contribuir sus conjuntos de comandos en el IDE de Visual Studio global. El IDE administra la complejidad de los miles de comandos mediante el filtrado de la funcionalidad disponible para el usuario basado en contexto.  
  
 Cuando cambia el contexto de un usuario - como el cambio de una ventana de diseño a un ventana de edición de código: funcionalidad no está relacionado con el nuevo contexto desaparece. Al mismo tiempo, superficies de funcionalidad nueva junto con información dinámica relacionado, como las opciones de propiedades y el cuadro de herramientas. El usuario no debería percibir el intercambio en el conjunto de comandos disponibles. Si el usuario es distrae o confunde con los comandos que aparecen o desaparecen, el diseño de interfaz de usuario necesario ajustar. El contexto del usuario actual siempre se indica en una o más maneras, como en la barra de título IDE, la ventana Propiedades o el cuadro de diálogo páginas de propiedades.  
  
 Barras de comandos permiten flexibilidad en la interfaz de usuario. El comando solo las estructuras inherente en el entorno son el menú principal y la barra de comandos principales que ambos se puede personalizar e incluso los ocultos de Visual Studio. Otras barras de comando aparecen y desaparecen en función del estado de la aplicación. Ventanas de herramientas y editores de documento también pueden contener las barras de herramientas incrustadas dentro de sus bordes de ventana.  
  
#### <a name="basic-guidelines"></a>Directrices básicas  
  
##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Use los comandos compartidos existentes, grupos de comandos y menús siempre que sea posible.  
 Puesto que los comandos se muestran normalmente basándose en contexto, uso de los menús compartidos existentes y grupos de comandos garantiza que la estructura del comando permanece relativamente estable entre los cambios del contexto. Volver a usar comandos compartidos y la colocación de nuevos comandos cerca de comandos compartidos relacionados también reducen la complejidad del IDE y crea una experiencia más fácil de usar. Si debe definirse un nuevo comando, pruebe a colocar en un grupo de comandos compartida existente. Si necesita definir un nuevo grupo, póngalo en un menú existente compartido cerca de un grupo de comandos relacionados antes de crear un nuevo menú de nivel superior.  
  
##### <a name="do-not-create-icons-for-every-command"></a>No se pueden crear iconos para cada comando.  
 Piénselo bien antes de crear un icono de comando. Se deben crear iconos para los comandos que:  
  
-   aparecen en una barra de herramientas predeterminada.  
  
-   es probable que va a agregar a los usuarios a una barra de herramientas a través de la **personalizar...**  cuadro de diálogo.  
  
-   tienen un icono asociado con la misma acción de otro producto de Microsoft.  
  
##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limitar la adición de métodos abreviados de teclado  
 La mayoría de los usuarios emplean una pequeña fracción de todos los métodos abreviados disponibles. En caso de duda, no se enlaza la característica a un método abreviado de teclado. Trabajo con el usuario experimente equipo antes de agregar nuevos métodos abreviados.  
  
##### <a name="give-commands-a-default-menu-placement"></a>Proporcionar comandos en una posición de menú predeterminada.  
 Tenga en cuenta que los comandos se personalizan por otros usuarios y diseñarlos en consecuencia. No hay nada que un comando oculto. Todos los comandos de Visual Studio aparecen en la **Herramientas > personalizar** cuadro de diálogo, la ventana de comandos, Autocompletar, el **Herramientas > Opciones > teclado** cuadro de diálogo y el entorno de herramientas de desarrollo (DTE). Asegúrese de que dé a los comandos de un nombre y la información sobre herramientas en el archivo .ctc para que los usuarios puedan encontrarlas fácilmente.  
  
##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>No se duplican comandos compartidos en una barra de herramientas incrustada.  
 Resulta útil para colocar comandos cerca del área objeto de atención del usuario. Una manera de hacerlo es crear una barra de herramientas incrustada en la parte superior del documento o ventana de herramientas del editor. Los comandos que se coloca en la barra de herramientas deben ser específicos para el área de contenido dentro de la ventana. No se duplican comandos compartidos en estas barras de herramientas. Por ejemplo, no coloque nunca un icono de "Guardar" dentro de una barra de herramientas incrustada.  
  
### <a name="content-and-command-visibility"></a>Visibilidad de comandos y contenida  
 Comandos existen en los siguientes ámbitos: **entorno**, **jerarquía**, y **documento**. Conocer cada ámbito para tener confianza en la ubicación del comando.  
  
 Comandos en el **entorno** ámbito establecer contexto principal y se comparten entre varios contextos. Se modifica la visibilidad o la disposición de los documentos y ventanas de herramientas. Entre los comandos en el entorno de ámbito es **nuevo proyecto**, **conectar al servidor**, **proceso de adjuntar**, **cortar**,  **Copia**, **pegar**, **buscar**, **opciones**, **personalizar**, **nueva ventana**, y **ver Ayuda**.  
  
 Comandos en el **jerarquía** ámbito administrar jerarquías en Visual Studio, incluidas **proyecto**, **equipo**, y **datos**. Se relacionan con subcontexto del proyecto: por ejemplo, **depurar**, **generar**, **prueba**, **arquitectura**, o **analizar** . Entre los comandos en la jerarquía de ámbito es **Agregar nuevo elemento**, **nueva consulta**, **configuración del proyecto**, **Agregar nuevo origen de datos**, **Iniciar Asistente de rendimiento**, y **nuevo diagrama**.  
  
 Comandos en el **documento** acto de ámbito en el contenido de un documento, como una consulta de elemento de trabajo (WIQ), diseño o código. También, que actúan en la vista de una ventana de herramientas o en caso contrario, son específicos de esa ventana de herramientas. Comandos de ámbito de documento también actúan sobre los objetos de archivo que son específicas de la jerarquía, como **quitar del proyecto**. Entre los comandos en el documento se encuentran ámbito **refactorizar > cambiar el nombre de**, **crear copia del elemento de trabajo**, **Expandir todo**, **Contraer todo**, y **Crear tarea de usuario**.  
  
### <a name="command-placement-decisions"></a>Decisiones de selección de ubicación de comando  
 Una vez que ha decidido crear un comando, debe determinar su posición adecuada y si se debe crear un método abreviado de teclado. Siga esta ruta de acceso de decisión para establecer dónde colocar el comando:  
  
 ![Gráfico de decisión de selección de ubicación de comando](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "a_CommandPlacement 0501")  
  
 **Ruta de acceso de decisión de ubicación del comando en Visual Studio**  
  
### <a name="command-placement-in-menus"></a>Ubicación del comando en los menús  
  
#### <a name="main-menu-bar"></a>Barra de menús principal  
 La barra de menús principal debe ser la ubicación estándar para los comandos de los paquetes de menú específicas del contexto que contribuyen a la interfaz de usuario. La barra de menús principal difiere de otras estructuras de comando en que el entorno utiliza para controlar qué comandos están visibles. Todas las otras barras de comando simplemente deshabilitar los comandos que están fuera del contexto, si se colocan en un menú o en una barra de herramientas.  
  
 El entorno define un conjunto de comandos integrada en la barra de menús principal que son comunes a todo el IDE y varios dominios de tarea. Estos comandos están siempre visibles independientemente de que los VSPackages se cargan en el entorno. Aunque VSPackages puede ampliar este conjunto de comandos, el conjunto de cada producto y la colocación de los comandos de comandos es la responsabilidad de cada equipo.  
  
 La estructura del menú principal de Visual Studio puede dividirse en las siguientes categorías de menú:  
  
##### <a name="core-menus"></a>Menús principales  
  
-   Archivo  
  
-   Editar  
  
-   Ver  
  
-   Herramientas  
  
-   Ventana  
  
-   Ayuda  
  
##### <a name="project-specific-menus"></a>Menús específicos del proyecto  
  
-   Proyecto  
  
-   Compilación  
  
-   Depuración  
  
##### <a name="context-specific-menus"></a>Menús específicos del contexto  
  
-   Equipo  
  
-   Datos  
  
-   Prueba  
  
-   Arquitectura  
  
-   Analizar  
  
##### <a name="document-specific-menus"></a>Menús específicos del documento  
  
-   Formato  
  
-   Tabla  
  
##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Al diseñar los menús principales, debe seguir estas reglas:  
  
-   No superen los 25 elementos de nivel superior en un contexto determinado  
  
-   Menús nunca supere 600 píxeles de alto.  
  
-   Evaluar un menú principal en varios contextos, como en la SKU de Ultimate y el perfil General.  
  
-   Menús desplegables son aceptables.  
  
-   Menús desplegables deben contener al menos tres elementos y no más de siete.  
  
-   Menús desplegables deben ir solo un nivel de profundidad: algunos elementos de menú de Visual Studio tienen submenús en cascada, pero no se recomienda este patrón.  
  
-   Utilice los separadores no más de seis. Agrupaciones deben cumplir la siguiente ilustración:  
  
     ![Directrices para la agrupación de menú principal](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "b_MainMenus 0501")  
  
-   Aunque no es necesario tener cada agrupación en la ilustración, agregar grupos adicionales está restringido.  
  
-   Cada agrupación debe tener entre dos y siete elementos de menú.  
  
#### <a name="main-menu-ordering"></a>Orden del menú principal  
 Antes de agregar un nuevo elemento de nivel superior, considere la posibilidad de colocar el comando en un menú de nivel superior existente. Al agregar un nuevo menú de nivel superior, asegúrese de colocarlo en la ubicación correcta. Decidir si el menú es específico para el proyecto, el contexto o el documento. Que el nombre del menú de nivel superior sea conciso y usar solo una palabra.  
  
 Los menús principales deben delimitador el resto de los comandos. Archivo, editar y ver siempre deben ser a la izquierda y las herramientas, ventana, y ayuda siempre debe estar a la derecha.  
  
#### <a name="context-menus"></a>Menús contextuales  
 Colocar demasiada funcionalidad dentro de los menús contextuales da como resultado una interfaz difícil de aprender. Toda la funcionalidad principal debe estar disponible a través de la barra de menús principal. Ubicación de los comandos deben reconciliarse con los comandos existentes para evitar comandos duplicados. Menús contextuales, el shell define los grupos de menús estándar que se deben incluidos dependiendo de si es el menú contextual para la solución, un nodo de proyecto o un elemento de proyecto.  
  
 Al diseñar los menús contextuales, cumplir las mismas reglas que en el menú principal y además:  
  
-   No supere los 25 elementos de menú de nivel superior.  
  
-   Menús desplegables son aceptables, pero debe no superan un nivel de profundidad; nunca utilizar menús emergentes en cascada.  
  
-   Utilice los separadores no más de seis.  
  
### <a name="command-placement-in-toolbars"></a>Ubicación del comando en las barras de herramientas  
  
#### <a name="general-toolbars"></a>Barras de herramientas generales  
 Al diseñar y organizar las barras de herramientas, siga estas normas:  
  
-   No utilice más de un verbo de cada botón. Un botón = una acción.  
  
-   Utilizar texto junto con el icono solo si necesita ser reforzados con la etiqueta.  
  
-   Utilice un cuadro combinado exclusivamente para las propiedades que se conmutará varias veces en una sesión. En caso contrario, exponer la propiedad en otro lugar.  
  
-   El ancho de un cuadro combinado debe ser igual al ancho del elemento mayor en el cuadro + 30%. Por ejemplo, si el elemento más largo es 200 píxeles, del cuadro combinado debe 260 píxeles de ancho.  
  
-   Limitar el uso de separadores. El uso de un separador junto a una lista desplegable es un antipatrón, porque la forma de la lista desplegable propio actúa como un separador visual.  
  
-   Grupos de icono deben contener entre tres y seis iconos.  
  
-   Si calificadores como resultado varios comandos útiles, use un botón de expansión que almacena el último valor:  
  
     ![Botones de división en Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "c_SplitButtons 0501")  
  
     **Ejemplo de un botón de expansión. En su lugar pueden satisfacer los seis comandos a la izquierda en un solo botón.**  
  
#### <a name="product-specific-toolbars"></a>Barras de herramientas específica del producto  
 Cada producto puede proporcionar una barra de herramientas predeterminada que contiene frecuente y comandos importantes y barra de herramientas de cada producto de forma predeterminada deben aparecer la primera vez que se inicia Visual Studio después de instala el producto.  
  
 Productos también deben aprovechar grupos de comandos compartida y menús proporcionados por el IDE. Cada grupo de comandos compartida se coloca en un menú compartido diseñado para organizar comandos relacionados de forma significativa para el usuario. Es importante aprovechar esta estructura de comando compartido con el fin de reducir la complejidad.  
  
#### <a name="global-toolbars"></a>Barras de herramientas globales  
 Barras de herramientas globales son necesarios para ajustarse a la derecha de una fila de fábrica. Al crear una nueva barra de herramientas global, siga las instrucciones para ese tipo de barra de herramientas.  
  
 **Directrices generales de la barra de herramientas:**  
  
-   Cada barra de herramientas tiene 24 píxeles en controles comunes (barra de redimensionamiento, desbordamiento).  
  
-   Cada botón de barra de herramientas es 22 píxeles de ancho de espaciado. Hacer que el icono de un botón de expansión, agrega otro 11 píxeles de ancho.  
  
-   Se permite la duplicación de comandos a través de las barras de herramientas.  
  
 **Barras de herramientas específicas del documento** aparecen cuando un determinado tipo de archivo está activo y desaparecen cuando se activa un tipo de archivo diferente.  
  
-   Barras de herramientas específicas del documento no pueden tener más de 12 botones.  
  
-   El ancho total de la barra de herramientas no puede superar los 300 píxeles.  
  
-   Cada tipo de archivo puede tener una barra de herramientas incrustada o una barra de herramientas global del documento específica, pero no ambos.  
  
 **Barras de herramientas específicas del contexto** aparecen cuando un contexto determinado está establecido y tienden a permanecer activas durante largos períodos.  
  
-   El límite de botón para todas las barras de herramientas específicas del contexto es 18.  
  
-   Si la mayoría de los usuarios no emplea constantemente los comandos de esta barra de herramientas cuando el contexto está activo, no asociar esta barra de herramientas con un contexto.  
  
-   Asegúrese de que la barra de herramientas desaparece al salir del contexto. Ninguna de estas barras de herramientas debe aparecer en el inicio.  
  
 **Barras de herramientas no tienen ningún contexto** nunca aparecen automáticamente. Aparecen solo cuando el usuario activa. Mantenga el ancho máximo por debajo de 200 píxeles.  
  
### <a name="general-organization-and-shell-defined-groups"></a>Organización general y grupos definidos por el shell  
 Use los comandos compartidos existentes, grupos de comandos y menús. Si debe definirse un nuevo comando, pruebe a colocar en un grupo de comandos compartida existente. Si debe definirse un nuevo grupo, pruebe a colocar en un menú existente compartido cerca de un grupo de comandos relacionados antes de crear un nuevo menú de nivel superior. Esto reduce la complejidad de comando asegurándose a la ubicación del comando coherente en el IDE.  
  
 El recurso compartido **formato** menú, normalmente se muestra en el contexto del Diseñador de estilo de ventana de documento, se muestra en la siguiente imagen:  
  
 ![Menú de Visual Studio formato con llamadas](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "d_FormatMenu 0501")  
  
 **Grupos de menús de Visual Studio**  
  
### <a name="reducing-and-reusing-commands"></a>Reducir y reutilización de comandos  
 Comandos normalmente aparecen basándose en contexto, con el fin de reducir el número de comandos que el usuario ve en un momento dado. Sin embargo, también debe volver a utilizar los menús compartidos existentes y los grupos de comandos para asegurarse de que la estructura del comando permanece relativamente estable entre los cambios del contexto.  
  
 Volver a usar comandos compartidos y la colocación de nuevos comandos cerca de comandos compartidos relacionados reducen la complejidad del IDE y crea una experiencia más fácil de usar.  
  
## <a name="naming-commands"></a>Comandos de nomenclaturas  
  
### <a name="naming-conventions"></a>Convenciones de nomenclatura  
 Comando coherente de nomenclatura es fundamental para que los usuarios pueden buscar y ejecutar comandos, ya sea mediante la línea de comandos o enlazar a un método abreviado de teclado. Nombres de comando ayudar al usuario a entender qué propósito un comando actúa cuando se muestre en una barra de herramientas o en un menú en cascada o contexto.  
  
#### <a name="when-naming-commands"></a>Nomenclatura comandos cuando:  
  
-   Crear texto para que resulte facilite la localización. Para obtener más información sobre cómo adaptar el texto, consulte [preparación del mundo para Visual Studio](http://msdn.microsoft.com/en-us/1cc35051-8126-441f-bea9-059245a47b1d).  
  
-   Ser conciso. Comandos deben utilizar no más de tres palabras.  
  
-   Utilice mayúsculas y minúsculas de mayúscula inicial: debe estar en mayúsculas la primera letra de cada palabra. Para obtener más información sobre el formato de texto en Visual Studio, vea [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
-   Tenga en cuenta dónde se colocará el comando. ¿Está en un menú de nivel superior o un ventana flotante? Por ejemplo, cuando los comandos de alineación de agrupación en un ventana flotante, el comando de nivel superior deben ser "Align" y los comandos de la ventana flotante debe ser "Left" "Derecha", "Center", "Justify" y así sucesivamente. Sería redundante para denominar los comandos de ventana flotante "Alinear a la izquierda" o "Alinear derecha".  
  
     ![Menú de Visual Studio formato](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "a_FormatMenu 0502")  
  
### <a name="using-icons-with-commands"></a>Uso de iconos con comandos  
 Se ahorra en el uso del icono de sincronización con comandos. Aunque asociar una imagen única con un comando apresura la capacidad del usuario para identificar ese comando, falta de eficiencia y desorden visual se producen con el uso excesivo de la imagen. Ayudar las reglas siguientes al decidir si desea crear un icono de comando.  
  
#### <a name="use-an-icon-with-a-command-only-if"></a>Utilice un icono con un comando sólo si:  
  
-   El mismo comando tiene un icono asociado a ella en otros productos de Microsoft destacado, por ejemplo, una de las aplicaciones de Microsoft Office.  
  
-   El comando se colocarán en una barra de herramientas predeterminada.  
  
-   El comando es un comando de especialidad que los usuarios pueden agregar a una barra de herramientas mediante el **"Personalizar..."** cuadro de diálogo.  
  
## <a name="access-and-shortcut-keys"></a>Teclas de acceso y el acceso directo  
  
### <a name="overview"></a>Información general  
 Hay dos tipos de asignaciones de teclas del teclado:  
  
-   **Las claves de acceso** (también conocido como aceleradores) permiten acceso a través de los menús mediante el teclado para comandos y a cada etiqueta en el cuadro de diálogo interfaz de usuario. Teclas de acceso son principalmente por motivos de accesibilidad, se asignan a todos los menús y la mayoría de los controles de cuadro de diálogo, no están diseñadas para ser memorizar, afecta a solo la ventana actual y están localizadas.  
  
-   **Teclas de método abreviado** utilizar principalmente el Control (Ctrl) y secuencias de teclas de función (Fn). Están diseñadas más para los usuarios avanzados y la Ayuda en la productividad. Que se asignan solo a los comandos usados con mayor frecuencia y permiten un acceso rápido y omitir el menú principal. Teclas de método abreviado están diseñados para ser memorizar y para ese motivo debe asignarse coherente con el esquema de perfil. Combinaciones de claves de acceso directo pueden variar para cada perfil. Un usuario puede personalizar teclas de método abreviado a través de **Herramientas > Opciones > teclado**.  
  
### <a name="assigning-access-keys"></a>Asignar teclas de acceso  
 Teclas de acceso constan de teclas Alt más alfanumérico. Asignar una tecla de acceso a cada elemento de menú sin excepciones. Siga las convenciones comunes para asignar teclas de acceso y Windows. Por ejemplo, la clave de acceso para **archivo > nuevo** siempre deben ser **Alt, F, N**.  
  
 No utilice letras de ancho de píxel de sencilla como 'i' (en mayúsculas o minúsculas) o una minúscula 'l' y evite utilizar caracteres con trazos descendentes (g, j, p, q e y), ya que son difíciles de distinguir.  
  
 Evite utilizar claves duplicadas, siempre que sea posible. En casos donde la duplicación es inevitable, el sistema de menús controla los conflictos a través de todos los comandos que utilizan la clave. Por ejemplo, para un hipotético "Número" comando en el menú archivo, que duplica la clave de acceso "N", **Alt, F, N** crearía un nuevo archivo, y **Alt, F, N, N** realizaría el comando "Número".  
  
### <a name="assigning-shortcut-keys"></a>Asignar teclas de método abreviado  
 Evite asignar teclas de método abreviado nuevo, ya que no son necesarios para todos los comandos y el sistema (y la memoria de usuario) de impuestos si sobreutilizados. Datos desde el programa para la mejora de la experiencia del usuario (CEIP) indican que los usuarios de Visual Studio usar solo un pequeño subconjunto de los métodos abreviados integrados.  
  
 Al definir métodos abreviados, siga estas reglas:  
  
-   **Utilizar el Control (Ctrl) y secuencias de teclas de función (Fn).**  
  
-   **Conservar los métodos abreviados utilizados con frecuencia.** Mantener los accesos directos más populares.  
  
-   **Facilitar el tipo de accesos directos del editor.** Enlazar métodos abreviados-tipo a comandos que los desarrolladores necesitan más al escribir código. Por ejemplo, **Edit.InvokeSmartTag** debe tener una clave de acceso directo rápido como Ctrl + / y no Alt + Mayús + F10.  
  
-   **Se esfuerzan por los métodos abreviados de forma coherente con temas.**  
  
-   **Siga las instrucciones de Windows para determinar qué modificador de claves que se emplea.** Usar combinaciones de teclas Ctrl para los comandos que tienen efectos a gran escala, como los comandos que se aplican a todo el documento. Usar combinaciones de teclas de desplazamiento para los comandos que amplían o complementan las acciones de tecla de método abreviado estándar. No use combinaciones de teclas Ctrl + Alt.  
  
-   **Quitar accesos directos a extraños.** Si tiene una característica heredada, considere la posibilidad de quitar accesos directos que se usan con poca extreme (menos de 10 horas de los datos del CEIP) o poca moderado (menos de 100 veces de los datos del CEIP) si una tecla de acceso proporciona acceso rápido al mismo comando. Por ejemplo: C Alt, H, abrirá y contenido de la Ayuda.  
  
 No hay una manera sencilla para comprobar la disponibilidad de acceso directo. Si desea agregar un acceso directo, siga estos pasos:  
  
1.  Compruebe la lista de [accesos directos de Visual Studio 2013](http://visualstudioshortcuts.com/2013/) para determinar si existen comandos similares para agrupar suyo con.  
  
2.  Vaya a **Herramientas > Opciones > entorno > teclado** y pruebe el acceso directo. Compruebe cada esquema de asignación de teclado que aparecen en "Aplicar la siguiente combinación de asignación de teclado adicionales". Comprobar los perfiles de General, C#, VB y C++, como los que compartan los métodos abreviados únicos. El acceso directo está disponible si no está asignada en cualquiera de esos sitios.