---
title: Menús y comandos para Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b726d13d77c56446ff19dbb477d29ec58627341
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690635"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menús y comandos para Visual Studio
## <a name="command-usage"></a>Uso del comando

### <a name="overview"></a>Información general
 A diferencia de Microsoft Office, que es un conjunto que consta de muchos productos independientes, Visual Studio contiene muchos productos de cada uno de ellos contribuir con sus conjuntos de comandos para el IDE de Visual Studio global. El IDE administra la complejidad de miles de comandos mediante el filtrado de la funcionalidad disponible para el usuario en función del contexto.

 Cuando cambia el contexto de un usuario - como el cambio de una ventana de diseño a un ventana de edición de código: la funcionalidad no está relacionado con el nuevo contexto desaparece. Al mismo tiempo, superficies nueva funcionalidad junto con información dinámica relacionado, como las opciones del cuadro de herramientas y propiedades. El usuario no debería observar el intercambio en el conjunto de comandos disponibles. Si el usuario es distrae o le desconcierta por comandos aparezcan o desaparezcan, a continuación, el diseño de interfaz de usuario debe ajuste. Siempre se indica el contexto del usuario actual en una o más maneras, como en la barra de título IDE, la ventana Propiedades o el cuadro de diálogo páginas de propiedades.

 Barras de comandos para aportar flexibilidad en la interfaz de usuario. El único comando estructuras inherentes en el entorno están el menú principal y la barra de comandos principales que ambos se puede personalizar e incluso oculta de Visual Studio. Otras barras de comandos aparecen y desaparecen en función del estado de la aplicación. Ventanas de herramientas y editores de documentos también pueden contener barras de herramientas incrustadas dentro de los bordes de ventana.

#### <a name="basic-guidelines"></a>Directrices básicas

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Use los comandos compartidos existentes, grupos de comandos y menús siempre que sea posible.
 Puesto que los comandos se muestran normalmente basándose en contexto, el uso de menús compartidos existentes y los grupos de comandos garantiza que permanece relativamente estable entre los cambios en el contexto de la estructura del comando. Volver a utilizar los comandos compartidos y colocar nuevos comandos cerca de los comandos compartidos relacionados también reducen la complejidad IDE y crea una experiencia más fácil de usar. Si se debe definir un nuevo comando, intente colocarlo en un grupo de comandos compartida existente. Si se debe definir un nuevo grupo, colocarlo en un menú existente compartido cerca de un grupo de comandos relacionados antes de crear un nuevo menú de nivel superior.

##### <a name="do-not-create-icons-for-every-command"></a>No cree iconos para cada comando.
 Piénselo bien antes de crear un icono de comando. Iconos que se deben crear solo para los comandos que:

-   aparecen en una barra de herramientas predeterminada.

-   es probable que los usuarios puedan agregar a una barra de herramientas a través de la **personalizar...**  cuadro de diálogo.

-   tienen un icono asociado con la misma acción en otro producto de Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limitar la adición de métodos abreviados de teclado
 La mayoría de los usuarios emplean una pequeña fracción de todos los métodos abreviados disponibles. En caso de duda, no se enlaza la característica a un método abreviado de teclado. Trabajo con el usuario experimente equipo antes de agregar nuevos métodos abreviados.

##### <a name="give-commands-a-default-menu-placement"></a>Proporcionar comandos en una posición de menú predeterminada.
 Tenga en cuenta que los comandos se va a personalizar otros y diseñarlas en consecuencia. No hay nada como un comando oculto. Todos los comandos de Visual Studio aparecen en la **Herramientas > personalizar** cuadro de diálogo, la ventana de comandos, Autocompletar, la **Herramientas > Opciones > teclado** cuadro de diálogo y el entorno de herramientas de desarrollo (DTE). Asegúrese de dar a los comandos de un nombre y la información sobre herramientas en el archivo .ctc para que los usuarios encontrarlos fácilmente.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>No se duplican los comandos compartidos en una barra de herramientas incrustada.
 Es útil colocar los comandos de cerca el área de enfoque del usuario. Una manera de hacerlo es crear una barra de herramientas incrustada en la parte superior del documento o ventana de herramienta del editor. Los comandos que se coloca en la barra de herramientas deben ser específicos para el área de contenido dentro de la ventana. No se duplican los comandos compartidos en estas barras de herramientas. Por ejemplo, no coloque nunca un icono de "Guardar" dentro de una barra de herramientas incrustada.

