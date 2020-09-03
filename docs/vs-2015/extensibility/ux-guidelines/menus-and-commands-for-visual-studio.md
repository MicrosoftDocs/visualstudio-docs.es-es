---
title: Menús y comandos
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 681df08c02813e209738e629495190ad889caf31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202091"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menús y comandos para Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="command-usage"></a>Uso del comando

### <a name="overview"></a>Información general
 A diferencia de Microsoft Office, que es un conjunto que comprende muchos productos independientes, Visual Studio contiene muchos productos que aportan sus conjuntos de comandos al IDE global de Visual Studio. El IDE administra la complejidad de miles de comandos mediante el filtrado de la funcionalidad disponible para el usuario en función del contexto.

 Cuando el contexto de un usuario cambia, por ejemplo, al cambiar de una ventana de diseño a una ventana de edición de código, desaparece la funcionalidad no relacionada con el nuevo contexto. Al mismo tiempo, las nuevas superficies de funcionalidad junto con información dinámica relacionada, como las propiedades y las opciones del cuadro de herramientas. El usuario no debe observar el intercambio del conjunto de comandos disponible. Si el usuario se distrae o se confunde con los comandos que aparecen o desaparecen, el diseño de la interfaz de usuario debe ajustarse. El contexto actual del usuario siempre se indica de una o varias maneras, como en la barra de título del IDE, en el ventana Propiedades o en el cuadro de diálogo páginas de propiedades.

 Las barras de comandos permiten la flexibilidad en la interfaz de usuario. Las únicas estructuras de comandos inherentes al entorno de Visual Studio son el menú principal y la barra de comandos principal, que se pueden personalizar e incluso ocultar. Otras barras de comandos aparecen y desaparecen en función del estado de la aplicación. Las ventanas de herramientas y los editores de documentos también pueden contener barras de herramientas incrustadas dentro de los bordes de la ventana.

#### <a name="basic-guidelines"></a>Instrucciones básicas

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Use los comandos compartidos, los grupos de comandos y los menús existentes siempre que sea posible.
 Puesto que los comandos se muestran normalmente en función del contexto, el uso de los menús compartidos y los grupos de comandos existentes garantiza que la estructura de comandos permanece relativamente estable entre los cambios en el contexto. La reutilización de los comandos compartidos y la colocación de nuevos comandos cerca de los comandos compartidos relacionados también reduce la complejidad del IDE y crea una experiencia más fácil de usar. Si es necesario definir un nuevo comando, intente colocarlo en un grupo de comandos compartido existente. Si es necesario definir un nuevo grupo, colóquelo en un menú compartido existente cerca de un grupo de comandos relacionado antes de crear un nuevo menú de nivel superior.

##### <a name="do-not-create-icons-for-every-command"></a>No cree iconos para cada comando.
 Piénselo detenidamente antes de crear un icono de comando. Los iconos solo deben crearse para los comandos que:

- aparecen en una barra de herramientas predeterminada.

- es probable que los usuarios los agreguen a una barra de herramientas mediante la función **personalizar...** .

- tener un icono asociado a la misma acción en otro producto de Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limitar la adición de métodos abreviados de teclado
 La mayoría de los usuarios emplean una pequeña fracción de todos los métodos abreviados disponibles. En duda, no enlace la característica a un método abreviado de teclado. Trabaje con el equipo de experiencia del usuario antes de agregar nuevos accesos directos.

##### <a name="give-commands-a-default-menu-placement"></a>Dar a los comandos una posición de menú predeterminada.
 Tenga en cuenta que los comandos serán personalizados por otros y los diseñarán en consecuencia. No hay nada como un comando oculto. Todos los comandos de Visual Studio aparecen en el cuadro de diálogo **herramientas > personalizar** , en la ventana comandos, en Autocompletar, en las **herramientas > opciones >** cuadro de diálogo teclado y en el entorno de herramientas de desarrollo (DTE). Asegúrese de proporcionar un nombre y una información sobre herramientas en el archivo. CTC para que los usuarios puedan encontrarlos fácilmente.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>No duplique comandos compartidos en una barra de herramientas incrustada.
 Resulta útil colocar comandos en proximidad cerca del área del foco del usuario. Una manera de hacerlo es crear una barra de herramientas incrustada en la parte superior de la ventana de herramientas o del editor de documentos. Los comandos que se colocan en la barra de herramientas deben ser específicos de la región de contenido dentro de la ventana. No duplique los comandos compartidos en estas barras de herramientas. Por ejemplo, no coloque nunca un icono "guardar" dentro de una barra de herramientas incrustada.

