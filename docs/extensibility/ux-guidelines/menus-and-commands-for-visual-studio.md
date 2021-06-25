---
title: Menús y comandos para Visual Studio | Microsoft Docs
description: Obtenga información sobre cómo las barras de comandos permiten flexibilidad en la interfaz de usuario al crear nuevas características para Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ef66123e1a4d62f89fc1c69b81bcb780d0b294f0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902103"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menús y comandos para Visual Studio
## <a name="command-usage"></a>Uso de los comandos

### <a name="overview"></a>Información general
 A Microsoft Office, que es un conjunto que consta de muchos productos independientes, Visual Studio contiene muchos productos que cada uno aporta sus conjuntos de comandos al IDE Visual Studio global. El IDE administra la complejidad de miles de comandos filtrando la funcionalidad disponible para el usuario en función del contexto.

 Cuando cambia el contexto de un usuario (por ejemplo, al cambiar de una ventana de diseño a una ventana de edición de código), desaparece la funcionalidad no relacionada con el nuevo contexto. Al mismo tiempo, la nueva funcionalidad se muestra junto con información dinámica relacionada, como propiedades y opciones del cuadro de herramientas. El usuario no debe observar el intercambio del conjunto de comandos disponible. Si el usuario está distraido o confuso por los comandos que aparecen o desaparecen, el diseño de la interfaz de usuario necesita ajuste. El contexto actual del usuario siempre se indica de una o varias maneras, como en la barra de título del IDE, el ventana Propiedades o el cuadro de diálogo Páginas de propiedades.

 Las barras de comandos permiten flexibilidad en la interfaz de usuario. Las únicas estructuras de comandos inherentes al entorno Visual Studio son el menú principal y la barra de comandos principal, que se pueden personalizar e incluso ocultar. Otras barras de comandos aparecen y desaparecen en función del estado de la aplicación. Las ventanas de herramientas y los editores de documentos también pueden contener barras de herramientas incrustadas dentro de sus bordes de ventana.

#### <a name="basic-guidelines"></a>Directrices básicas

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Use los comandos compartidos existentes, los grupos de comandos y los menús siempre que sea posible.
 Puesto que los comandos se muestran normalmente en función del contexto, el uso de menús compartidos y grupos de comandos existentes garantiza que la estructura de comandos permanece relativamente estable entre los cambios en el contexto. Volver a usar comandos compartidos y colocar nuevos comandos cerca de comandos compartidos relacionados también reduce la complejidad del IDE y crea una experiencia más fácil de usar. Si es necesario definir un nuevo comando, intente colocarlo en un grupo de comandos compartido existente. Si es necesario definir un nuevo grupo, colódelo en un menú compartido existente cerca de un grupo de comandos relacionado antes de crear un nuevo menú de nivel superior.

##### <a name="do-not-create-icons-for-every-command"></a>No cree iconos para cada comando.
 Piense detenidamente antes de crear un icono de comando. Los iconos solo se deben crear para los comandos que:

- aparecen en una barra de herramientas predeterminada.

- es probable que los usuarios los agregan a una barra de herramientas a través del **cuadro de diálogo** Personalizar....

- tener un icono asociado a la misma acción en otro producto de Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limitar la adición de métodos abreviados de teclado
 La gran mayoría de los usuarios emplean una pequeña fracción de todos los accesos directos disponibles. Cuando esté en duda, no enlace la característica a un método abreviado de teclado. Trabaje con el equipo de experiencia del usuario antes de agregar nuevos accesos directos.

##### <a name="give-commands-a-default-menu-placement"></a>Dé a los comandos una ubicación de menú predeterminada.
 Tenga en cuenta que otros usuarios personalizarán los comandos y los diseñarán en consecuencia. No hay nada como un comando oculto. Todos Visual Studio comandos aparecen en el cuadro de diálogo Herramientas **>** Personalizar, la ventana Comandos, autocompletar, el cuadro de diálogo Herramientas **> Opciones >** teclado y el Entorno de herramientas de desarrollo (DTE). Asegúrese de dar a los comandos un nombre e información sobre herramientas en el archivo .ctc para que los usuarios puedan encontrarlos fácilmente.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>No duplique comandos compartidos en una barra de herramientas incrustada.
 Resulta útil colocar comandos cerca del área del foco del usuario. Una manera de hacerlo es crear una barra de herramientas incrustada en la parte superior de la ventana de herramientas o del editor de documentos. Los comandos colocados en la barra de herramientas deben ser específicos de la región de contenido dentro de la ventana. No duplique los comandos compartidos en estas barras de herramientas. Por ejemplo, nunca coloque un icono "Guardar" en una barra de herramientas incrustada.