### <a name="content-and-command-visibility"></a>Visibilidad de comandos y contenida
 Los comandos se encuentran en los siguientes ámbitos: **Entorno**, **jerarquía**, y **documento**. Conocer cada ámbito para tener confianza en la ubicación del comando.

 Los comandos de la **entorno** ámbito establecer el contexto principal y se comparten entre varios contextos. Se modifica la visibilidad o la disposición de los documentos y ventanas de herramientas. Entre los comandos en el entorno de ámbito son **nuevo proyecto**, **conectar al servidor**, **asociar proceso**, **cortar**,  **Copia**, **pegar**, **buscar**, **opciones**, **personalizar**, **nueva ventana**, y **ver Ayuda**.

 Los comandos de la **jerarquía** ámbito administrar jerarquías en Visual Studio, incluidas **proyecto**, **equipo**, y **datos**. Se relacionan con subcontexto de un proyecto: por ejemplo, **depurar**, **compilar**, **prueba**, **arquitectura**, o **analizar** . Entre los comandos en la jerarquía de ámbito son **Agregar nuevo elemento**, **nueva consulta**, **configuración del proyecto**, **Agregar nuevo origen de datos**, **Iniciar Asistente de rendimiento**, y **nuevo diagrama**.

 Los comandos de la **documento** acto de ámbito en el contenido de un documento, como código, diseño o una consulta de elemento de trabajo (WIQ). También, que actúan en la vista de una ventana de herramientas o en caso contrario, son específicas de esa ventana de herramientas. Comandos de ámbito de documento también actúan en los objetos de archivo que son específicas de la jerarquía, como **quitar del proyecto**. Entre los comandos en el documento de ámbito son **refactorizar > cambiar el nombre de**, **crear copia del elemento de trabajo**, **Expandir todo**, **Contraer todo**, y **Crear tarea de usuario**.