### <a name="content-and-command-visibility"></a>Visibilidad de contenido y comandos
 Los comandos existen en los siguientes ámbitos: **entorno**, **jerarquía**y **documento**. Conozca cada ámbito para tener confianza en la ubicación de los comandos.

 Los comandos del ámbito del **entorno** establecen el contexto principal y se comparten entre varios contextos. Modifican la visibilidad o organización de los documentos y las ventanas de herramientas. Entre los comandos del ámbito del entorno se **encuentran nuevo proyecto**, **conectar con el servidor**, **asociar proceso**, **cortar**, **copiar**, **pegar**, **Buscar**, **Opciones**, **personalizar**, **nueva ventana**y **Ver ayuda**.

 Los comandos del ámbito de la **jerarquía** administran las jerarquías de Visual Studio, incluidos el **proyecto**, el **equipo**y los **datos**. Se relacionan con el subcontexto del proyecto, por ejemplo, **depurar**, **compilar**, **probar**, **arquitectura**o **analizar**. Entre los comandos del ámbito de la jerarquía **están agregar nuevo elemento**, **nueva consulta**, **configuración del proyecto**, **Agregar nuevo origen de datos**, iniciar el Asistente de **rendimiento**y **nuevo diagrama**.

 Los comandos del ámbito del **documento** actúan sobre el contenido de un documento, como código, diseño o una consulta de elementos de trabajo (WIQ). También actúan sobre la vista de una ventana de herramientas o son específicas de la ventana de herramientas. Los comandos de ámbito de documento también actúan sobre los objetos de archivo que son específicos de la jerarquía, como **quitar del proyecto**. Entre los comandos del ámbito del documento se incluyen **refactorizar > cambiar el nombre**, **crear una copia del elemento de trabajo**, **expandir todo**, **contraer todo**y **crear tarea de usuario**.

### <a name="command-placement-decisions"></a>Decisiones de selección de ubicación de comandos
 Una vez que haya decidido crear un comando, deberá determinar su ubicación adecuada y si desea crear un método abreviado de teclado. Siga esta ruta de acceso de decisión para establecer dónde colocar el comando:

 ![Gráfico de decisión de ubicación de comando](../../extensibility/ux-guidelines/media/0501-a-commandplacement.png "0501-a_CommandPlacement")

 **Ruta de acceso de decisión para la selección de ubicación de comandos en Visual Studio**

### <a name="command-placement-in-menus"></a>Colocación de comandos en menús

#### <a name="main-menu-bar"></a>Barra de menús principal
 La barra de menús principal debe ser la ubicación estándar para los comandos de los paquetes de menú específicos del contexto que contribuyan a la interfaz de usuario. La barra de menús principal difiere de otras estructuras de comandos en que el entorno lo usa para controlar qué comandos están visibles. Todas las demás barras de comandos simplemente deshabilitan los comandos que no están en el contexto, tanto si se colocan en un menú como en una barra de herramientas.

 El entorno define un conjunto de comandos integrados en la barra de menús principal que son comunes en todo el IDE y varios dominios de tareas. Estos comandos siempre están visibles independientemente de qué VSPackages se cargan en el entorno. Aunque los VSPackages pueden extender este conjunto de comandos, el conjunto de comandos de cada producto y la colocación de sus comandos es responsabilidad de cada equipo.

 La estructura del menú principal de Visual Studio se puede dividir en las siguientes categorías de menú:

##### <a name="core-menus"></a>Menús principales

- Archivo

- Editar

- Ver

- Herramientas

- Periodo

- Ayuda

##### <a name="project-specific-menus"></a>Menús específicos del proyecto

- Proyecto

- Build

- Depurar

##### <a name="context-specific-menus"></a>Menús específicos del contexto

- Team

- data

- Prueba

- Architecture

- Analizar

##### <a name="document-specific-menus"></a>Menús específicos del documento

- Formato

- Tabla

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Al diseñar los menús principales, siga estas reglas:

- No superar los 25 elementos de nivel superior en un contexto determinado

- Los menús nunca deben superar los 600 píxeles de alto.

- Evalúe un menú principal en varios contextos, como en la SKU Ultimate y en el perfil general.

- Los menús desplegables son aceptables.

- Los menús desplegables deben contener al menos tres elementos y no más de siete.

- Los menús contextuales solo deben tener un nivel de profundidad: algunos elementos de menú de Visual Studio tienen submenús en cascada, pero no se recomienda este patrón.

- No use más de seis separadores. Las agrupaciones deben cumplir la siguiente ilustración:

     ![Directrices para la agrupación de menú principal](../../extensibility/ux-guidelines/media/0501-b-mainmenus.png "0501-b_MainMenus")