### <a name="content-and-command-visibility"></a>Visibilidad del contenido y los comandos
 Los comandos existen en los ámbitos siguientes: **Entorno,** **Jerarquía** y **Documento.** Conozca cada ámbito para tener confianza en la selección de ubicación de comandos.

 Los comandos del ámbito **entorno** establecen el contexto principal y se comparten entre varios contextos. Modifican la visibilidad o la organización de documentos y ventanas de herramientas. Entre los comandos del ámbito del entorno se encuentran New **Project**, **Connect to Server**, Attach **Process**, **Cut**, **Copy**, **Paste**, **Find**, **Options**, **Customize**, **New Window** y View **Help**.

 Los comandos del ámbito **Hierarchy** administran jerarquías en Visual Studio, **incluidos Project**, **Team** y **Data**. Se relacionan con el subcontexto de un proyecto, por ejemplo, **Depurar,** **Compilar,** **Probar,** **Arquitectura** o **Analizar.** Entre los comandos del ámbito Hierarchy se encuentran **Add New Item**, New **Query**, **Project Settings**, Add New Data **Source**, Launch **Performance Wizard** y New **Diagram**.

 Los comandos del ámbito **documento** actúan sobre el contenido de un documento, como código, diseño o una consulta de elemento de trabajo (WIQ). También actúan en la vista de una ventana de herramientas o son específicos de esa ventana de herramientas. Los comandos de ámbito de documento también actúan en los objetos de archivo que son específicos de la jerarquía, como **Quitar del proyecto**. Entre los comandos del ámbito del documento se encuentran **Refactorizar > Cambiar** **nombre,** Crear copia del elemento de trabajo, **Expandir** todo, **Contraer todo** y Crear tarea **de usuario**.