### <a name="command-placement-decisions"></a>Decisiones de selección de ubicación de comando
 Una vez que ha decidido crear un comando, deberá determinar su posición adecuada y si se debe crear un método abreviado de teclado. Siga esta ruta de acceso de decisión para establecer dónde colocar el comando:

 ![Gráfico de decisión de selección de ubicación de comando](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501 a_CommandPlacement")

 **Ruta de acceso de decisión de ubicación del comando en Visual Studio**

### <a name="command-placement-in-menus"></a>Ubicación del comando en los menús

#### <a name="main-menu-bar"></a>Barra de menús principal
 La barra de menús principal debe ser la ubicación estándar para los comandos de los paquetes de los menús específicos del contexto que contribuyen a la interfaz de usuario. La barra de menús principal difiere de otras estructuras de comando que el entorno usa para controlar qué comandos están visibles. Todas las otras barras de comandos simplemente deshabilitar los comandos que están fuera del contexto, si se colocan en un menú o barra de herramientas.

 El entorno define un conjunto de comandos integrada en la barra de menús principales que son comunes en todo el IDE y varios dominios de la tarea. Estos comandos siempre están visibles independientemente de que los paquetes VSPackage se cargan en el entorno. Aunque los paquetes VSPackage pueden extender este conjunto de comandos, el conjunto de cada producto y la colocación de los comandos de comandos es responsabilidad de cada equipo.

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

-   No superar los 25 elementos de nivel superior en un contexto determinado

-   Los menús nunca deben superar los 600 píxeles de alto.

-   Evaluar un menú principal en varios contextos, como en la SKU de Ultimate y el perfil General.

-   Menús desplegables son aceptables.

-   Menús desplegables deben contener al menos tres elementos y no más de siete.

-   Menús desplegables deben ir solo un nivel de profundidad: algunos elementos de menú de Visual Studio tienen submenús en cascada, pero no se recomienda establecer este patrón.

-   Utilice los separadores no más de seis. Las agrupaciones deben cumplir la siguiente ilustración:

     ![Directrices para la agrupación de menú principal](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501 b_MainMenus")

-   Aunque no es necesario tener cada agrupación en la ilustración, agregar grupos adicionales está restringido.

-   Cada agrupación debe tener entre dos y siete elementos de menú.

#### <a name="main-menu-ordering"></a>Ordenación de menú principal
 Antes de agregar un nuevo elemento de nivel superior, considere la posibilidad de colocar el comando en un menú de nivel superior existente. Al agregar un nuevo menú de nivel superior, asegúrese de colocarlo en la ubicación correcta. Decidir si el menú es específico para el proyecto, el contexto o el documento. Mantenga el nombre de menú de nivel superior concisa y usar solo una palabra.

 Los menús principales deben rodear el resto de los comandos. Archivo, edición y vista deben ser siempre a la izquierda y las herramientas, ventana, y debe ser siempre ayuda a la derecha.

#### <a name="context-menus"></a>Menús contextuales
 Colocar demasiada funcionalidad dentro de los menús contextuales da lugar a una interfaz difícil de aprender. Toda la funcionalidad principal debe estar disponible a través de la barra de menús principal. Ubicación de los comandos deben reconciliarse con los comandos existentes para evitar duplicados comandos. En los menús de contexto, el shell define los grupos de menús estándar que se deben incluidos dependiendo de si es el menú contextual para la solución, un nodo de proyecto o un elemento de proyecto.

 Al diseñar los menús contextuales, cumplir las mismas reglas que para el menú principal y además:

-   No superar los 25 elementos de menú de nivel superior.

-   Menús desplegables son aceptables, pero debe no superen un nivel de profundidad: nunca use flotantes en cascada.

-   Utilice los separadores no más de seis.

### <a name="command-placement-in-toolbars"></a>Ubicación del comando en las barras de herramientas

#### <a name="general-toolbars"></a>Barras de herramientas generales
 Al diseñar y organizar las barras de herramientas, siga estos estándares:

-   No utilice más de un verbo por cada botón. Un botón = una acción.

-   Use texto junto con el icono únicamente si necesita se verá reforzada con la etiqueta.

-   Utilice un cuadro combinado exclusivamente para las propiedades que se desactivará varias veces en una sesión. En caso contrario, se exponen la propiedad en otro lugar.

-   El ancho de un cuadro combinado debe coincidir con el ancho del elemento en el cuadro + 30% más largo. Por ejemplo, si el elemento más largo es de 200 píxeles, del cuadro combinado debe ser 260 píxeles de ancho.

-   Limite el uso de separadores. El uso de un separador situado junto a una lista desplegable es un antipatrón, porque la forma de la lista desplegable propio actúa como un separador visual.

-   Deben contener grupos de icono de tres a seis iconos.

-   Si calificadores como resultado varios comandos útiles, use un botón de expansión que almacena el último valor:

     ![Botones de división en Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501 c_SplitButtons")

     **Ejemplo de un botón de expansión. Los seis comandos a la izquierda en su lugar pueden adaptarse a un solo botón.**

#### <a name="product-specific-toolbars"></a>Barras de herramientas específica del producto
 Cada producto puede proporcionar una barra de herramientas predeterminada que contiene de uso frecuente y comandos importantes y barra de herramientas de cada producto predeterminada deben aparecer la primera vez que se inicia Visual Studio después de que el producto está instalado.

 También deben aprovechar productos de grupos de comandos compartida y los menús proporcionados por el IDE. Cada grupo de comandos compartido se coloca en un menú compartido que se quiera organizar comandos relacionados de manera significativa para el usuario. Es importante aprovechar esta estructura de comandos compartida con el fin de reducir la complejidad.

#### <a name="global-toolbars"></a>Barras de herramientas globales
 Las barras de herramientas globales son necesarios para que quepan en una fila un comienzo. Al crear una nueva barra de herramientas global, siga las instrucciones para ese tipo de barra de herramientas.

 **Directrices generales de la barra de herramientas:**

- Cada barra de herramientas tiene 24 píxeles en controles comunes (agarrador, desbordamiento).

- Cada botón de barra de herramientas es 22 píxeles de ancho incluido relleno. Hacer que el icono de un botón de expansión, agrega otro 11 píxeles de ancho.

- La duplicación de comandos a través de las barras de herramientas está permitida.

  **Las barras de herramientas específica del documento** aparecen cuando un tipo de archivo determinado está activo y desaparecen cuando se activa un tipo de archivo diferente.

- Las barras de herramientas específica del documento no pueden tener más de 12 botones.

- El ancho total de la barra de herramientas no puede tener más de 300 píxeles.

- Cada tipo de archivo puede tener una barra de herramientas incrustada o una barra de herramientas global del documento específico, pero no ambos.

  **Las barras de herramientas específicas del contexto** aparecen cuando un contexto determinado está establecido y tienden a permanecen activas durante largos períodos.

- El límite de botón para todas las barras de herramientas específicas del contexto es 18.

- Si la mayoría de los usuarios no emplea constantemente los comandos de esta barra de herramientas cuando el contexto está activo, no asociar esta barra de herramientas con un contexto.

- Asegúrese de que la barra de herramientas desaparece al salir de contexto. Ninguna de estas barras de herramientas debe aparecer al inicio.

  **Barras de herramientas con ningún contexto** nunca aparecen automáticamente. Estos muestran solo cuando el usuario las activa. Mantenga el ancho máximo por debajo de 200 píxeles.

### <a name="general-organization-and-shell-defined-groups"></a>Organización general y grupos definidos por el shell
 Use los comandos compartidos existentes, grupos de comandos y menús. Si se debe definir un nuevo comando, intente colocarlo en un grupo de comandos compartida existente. Si se debe definir un nuevo grupo, pruebe a colocarlo en un menú existente compartido cerca de un grupo de comandos relacionados antes de crear un nuevo menú de nivel superior. Esto reduce la complejidad de comando asegurándose a la ubicación del comando coherente en el IDE.

 El recurso compartido **formato** menú, normalmente se muestra en el contexto de ventanas de documento del Diseñador de estilo, se muestra en la siguiente imagen:

 ![Menú de Visual Studio formato con llamadas](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501 d_FormatMenu")

 **Grupos de menús de Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Reducir y volver a usar los comandos
 Los comandos son normalmente muestra en función de contexto, con el fin de reducir el número de comandos que el usuario ve en un momento dado. Sin embargo, también debe volver a usar los menús compartidos existentes y los grupos de comandos para asegurarse de que la estructura del comando permanece relativamente estable entre los cambios de contexto.

 Volver a utilizar los comandos compartidos y colocar nuevos comandos cerca de los comandos compartidos relacionados reducen la complejidad IDE y crea una experiencia más fácil de usar.

## <a name="naming-commands"></a>Nomenclatura de comandos

### <a name="naming-conventions"></a>Convenciones de nomenclatura
 Comando coherente de nomenclatura es fundamental para que los usuarios pueden buscar y ejecutar comandos, ya sea mediante la línea de comandos o enlazar a un método abreviado de teclado. Los nombres de comando también ayudar al usuario a entender qué finalidad un comando sirve cuando se muestre en una barra de herramientas o en un menú contextual en cascada.

#### <a name="when-naming-commands"></a>Nomenclatura de comandos cuando:

-   Construir el texto para que sea localizable fácilmente. Para obtener más información sobre cómo localizar texto, consulte [preparación del mundo para Visual Studio](http://msdn.microsoft.com/en-us/1cc35051-8126-441f-bea9-059245a47b1d).

-   Ser conciso. Los comandos deben utilizar no más de tres palabras.

-   Utilice mayúsculas y minúsculas de título: debe escribirse en mayúsculas la primera letra de cada palabra. Para obtener más información sobre el formato de texto en Visual Studio, consulte [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

-   Tenga en cuenta dónde se colocará el comando. ¿Está en un menú de nivel superior o un control flotante? Por ejemplo, cuando los comandos de alineación de agrupación en una ventana flotante, el comando de nivel superior deben ser "Alinear" y los comandos de control flotante debe ser "Left" "Derecha", "Center", "Justify" y así sucesivamente. Sería redundante para denominar los comandos de control flotante "Alinear a la izquierda" o "Right Align."

     ![Menú de Visual Studio formato](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502 a_FormatMenu")

### <a name="using-icons-with-commands"></a>Uso de iconos con comandos
 La moderación en el uso del icono de emparejamiento con comandos. Aunque la asociación de una imagen única con un comando apresura la capacidad del usuario para identificar ese comando, falta de eficiencia y desorden visual se producen con uso excesivo de la imagen. Ayudar las reglas siguientes al decidir si desea crear un icono de comando.

#### <a name="use-an-icon-with-a-command-only-if"></a>Usar un icono con un comando sólo si:

-   El mismo comando tiene un icono asociado en otro producto destacado de Microsoft, como una de las aplicaciones de Microsoft Office.

-   El comando se colocará en una barra de herramientas predeterminada.

-   El comando es un comando de especialidad que los usuarios suelen agregar a una barra de herramientas mediante el **"Personalizar..."** cuadro de diálogo.

## <a name="access-and-shortcut-keys"></a>Teclas de acceso y el acceso directo

### <a name="overview"></a>Información general
 Hay dos tipos de asignaciones de teclas del teclado:

-   **Las claves de acceso** (también conocido como aceleradores) permiten el acceso a través de los menús mediante el teclado para comandos y a cada etiqueta en la interfaz de usuario del cuadro de diálogo. Teclas de acceso son principalmente para fines de accesibilidad, se asignan a todos los menús y la mayoría de los controles de cuadro de diálogo, no están diseñadas para ser memorizar, afectan a solo la ventana actual y están localizadas.

-   **Teclas de método abreviado** principalmente, usa el Control (Ctrl) y secuencias de teclas de función (Fn). Están diseñados más para los usuarios avanzados y la Ayuda en la productividad. Que se asignan solo a los comandos usados con mayor frecuencia y permiten un acceso rápido al omitir el menú principal. Teclas de método abreviado están diseñados para ser han memorizado y para ese motivo debe asignarse coherente con el esquema de perfil. Esquemas de claves de acceso directo pueden variar para cada perfil. Un usuario puede personalizar las teclas de método abreviado a **Herramientas > Opciones > teclado**.

### <a name="assigning-access-keys"></a>Asignar teclas de acceso
 Las claves de acceso constan de teclas Alt más alfanumérico. Asignar una tecla de acceso a cada elemento de menú sin excepciones. Siga las convenciones comunes para asignar teclas de acceso y Windows. Por ejemplo, la clave de acceso para **archivo > nuevo** siempre debe **Alt, F, N**.

 No usan letras de ancho de píxel único como 'i' (en mayúsculas o minúsculas) o 'l' minúscula y evite usar caracteres con trazos descendentes (g, j, p, q e y), ya que son difíciles de distinguir.

 Evite el uso de claves duplicadas, siempre que sea posible. En casos donde la desduplicación es inevitable, el sistema de menús controla los conflictos a través de todos los comandos que usan la clave. Por ejemplo, para un hipotético "Number" comando en el menú archivo, que duplica la clave de acceso de "N", **Alt, F, N** crearía un nuevo archivo, y **Alt, F, N, N** realizaría el comando "Número".

### <a name="assigning-shortcut-keys"></a>Asignar teclas de método abreviado
 Evite asignar nuevas teclas de método abreviado, ya que no son necesarias para todos los comandos y si se sobreutiliza de impuestos del sistema (y la memoria de usuario). Datos desde el programa para la mejora de la experiencia del usuario (CEIP) indican que los usuarios de Visual Studio utilizar solo un pequeño subconjunto de los métodos abreviados integrados.

 Al definir los métodos abreviados, siga estas reglas:

- **Usar el Control (Ctrl) y secuencias de teclas de función (Fn).**

- **Conservar los métodos abreviados utilizados con frecuencia.** Mantener los métodos abreviados más populares.

- **Asegúrese de fácil de escribir métodos abreviados del editor.** Enlazar métodos abreviados de-tipo a los comandos que los desarrolladores necesitan más al escribir código. Por ejemplo, **Edit.InvokeSmartTag** debe tener una clave de acceso directo rápido como Ctrl + / y no Alt + Mayús + F10.

- **El objetivo es para los métodos abreviados de forma coherente con temas.**

- **Siga las instrucciones de Windows para determinar qué modificador teclas emplear.** Usar combinaciones de teclas Ctrl para los comandos que tienen efectos a gran escala, como los comandos que se aplican a todo el documento. Usar combinaciones de teclas de desplazamiento para los comandos que amplían o complementan las acciones de tecla de método abreviado estándar. No use combinaciones Ctrl + Alt.

- **Quitar accesos directos extraños.** Si tiene una característica heredada, considere la posibilidad de quitar los accesos directos que se utilizan con poca extreme (que tenga menos de 10 veces en los datos del CEIP) o poca moderado (que tenga menos de 100 veces desde los datos del CEIP) si una clave de acceso proporciona acceso rápido al mismo comando. Por ejemplo: C ALT, H, abrirá y contenido de la Ayuda.

  No es una manera sencilla de comprobar la disponibilidad de acceso directo. Si desea agregar un acceso directo, siga estos pasos:

1.  Compruebe la lista de [accesos directos de Visual Studio 2013](http://visualstudioshortcuts.com/2013/) para determinar si hay comandos similares para agrupar la suya con.

2.  Vaya a **Herramientas > Opciones > entorno > teclado** y probar el acceso directo. Compruebe que cada combinación de asignación de teclado aparece en "Aplicar la siguiente combinación de asignación de teclado adicionales". Comprobar los perfiles de General, C#, VB y C++, como los que compartan métodos abreviados de únicos. El acceso directo está disponible si no está asignada en cualquiera de los lugares.