- Aunque no es necesario tener cada agrupación en la ilustración, la adición de agrupaciones adicionales está restringida.

- Cada agrupación debe tener entre dos y siete elementos de menú.

#### <a name="main-menu-ordering"></a>Ordenación del menú principal
 Antes de agregar un nuevo elemento de nivel superior, considere la posibilidad de colocar el comando en un menú de nivel superior existente. Al agregar un nuevo menú de nivel superior, asegúrese de colocarlo en la ubicación correcta. Decida si el menú es específico del proyecto, el contexto o el documento. Mantenga el nombre del menú de nivel superior conciso y use solo una palabra.

 Los menús principales deben delimitador el resto de los comandos. Archivo, editar y ver siempre deben estar a la izquierda, y las herramientas, la ventana y la ayuda siempre deben estar a la derecha.

#### <a name="context-menus"></a>Menús contextuales
 La colocación de demasiada funcionalidad en los menús contextuales produce una interfaz difícil de aprender. Toda la funcionalidad principal debe estar disponible a través de la barra de menús principal. La colocación de los comandos se debe conciliar con los comandos existentes para evitar comandos duplicados. En el caso de los menús contextuales, el shell define los grupos de menús estándar que deben incluirse en función de si el menú contextual es para la solución, un nodo de proyecto o un elemento de proyecto.

 Al diseñar menús contextuales, siga las mismas reglas que para el menú principal y, además:

- No supere los 25 elementos de menú de nivel superior.

- Los menús desplegables son aceptables, pero no deben superar un nivel de profundidad: nunca se usan controles flotantes en cascada.

- No use más de seis separadores.

### <a name="command-placement-in-toolbars"></a>Colocación de comandos en las barras de herramientas

#### <a name="general-toolbars"></a>Barras de herramientas generales
 Al diseñar y organizar las barras de herramientas, siga estos estándares:

- No use más de un verbo por cada botón. Un botón = una acción.

- Use el texto junto con el icono solo si necesita reforzarse con la etiqueta.

- Use un cuadro combinado exclusivamente para propiedades que se cambiarán varias veces en una sesión. De lo contrario, exponga la propiedad en otro lugar.

- El ancho de un cuadro combinado debe ser igual al ancho del elemento más largo en el cuadro + 30%. Por ejemplo, si el elemento más largo es de 200 píxeles, el cuadro combinado debe ser de 260 píxeles de ancho.

- Limite el uso de separadores. El uso de un separador junto a una lista desplegable es un anti-patrón, ya que la forma de la lista desplegable actúa como separador visual.

- Los grupos de iconos deben contener de tres a seis iconos.

- Si los calificadores dan como resultado varios comandos útiles, use un botón de expansión que almacene la última configuración:

     ![Botones de división en Visual Studio](../../extensibility/ux-guidelines/media/0501-c-splitbuttons.png "0501-c_SplitButtons")

     **Ejemplo de un botón de expansión. En su lugar, los seis comandos de la izquierda pueden caber en un solo botón.**

#### <a name="product-specific-toolbars"></a>Barras de herramientas específicas del producto
 Cada producto puede proporcionar una barra de herramientas predeterminada que contiene comandos importantes y usados con frecuencia, y la barra de herramientas predeterminada de cada producto debe aparecer la primera vez que se inicia Visual Studio después de instalar el producto.

 Los productos también deben aprovechar los grupos de comandos y menús compartidos proporcionados por el IDE. Cada grupo de comandos compartido se coloca en un menú compartido diseñado para organizar los comandos relacionados de forma significativa para el usuario. Es importante aprovechar esta estructura de comandos compartida para reducir la complejidad.

#### <a name="global-toolbars"></a>Barras de herramientas globales
 Las barras de herramientas globales deben ajustarse a una fila de la derecha. Al crear una nueva barra de herramientas global, siga las instrucciones para ese tipo de barra de herramientas.

 **Instrucciones generales de la barra de herramientas:**

- Cada barra de herramientas tiene 24 píxeles en controles comunes (agarrador, desbordamiento).

- Cada botón de la barra de herramientas tiene un ancho de 22 píxeles, incluido el relleno. Al convertir el icono en un botón de expansión, se agregan otros 11 píxeles de ancho.

- Se permite la duplicación de comandos en todas las barras de herramientas.

  Las **barras de herramientas específicas del documento** aparecen cuando un determinado tipo de archivo está activo y desaparecen cuando se activa un tipo de archivo diferente.

- Es posible que las barras de herramientas específicas del documento no tengan más de 12 botones.

- El ancho total de la barra de herramientas no puede superar los 300 píxeles.