### <a name="command-placement-decisions"></a>Decisiones de selección de ubicación de comandos
 Una vez que haya decidido crear un comando, deberá determinar su ubicación adecuada y si debe crear un método abreviado de teclado. Siga esta ruta de decisión para establecer dónde colocar el comando:

 ![Gráfico de decisión de ubicación de comando](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Ruta de acceso de decisión para la selección de ubicación de comandos Visual Studio**

### <a name="command-placement-in-menus"></a>Selección de ubicación de comandos en los menús

#### <a name="main-menu-bar"></a>Barra de menús principal
 La barra de menús principal debe ser la ubicación estándar para los comandos de cualquier paquete de menú específico del contexto que contribuya a la interfaz de usuario. La barra de menús principal difiere de otras estructuras de comandos en que el entorno la usa para controlar qué comandos están visibles. Todas las demás barras de comandos simplemente deshabilitan los comandos que están fuera de contexto, tanto si se colocan en un menú como en una barra de herramientas.

 El entorno define un conjunto de comandos integrados en la barra de menús principal que son comunes en todo el IDE y en varios dominios de tarea. Estos comandos siempre son visibles independientemente de qué VSPackages se cargan en el entorno. Aunque los VSPackages pueden ampliar este conjunto de comandos, el conjunto de comandos de cada producto y la colocación de sus comandos es responsabilidad de cada equipo.

 La estructura del menú Visual Studio principal se puede dividir en las siguientes categorías de menú:

##### <a name="core-menus"></a>Menús principales

- Archivo

- Editar

- Ver

- Herramientas

- Periodo

- Ayuda

##### <a name="project-specific-menus"></a>Menús específicos del proyecto

- Project

- Build

- Depurar

##### <a name="context-specific-menus"></a>Menús específicos del contexto

- Team

- Datos

- Test

- Architecture

- Análisis

##### <a name="document-specific-menus"></a>Menús específicos del documento

- Formato

- Tabla

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Al diseñar los menús principales, cumpla estas reglas:

- No superar los 25 elementos de nivel superior en un contexto determinado

- Los menús nunca deben superar los 600 píxeles de alto.

- Evalúe un menú principal en varios contextos, como en la SKU Ultimate y el perfil general.

- Los menús de salida son aceptables.

- Los menús de salida deben contener al menos tres elementos y no más de siete.

- Los menús del menú desplegable solo deben tener un nivel de profundidad: algunos Visual Studio de menú tienen submenús en cascada, pero no se recomienda este patrón.

- No use más de seis separadores. Las agrupaciones deben cumplir la siguiente ilustración:

     ![Directrices para la agrupación de menú principal](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

- Aunque no es necesario tener cada agrupación en la ilustración, la adición de agrupaciones adicionales está restringida.

- Cada agrupación debe tener de dos a siete elementos de menú.

#### <a name="main-menu-ordering"></a>Ordenación del menú principal
 Antes de agregar un nuevo elemento de nivel superior, considere la posibilidad de colocar el comando en un menú de nivel superior existente. Al agregar un nuevo menú de nivel superior, asegúrese de colocarlo en la ubicación correcta. Decida si el menú es específico del proyecto, contexto o documento. Mantenga el nombre del menú de nivel superior conciso y use solo una palabra.

 Los menús principales deben reservar el resto de los comandos. Archivo, Edición y Vista siempre deben estar a la izquierda, y Herramientas, Ventana y Ayuda siempre deben estar a la derecha.

#### <a name="context-menus"></a>Menús contextuales
 La colocación de demasiada funcionalidad en los menús contextuales da como resultado una interfaz difícil de aprender. Toda la funcionalidad principal debe estar disponible a través de la barra de menús principal. La colocación de comandos debe conciliarse con los comandos existentes para evitar comandos duplicados. En el caso de los menús contextuales, el shell define grupos de menús estándar que deben incluirse en función de si el menú contextual es para la solución, un nodo de proyecto o un elemento de proyecto.

 Al diseñar menús contextuales, cumpla las mismas reglas que para el menú principal y, además:

- No supere los 25 elementos de menú de nivel superior.

- Los menús de menús desplegables son aceptables, pero no deben superar un nivel de profundidad; nunca se usan los elementos emergentes en cascada.

- No use más de seis separadores.

### <a name="command-placement-in-toolbars"></a>Colocación de comandos en las barras de herramientas

#### <a name="general-toolbars"></a>Barras de herramientas generales
 Al diseñar y organizar barras de herramientas, siga estos estándares:

- No use más de un verbo por botón. Un botón = una acción.

- Use texto junto con el icono solo si es necesario reforzarlo con la etiqueta .

- Use un cuadro combinado exclusivamente para las propiedades que se cambiarán varias veces en una sesión. De lo contrario, exponga la propiedad en otro lugar.

- El ancho de un cuadro combinado debe ser igual al ancho del elemento más largo dentro del cuadro + 30 %. Por ejemplo, si el elemento más largo es de 200 píxeles, el cuadro combinado debe tener 260 píxeles de ancho.

- Limitar el uso de separadores. El uso de un separador junto a una lista desplegable es un anti pattern, ya que la forma de la lista desplegable actúa como separador visual.

- Los grupos de iconos deben contener de tres a seis iconos.

- Si los calificadores tienen como resultado varios comandos útiles, use un botón de división que almacena la última configuración:

     ![Botones de división en Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Ejemplo de un botón de división. En su lugar, los seis comandos de la izquierda pueden caber en un solo botón.**

#### <a name="product-specific-toolbars"></a>Barras de herramientas específicas del producto
 Cada producto puede proporcionar una barra de herramientas predeterminada que contiene comandos importantes y usados con frecuencia, y la barra de herramientas predeterminada de cada producto debe aparecer la primera vez que Visual Studio se inicia después de instalar el producto.

 Los productos también deben aprovechar los menús y grupos de comandos compartidos proporcionados por el IDE. Cada grupo de comandos compartidos se coloca en un menú compartido diseñado para organizar comandos relacionados de una manera significativa para el usuario. Es importante aprovechar esta estructura de comandos compartidos para reducir la complejidad.

#### <a name="global-toolbars"></a>Barras de herramientas globales
 Las barras de herramientas globales deben caber en una fila directamente desde el primer momento. Al crear una nueva barra de herramientas global, siga las instrucciones para ese tipo de barra de herramientas.

 **Directrices generales de la barra de herramientas:**

- Cada barra de herramientas tiene 24 píxeles en controles comunes (control, desbordamiento).

- Cada botón de la barra de herramientas tiene 22 píxeles de ancho, incluido el relleno. Al convertir el icono en un botón de división, se agregan otros 11 píxeles de ancho.

- Se permite la duplicación de comandos en las barras de herramientas.

  **Las barras de herramientas específicas del documento** aparecen cuando un determinado tipo de archivo está activo y desaparece cuando se activa otro tipo de archivo.

- Es posible que las barras de herramientas específicas del documento no tengan más de 12 botones.

- El ancho total de la barra de herramientas no puede superar los 300 píxeles.

- Cada tipo de archivo puede tener una barra de herramientas incrustada o una barra de herramientas global específica del documento, pero no ambas.

  **Las barras de herramientas específicas del contexto** aparecen cuando se establece un contexto determinado y tienden a permanecer activas durante períodos prolongados.

- El límite de botón para todas las barras de herramientas específicas del contexto es 18.

- Si la mayoría de los usuarios no emplean de forma coherente los comandos de esta barra de herramientas cuando el contexto está activo, no asocie esta barra de herramientas a un contexto.

- Asegúrese de que la barra de herramientas desaparece al salir del contexto. Ninguna de estas barras de herramientas debe aparecer en el inicio.

  **Las barras de herramientas sin contexto** nunca aparecen automáticamente. Solo se muestran cuando el usuario los activa. Mantenga el ancho máximo por debajo de 200 píxeles.

### <a name="general-organization-and-shell-defined-groups"></a>Organización general y grupos definidos por shell
 Use comandos compartidos existentes, grupos de comandos y menús. Si es necesario definir un nuevo comando, intente colocarlo en un grupo de comandos compartido existente. Si es necesario definir un nuevo grupo, intente colocarlo en un menú compartido existente cerca de un grupo de comandos relacionado antes de crear un nuevo menú de nivel superior. Esto reduce la complejidad de los comandos a la vez que garantiza la colocación coherente de los comandos en el IDE.

 El menú **Formato** compartido, que normalmente se muestra en el contexto de las ventanas de documento de estilo diseñador, se muestra en la siguiente imagen:

 ![Menú Formato de Visual Studio con llamadas](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Grupos de menús en Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Reducción y reuso de comandos
 Los comandos se muestran normalmente en función del contexto, con el fin de reducir el número de comandos que el usuario ve en un momento dado. Sin embargo, también debe reutilizar los menús compartidos y los grupos de comandos existentes para asegurarse de que la estructura de comandos permanece relativamente estable entre los cambios en el contexto.

 Volver a usar comandos compartidos y colocar nuevos comandos cerca de comandos compartidos relacionados reduce la complejidad del IDE y crea una experiencia más fácil de usar.

## <a name="naming-commands"></a>Comandos de nomenclatura

### <a name="naming-conventions"></a>Convenciones de nomenclatura
 La nomenclatura de comandos coherente es fundamental para que los usuarios puedan buscar y ejecutar comandos, ya sea mediante la línea de comandos o el enlace a un método abreviado de teclado. Los nombres de comando también ayudan al usuario a comprender qué propósito sirve un comando cuando se muestra en una barra de herramientas o en un menú contextual o en cascada.

#### <a name="when-naming-commands"></a>Al asignar nombres a comandos:

- Construya texto para que sea fácilmente localizable. Para obtener más información sobre la localización de texto, vea [Procedimientos recomendados de localización.](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices)

- Sea conciso. Los comandos no deben usar más de tres palabras.

- Use mayúsculas y minúsculas de título: la primera letra de cada palabra debe estar en mayúsculas. Para obtener más información sobre el formato de texto en Visual Studio, vea [Estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

- Tenga en cuenta dónde se colocará el comando. ¿Está en un menú de nivel superior o en un menú desplegable? Por ejemplo, al agrupar los comandos de alineación en un control flyout, el comando de nivel superior debe ser "Align" y los comandos de control lateral deben ser "Left", "Right", "Center", "Justify", y así sucesivamente. Sería redundante nombrar los comandos de control lateral "Alinear a la izquierda" o "Alinear a la derecha".

     ![Menú Formato de Visual Studio](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Uso de iconos con comandos
 Esté moderando el uso del emparejamiento de iconos con comandos. Aunque la asociación de una imagen única a un comando acelerará la capacidad del usuario para identificar ese comando, el desorden visual y la ineficacia se producen con el uso excesivo de la imagen. Las reglas siguientes ayudan a decidir si se va a crear un icono de comando.

#### <a name="use-an-icon-with-a-command-only-if"></a>Use un icono con un comando solo si:

- El mismo comando tiene un icono asociado en otro producto destacado de Microsoft, como una de las Microsoft Office aplicaciones.

- El comando se colocará en una barra de herramientas predeterminada.

- El comando es un comando especializado que es probable que los usuarios agreguen a una barra de herramientas mediante el **cuadro de diálogo "Personalizar...".**

## <a name="access-and-shortcut-keys"></a>Teclas de acceso y acceso directo

### <a name="overview"></a>Información general
 Hay dos tipos de asignaciones de teclas de teclado:

- **Las teclas de** acceso (también conocidas como aceleradores) permiten el acceso mediante teclado a través de los menús para comandos y a cada etiqueta en la interfaz de usuario del cuadro de diálogo. Las claves de acceso se asignan principalmente con fines de accesibilidad, se asignan a todos los menús y a la mayoría de los controles de cuadro de diálogo, no están pensadas para ser memoriadas, afectan solo a la ventana actual y se localizan.

- **Las teclas de** método abreviado usan principalmente secuencias de teclas Control (Ctrl) y Función (Fn). Están diseñados más para usuarios avanzados y ayudan en la productividad. Solo se asignan a los comandos usados con más frecuencia y permiten el acceso rápido mientras se omite el menú principal. Las teclas de método abreviado están diseñadas para que se memorizan y, por ese motivo, se deben asignar coherentes con el esquema de perfil. Los esquemas de teclas de método abreviado pueden variar de un perfil a otro. Un usuario puede personalizar las teclas de método abreviado a través de **Herramientas > opciones > Teclado**.

### <a name="assigning-access-keys"></a>Asignación de claves de acceso
 Las claves de acceso constan de alt más claves alfanuméricas. Asigne una clave de acceso a cada elemento de menú sin excepción. Siga las convenciones comunes y de Windows para asignar claves de acceso. Por ejemplo, la clave de acceso para **File > New** siempre debe ser **Alt, F, N**.

 No use letras de un solo píxel, como "i" (en mayúsculas o minúsculas) o una "l" minúscula, y evite usar caracteres con descendientes (g, j, p, q e y), ya que son difíciles de distinguir.

 Evite usar claves duplicadas cuando sea posible. En los casos en los que la duplicación es inevitable, el sistema de menús controla los conflictos mediante el redoble de todos los comandos que usan la clave. Por ejemplo, para un comando hipotético "Number" en el menú Archivo que duplica la clave de acceso "N", **Alt, F, N** crearía un nuevo archivo y **Alt, F, N, N** realizaría el comando "Number".

### <a name="assigning-shortcut-keys"></a>Asignación de teclas de método abreviado
 Evite asignar nuevas teclas de método abreviado, ya que no son necesarias para cada comando e imposición del sistema (y la memoria del usuario) si se usan en exceso. Los datos del Programa para la mejora de la experiencia del usuario (CEIP) indican que los Visual Studio usan solo un pequeño subconjunto de los accesos directos integrados.

 Al definir accesos directos, siga estas reglas:

- **Use secuencias de teclas Control (Ctrl) y Función (Fn).**

- **Conservar los accesos directos usados con frecuencia.** Mantenga los accesos directos más populares.

- **Facilita la tarea de escribir los accesos directos del editor.** Enlace accesos directos fáciles de escribir a los comandos que los desarrolladores necesitan más al escribir código. Por ejemplo, **Edit.InvokeSmartTag** debe tener una tecla de método abreviado rápida como Ctrl+/ y no Alt+Mayús+F10.

- **Esfuérzse por obtener accesos directos con un formato coherente.**

- **Siga las instrucciones de Windows para determinar qué teclas modificadoras emplear.** Use las combinaciones de teclas Ctrl para los comandos que tienen efectos a gran escala, como los comandos que se aplican a todo un documento. Use combinaciones de teclas Mayús para los comandos que amplían o complementan las acciones de la tecla de método abreviado estándar. No use combinaciones Ctrl+Alt.

- **Quite los accesos directos extraneosos.** Si tiene una característica heredada, considere la posibilidad de quitar los accesos directos que se usan con una poca frecuencia extrema (menos de 10 veces desde los datos del CEIP) o una poca frecuencia moderada (menos de 100 veces de los datos del CEIP) si una clave de acceso proporciona acceso rápido al mismo comando. Por ejemplo: Alt, H y C abrirán Ayuda/Contenido.

  No hay una manera sencilla de comprobar la disponibilidad de accesos directos. Si desea agregar un acceso directo, siga estos pasos:

1. Compruebe la lista de [Visual Studio 2013 accesos directos](http://visualstudioshortcuts.com/2013/) para determinar si hay comandos similares con los que agrupar los de .

2. Vaya a **Herramientas > opciones > entorno > teclado y** pruebe el acceso directo. Compruebe cada esquema de asignación de teclado que aparece en "Aplicar el siguiente esquema de asignación de teclado adicional". Compruebe los perfiles General, C#, VB y C++, ya que comparten accesos directos únicos. El acceso directo está disponible si no está asignado en ninguno de esos lugares.