- Cada tipo de archivo puede tener una barra de herramientas incrustada o una barra de herramientas global específica del documento, pero no ambas.

  Las **barras de herramientas específicas del contexto** aparecen cuando se establece un determinado contexto y tienden a permanecer activas durante períodos prolongados.

- El límite de botones para todas las barras de herramientas específicas del contexto es 18.

- Si la mayoría de los usuarios no emplean sistemáticamente los comandos de esta barra de herramientas cuando el contexto está activo, no asocie esta barra de herramientas a un contexto.

- Asegúrese de que la barra de herramientas desaparece al salir del contexto. Ninguna de estas barras de herramientas debe aparecer en el inicio.

  Las **barras de herramientas sin contexto** nunca aparecen automáticamente. Solo se muestran cuando el usuario las activa. Mantenga el ancho máximo por debajo de 200 píxeles.

### <a name="general-organization-and-shell-defined-groups"></a>Grupos de organización y de grupo definidos por el shell generales
 Usar comandos compartidos, grupos de comandos y menús existentes. Si es necesario definir un nuevo comando, intente colocarlo en un grupo de comandos compartido existente. Si es necesario definir un nuevo grupo, intente colocarlo en un menú compartido existente cerca de un grupo de comandos relacionado antes de crear un nuevo menú de nivel superior. Esto reduce la complejidad del comando y garantiza una ubicación de comandos coherente en el IDE.

 En la imagen siguiente se muestra el menú **formato** compartido, que normalmente se muestra en el contexto de las ventanas de documento de estilo de diseñador:

 ![Menú Formato de Visual Studio con llamadas](../../extensibility/ux-guidelines/media/0501-d-formatmenu.png "0501-d_FormatMenu")

 **Grupos de menús en Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Reducir y reutilizar comandos
 Los comandos se muestran normalmente en función del contexto, con el fin de reducir el número de comandos que el usuario ve en un momento dado. Sin embargo, también debe volver a usar los menús compartidos y los grupos de comandos existentes para asegurarse de que la estructura de comandos permanece relativamente estable entre los cambios en el contexto.

 La reutilización de los comandos compartidos y la colocación de comandos nuevos cerca de los comandos compartidos relacionados reduce la complejidad del IDE y crea una experiencia más fácil de usar.

## <a name="naming-commands"></a>Asignar nombres a comandos

### <a name="naming-conventions"></a>Convenciones de nomenclatura
 La nomenclatura de comandos coherente es fundamental para que los usuarios puedan buscar y ejecutar comandos, ya sea mediante la línea de comandos o el enlace a un método abreviado de teclado. Los nombres de comando también ayudan al usuario a entender qué propósito tiene un comando cuando se muestra en una barra de herramientas o en un menú en cascada o en un menú contextual.

#### <a name="when-naming-commands"></a>Al asignar nombres a comandos:

- Construya texto para que sea fácilmente localizable. Para obtener más información sobre cómo localizar texto, consulte [procedimientos recomendados de localización](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices).

- Sea conciso. Los comandos no deben usar más de tres palabras.

- Usar mayúsculas y minúsculas en el título: la primera letra de cada palabra debe escribirse en mayúsculas. Para obtener más información sobre el formato de texto en Visual Studio, vea [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

- Tenga en cuenta dónde se colocará el comando. ¿Está en un menú de nivel superior o en un control flotante? Por ejemplo, al agrupar los comandos de alineación en un control flotante, el comando de nivel superior debe ser "align" y los comandos de control flotante deben ser "left", "Right", "Center", "Justify", etc. Sería redundante asignar un nombre a los comandos de control flotante "alinear a la izquierda" o "alinear a la derecha".

     ![Menú Formato de Visual Studio](../../extensibility/ux-guidelines/media/0502-a-formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Usar iconos con comandos
 Ser de reserva en el uso del emparejamiento de iconos con los comandos. Aunque la Asociación de una imagen única con un comando aumenta la capacidad del usuario para identificar ese comando, el desorden visual y la ineficacia se producen con un uso excesivo de la imagen. Las siguientes reglas ayudan a decidir si crear un icono de comando.

#### <a name="use-an-icon-with-a-command-only-if"></a>Use un icono con un comando solo si:

- El mismo comando tiene un icono asociado a él en otro producto destacado de Microsoft, como una de las aplicaciones Microsoft Office.

- El comando se colocará en una barra de herramientas predeterminada.

- El comando es un comando de especialidad que es probable que los usuarios agreguen a una **barra de herramientas mediante el uso** de la .

## <a name="access-and-shortcut-keys"></a>Acceso y teclas de método abreviado

### <a name="overview"></a>Información general
 Hay dos tipos de asignaciones de teclas de teclado:

- **Las claves de acceso** (también conocidas como aceleradores) permiten el acceso mediante teclado a través de los menús para comandos y a cada etiqueta en la interfaz de usuario de cuadro de diálogo. Las claves de acceso son principalmente para fines de accesibilidad, se asignan a todos los menús y la mayoría de los controles de cuadro de diálogo, no están diseñados para memorizarse, solo afectan a la ventana actual y están localizados.

- **Las teclas de método abreviado** usan principalmente secuencias de teclas de control (Ctrl) y de función (FN). Están diseñados más para usuarios avanzados y ayudan en la productividad. Solo se asignan a los comandos usados con más frecuencia y permiten el acceso rápido mientras se omite el menú principal. Las teclas de método abreviado están diseñadas para memorizarse y, por esa razón, deben asignarse de forma coherente con el esquema de perfil. Los esquemas de teclas de método abreviado pueden variar de un perfil a un perfil. Un usuario puede personalizar las teclas de método abreviado a través de **herramientas > opciones > teclado**.

### <a name="assigning-access-keys"></a>Asignación de claves de acceso
 Las claves de acceso se componen de Alt más las claves alfanuméricas. Asigne una clave de acceso a cada elemento de menú sin excepción. Siga las convenciones de Windows y comunes para asignar claves de acceso. por ejemplo, la tecla de acceso para el **archivo > New** siempre debe ser **Alt, F, N**.

 No use Letras de ancho único de píxel como ' i ' (en mayúsculas o minúsculas) o una ' l ' minúscula, y evite usar caracteres con descendentes (g, j, p, q e y), ya que son difíciles de distinguir.

 Evite el uso de claves duplicadas siempre que sea posible. En los casos en los que la duplicación es inevitable, el sistema de menús controla los conflictos mediante el recorrido de todos los comandos que usan la clave. Por ejemplo, para un comando hipotético "número" en el menú archivo que duplique la tecla de acceso "N", **Alt, F, n** crearía un archivo nuevo y **Alt, f,** n, se ejecutaría el comando "número".

### <a name="assigning-shortcut-keys"></a>Asignar teclas de método abreviado
 Evite asignar nuevas teclas de método abreviado, ya que no son necesarias para todos los comandos y los impuestos del sistema (y de la memoria de usuario) si están sobreutilizados. Los datos del Programa para la mejora de la experiencia del usuario (CEIP) indican que los usuarios de Visual Studio solo usan un pequeño subconjunto de los métodos abreviados integrados.

 Al definir accesos directos, siga estas reglas:

- **Use secuencias de teclas de control (Ctrl) y de función (FN).**

- **Conservar los métodos abreviados usados con frecuencia.** Mantenga los métodos abreviados más populares.

- **Facilite el tipo a los métodos abreviados del editor.** Enlazar accesos directos fáciles a escribir a comandos que los desarrolladores necesitan más mientras escriben código. Por ejemplo, **Edit. InvokeSmartTag** debe tener una tecla de método abreviado rápido como Ctrl +/y no Alt + Mayús + F10.

- **Procurar los accesos directos de forma coherente.**

- **Siga las directrices de Windows para determinar qué teclas modificadoras se deben emplear.** Use combinaciones de teclas Ctrl para los comandos que tienen efectos a gran escala, como los comandos que se aplican a un documento completo. Use combinaciones de teclas Mayús para los comandos que extienden o complementan las acciones de la tecla de método abreviado estándar. No use las combinaciones CTRL + ALT.

- **Quitar accesos directos extraños.** Si tiene una característica heredada, considere la posibilidad de quitar los accesos directos que se usan con una inestabilidad extrema (menos de 10 veces de los datos del CEIP) o la inestabilidad moderada (menos de 100 veces de los datos del CEIP) si una clave de acceso proporciona acceso rápido al mismo comando. Por ejemplo: Alt, H, C abrirá la ayuda y el contenido.

  No hay una manera sencilla de comprobar la disponibilidad del acceso directo. Si desea agregar un acceso directo, siga estos pasos:

1. Compruebe la lista de [métodos abreviados de Visual Studio 2013](http://visualstudioshortcuts.com/2013/) para determinar si hay comandos similares para agruparlos con.

2. Vaya a **herramientas > opciones de > entorno > teclado** y pruebe el acceso directo. Compruebe cada combinación de asignación de teclado que aparece en "aplicar la siguiente combinación de asignación de teclado adicional". Compruebe los perfiles general, C#, VB y C++, ya que comparten accesos directos únicos. El acceso directo está disponible si no está asignado en ninguno de estos lugares.
