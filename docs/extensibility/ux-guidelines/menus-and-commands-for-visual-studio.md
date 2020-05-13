---
title: Menús y comandos para Visual Studio ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1f22b7ac4377b600208c079b6af1eff7fc3cbfc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698382"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menús y comandos para Visual Studio
## <a name="command-usage"></a>Uso de comandos

### <a name="overview"></a>Información general
 A diferencia de Microsoft Office, que es un conjunto que comprende muchos productos independientes, Visual Studio contiene muchos productos que cada uno aporta sus conjuntos de comandos al IDE global de Visual Studio. El IDE administra la complejidad de miles de comandos filtrando la funcionalidad disponible para el usuario en función del contexto.

 Cuando cambia el contexto de un usuario, como cambiar de una ventana de diseño a una ventana de edición de código, desaparece la funcionalidad no relacionada con el nuevo contexto. Al mismo tiempo, la nueva funcionalidad aparece junto con la información dinámica relacionada, como las opciones Propiedades y Cuadro de herramientas. El usuario no debe notar el intercambio del conjunto de comandos disponible. Si el usuario está distraído o confundido por los comandos que aparecen o desaparecen, el diseño de la interfaz de usuario necesita un ajuste. El contexto actual del usuario siempre se indica de una o varias maneras, como en la barra de título del IDE, la ventana Propiedades o el cuadro de diálogo Páginas de propiedades.

 Las barras de comandos permiten flexibilidad en la interfaz de usuario. Las únicas estructuras de comandos inherentes al entorno de Visual Studio son el menú principal y la barra de comandos principal, que se pueden personalizar e incluso ocultar. Otras barras de comandos aparecen y desaparecen en función del estado de la aplicación. Las ventanas de herramientas y los editores de documentos también pueden contener barras de herramientas incrustadas dentro de sus bordes de ventana.

#### <a name="basic-guidelines"></a>Directrices básicas

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Utilice comandos compartidos, grupos de comandos y menús existentes siempre que sea posible.
 Puesto que los comandos se muestran normalmente en función del contexto, el uso de los menús compartidos existentes y los grupos de comandos garantiza que la estructura de comandos permanezca relativamente estable entre los cambios en el contexto. Reutilizar comandos compartidos y colocar nuevos comandos cerca de comandos compartidos relacionados también reduce la complejidad del IDE y crea una experiencia más fácil de usar. Si es necesario definir un nuevo comando, intente colocarlo en un grupo de comandos compartido existente. Si es necesario definir un nuevo grupo, colóquelo en un menú compartido existente cerca de un grupo de comandos relacionado antes de crear un nuevo menú de nivel superior.

##### <a name="do-not-create-icons-for-every-command"></a>No cree iconos para cada comando.
 Piense detenidamente antes de crear un icono de comando. Los iconos se deben crear solamente para los comandos que:

- aparecen en una barra de herramientas predeterminada.

- es probable que los usuarios agreguen a una barra de herramientas a través del cuadro de diálogo **Personalizar...**

- tienen un icono asociado a la misma acción en otro producto de Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limitar la adición de atajos de teclado
 La gran mayoría de los usuarios emplean una pequeña fracción de todos los accesos directos disponibles. En caso de duda, no vincule la función a un método abreviado de teclado. Trabaje con su equipo de experiencia de usuario antes de agregar nuevos accesos directos.

##### <a name="give-commands-a-default-menu-placement"></a>Proporcione a los comandos una ubicación de menú predeterminada.
 Tenga en cuenta que sus comandos serán personalizados por otros y diseñarlos en consecuencia. No existe tal cosa como un comando oculto. Todos los comandos de Visual Studio aparecen en el cuadro de diálogo **Herramientas > personalizar,** la ventana de comandos, autocompletar, el cuadro de diálogo **Herramientas > opciones > teclado** y el entorno de herramientas de desarrollo (DTE). Asegúrese de asignar a sus comandos un nombre y información sobre herramientas en el archivo .ctc para que los usuarios puedan encontrarlos fácilmente.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>No duplique comandos compartidos en una barra de herramientas incrustada.
 Es útil colocar comandos cerca del área del foco del usuario. Una forma de hacerlo es crear una barra de herramientas incrustada en la parte superior de la ventana de herramientas o el editor de documentos. Los comandos colocados en la barra de herramientas deben ser específicos de la región de contenido dentro de la ventana. No duplique los comandos compartidos en estas barras de herramientas. Por ejemplo, nunca coloque un icono "Guardar" dentro de una barra de herramientas incrustada.

### <a name="content-and-command-visibility"></a>Visibilidad de contenido y comandos
 Los comandos existen en los ámbitos siguientes: **Entorno**, **Jerarquía**y **Documento**. Conozca cada ámbito para tener confianza en la colocación del comando.

 Los comandos del ámbito **Entorno** establecen el contexto principal y se comparten entre varios contextos. Modifican la visibilidad o disposición de documentos y ventanas de herramientas. Entre los comandos del ámbito de entorno se encuentran **Nuevo proyecto**, **Conectar al servidor**, Adjuntar **proceso**, **Cortar**, **Copiar**, **Pegar**, **Buscar**, **Opciones**, **Personalizar**, **Nueva ventana**y Ver **ayuda**.

 Los comandos del ámbito **Jerarquía** administran jerarquías en Visual Studio, incluidos **Proyecto**, **Equipo**y **Datos**. Se relacionan con el subcontexto de un proyecto, por ejemplo, **Depurar**, **Compilar**, **Probar**, **Arquitectura**o **Analizar**. Entre los comandos del ámbito Jerarquía se encuentran **Agregar nuevo elemento**, Nueva **consulta**, Configuración del **proyecto**, Agregar nuevo origen de **datos**, Iniciar asistente de **rendimiento**y **Nuevo diagrama**.

 Los comandos del ámbito **Documento** actúan sobre el contenido de un documento, como código, diseño o una consulta de elemento de trabajo (WIQ). También actúan en la vista de una ventana de herramientas o son específicos de esa ventana de herramientas. Los comandos de ámbito de documento también actúan en los objetos de archivo que son específicos de la jerarquía, como **Quitar del proyecto.** Entre los comandos del ámbito del documento se encuentran **Refactorizar > cambiar nombre**, **Crear copia del elemento de trabajo**, **Expandir todo**, **Contraer todo**y Crear tarea de **usuario**.

### <a name="command-placement-decisions"></a>Decisiones de colocación de comandos
 Una vez que haya decidido crear un comando, tendrá que determinar su ubicación adecuada y si desea crear un método abreviado de teclado. Siga esta ruta de decisión para establecer dónde colocar el comando:

 ![Gráfico de decisión de ubicación de comando](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Ruta de decisión para la colocación de comandos en Visual Studio**

### <a name="command-placement-in-menus"></a>Colocación de comandos en los menús

#### <a name="main-menu-bar"></a>Barra de menú principal
 La barra de menúprincipal debe ser la ubicación estándar para los comandos de cualquier paquete de menú específico del contexto que contribuya a la interfaz de usuario. La barra de menús principal difiere de otras estructuras de comandos en que el entorno la utiliza para controlar qué comandos son visibles. Todas las demás barras de comandos simplemente deshabilitan los comandos que están fuera de contexto, ya sea que se coloquen en un menú o en una barra de herramientas.

 El entorno define un conjunto de comandos integrados en la barra de menús principal que son comunes en todo el IDE y varios dominios de tareas. Estos comandos siempre están visibles independientemente de qué VSPackages se cargan en el entorno. Aunque VSPackages puede extender este conjunto de comandos, el conjunto de comandos de cada producto y la colocación de sus comandos es responsabilidad de cada equipo.

 La estructura del menú principal de Visual Studio se puede desglosar en las siguientes categorías de menú:

##### <a name="core-menus"></a>Menús principales

- Archivo

- Editar

- Ver

- Herramientas

- Periodo

- Ayuda

##### <a name="project-specific-menus"></a>Menús específicos del proyecto

- proyecto

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

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Al diseñar menús principales, siga estas reglas:

- No exceda los 25 elementos de nivel superior en un contexto determinado

- Los menús nunca deben superar los 600 píxeles de altura.

- Evalúe un menú principal en varios contextos, como en la SKU definitiva y el perfil general.

- Los menús desplegables son aceptables.

- Los menús desplegables deben contener al menos tres elementos y no más de siete.

- Los menús desplegables deben ir solo un nivel de profundidad: algunos elementos de menú de Visual Studio tienen submenús en cascada, pero no se recomienda este patrón.

- No utilice más de seis separadores. Las agrupaciones deben adherirse a la siguiente ilustración:

     ![Directrices para la agrupación de menú principal](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

- Aunque no es necesario tener cada agrupación en la figura, la adición de agrupaciones adicionales está restringida.

- Cada agrupación debe tener de dos a siete elementos de menú.

#### <a name="main-menu-ordering"></a>Ordenación del menú principal
 Antes de agregar un nuevo elemento de nivel superior, considere la posibilidad de colocar el comando en un menú de nivel superior existente. Al agregar un nuevo menú de nivel superior, asegúrese de colocarlo en la ubicación correcta. Decida si el menú es específico del proyecto, el contexto o el documento. Mantenga el nombre del menú de nivel superior conciso y utilice una sola palabra.

 Los menús principales deben reservar el resto de los comandos. Archivo, Editar y Ver siempre deben estar a la izquierda, y Herramientas, Ventana y Ayuda siempre deben estar a la derecha.

#### <a name="context-menus"></a>Menús contextuales
 Colocar demasiada funcionalidad dentro de los menús contextuales da como resultado una interfaz difícil de aprender. Todas las funciones principales deben estar disponibles a través de la barra de menú principal. La colocación de comandos debe conciliarse con los comandos existentes para evitar comandos duplicados. Para los menús contextuales, el shell define los grupos de menús estándar que se deben incluir en función de si el menú contextual es para la solución, un nodo de proyecto o un elemento de proyecto.

 Al diseñar menús contextuales, siga las mismas reglas que para el menú principal y, además:

- No exceda los 25 elementos de menú de nivel superior.

- Los menús desplegables son aceptables, pero no deben superar un nivel de profundidad - nunca utilice flyouts en cascada.

- No utilice más de seis separadores.

### <a name="command-placement-in-toolbars"></a>Colocación de comandos en las barras de herramientas

#### <a name="general-toolbars"></a>Barras de herramientas generales
 Al diseñar y organizar barras de herramientas, siga estos estándares:

- No uses más de un verbo por botón. Un botón: una acción.

- Utilice texto junto al icono solo si necesita reforzarse con la etiqueta.

- Utilice un cuadro combinado exclusivamente para las propiedades que se cambiarán varias veces en una sesión. De lo contrario, exponga la propiedad en otro lugar.

- El ancho de un cuadro combinado debe ser igual al ancho del elemento más largo dentro del cuadro + 30%. Por ejemplo, si el elemento más largo es de 200 píxeles, el cuadro combinado debe tener 260 píxeles de ancho.

- Limite el uso de separadores. El uso de un separador junto a una lista desplegable es un antipatrón, porque la forma de la lista desplegable actúa como un separador visual.

- Los grupos de iconos deben contener de tres a seis iconos.

- Si los calificadores dan como resultado varios comandos útiles, utilice un botón de división que almacene la última configuración:

     ![Botones de división en Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Ejemplo de un botón de división. Los seis comandos de la izquierda pueden caber en un solo botón.**

#### <a name="product-specific-toolbars"></a>Barras de herramientas específicas del producto
 Cada producto puede proporcionar una barra de herramientas predeterminada que contiene comandos importantes y de uso frecuente, y la barra de herramientas predeterminada de cada producto debe aparecer la primera vez que visual Studio se inicia después de instalar el producto.

 Los productos también deben aprovechar los menús y grupos de comandos compartidos proporcionados por el IDE. Cada grupo de comandos compartidose se coloca en un menú compartido destinado a organizar los comandos relacionados de una manera significativa para el usuario. Es importante aprovechar esta estructura de comandos compartidos para reducir la complejidad.

#### <a name="global-toolbars"></a>Barras de herramientas globales
 Las barras de herramientas globales deben caber en una fila de inmediato. Al crear una nueva barra de herramientas global, siga las directrices para ese tipo de barra de herramientas.

 **Directrices generales de la barra de herramientas:**

- Cada barra de herramientas tiene 24 píxeles en controles comunes (agarrador, desbordamiento).

- Cada botón de la barra de herramientas tiene 22 píxeles de ancho, incluido el relleno. Hacer que el icono sea un botón de división añade otros 11 píxeles de ancho.

- Se permite la duplicación de comandos en las barras de herramientas.

  **Las barras de herramientas específicas** del documento aparecen cuando un determinado tipo de archivo está activo y desaparecen cuando se activa un tipo de archivo diferente.

- Es posible que las barras de herramientas específicas del documento no tengan más de 12 botones.

- El ancho total de la barra de herramientas no puede superar los 300 píxeles.

- Cada tipo de archivo puede tener una barra de herramientas incrustada o una barra de herramientas global específica del documento, pero no ambas.

  **Las barras de herramientas específicas** del contexto aparecen cuando se establece un contexto determinado y tienden a permanecer activas durante períodos prolongados.

- El límite de botones para todas las barras de herramientas específicas del contexto es 18.

- Si la mayoría de los usuarios no emplean constantemente los comandos de esta barra de herramientas cuando el contexto está activo, no asocie esta barra de herramientas con un contexto.

- Asegúrese de que la barra de herramientas desaparece al salir del contexto. Ninguna de estas barras de herramientas debe aparecer al inicio.

  **Las barras de herramientas sin contexto** nunca aparecen automáticamente. Estos se muestran solamente cuando el usuario los activa. Mantenga el ancho máximo por debajo de 200 píxeles.

### <a name="general-organization-and-shell-defined-groups"></a>Organización general y grupos definidos por shell
 Utilice comandos compartidos, grupos de comandos y menús existentes. Si es necesario definir un nuevo comando, intente colocarlo en un grupo de comandos compartido existente. Si es necesario definir un nuevo grupo, intente colocarlo en un menú compartido existente cerca de un grupo de comandos relacionado antes de crear un nuevo menú de nivel superior. Esto reduce la complejidad de los comandos al tiempo que garantiza la colocación coherente de los comandos en el IDE.

 El menú **Formato** compartido, que normalmente se muestra en el contexto de las ventanas de documento de estilo diseñador, se ilustra en la siguiente imagen:

 ![Menú Formato de Visual Studio con llamadas](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Grupos de menús en Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Reducción y reutilización de comandos
 Los comandos se muestran típicamente basados en el contexto, para reducir el número de comandos que el usuario ve en un momento dado. Sin embargo, también debe reutilizar los menús compartidos existentes y los grupos de comandos para asegurarse de que la estructura de comandos permanece relativamente estable entre los cambios en el contexto.

 Reutilizar comandos compartidos y colocar nuevos comandos cerca de comandos compartidos relacionados reduce la complejidad del IDE y crea una experiencia más fácil de usar.

## <a name="naming-commands"></a>Comandos de nomenclatura

### <a name="naming-conventions"></a>Convenciones de nomenclatura
 La nomenclatura de comandos coherente es fundamental para que los usuarios puedan buscar y ejecutar comandos, ya sea mediante la línea de comandos o enlazando a un método abreviado de teclado. Los nombres de comando también ayudan al usuario a comprender qué propósito sirve un comando cuando se muestra en una barra de herramientas o en un menú contextual o en cascada.

#### <a name="when-naming-commands"></a>Al asignar nombres a los comandos:

- Construya texto para que sea fácilmente localizable. Para obtener más información sobre la localización de texto, consulte [Prácticas recomendadas](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices)de localización .

- Sé conciso. Los comandos no deben usar más de tres palabras.

- Usar mayúsculas y minúsculas de título: la primera letra de cada palabra debe estar en mayúsculas. Para obtener más información sobre el formato de texto en Visual Studio, vea [Estilo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)de texto .

- Tenga en cuenta dónde se colocará el comando. ¿Está en un menú de nivel superior o en un control flotante? Por ejemplo, al agrupar comandos de alineación en un control flotante, el comando de nivel superior debe ser "Alinear" y los comandos desplegables deben ser "Izquierda", "Derecha", "Centro", "Justificar", etc. Sería redundante nombrar los comandos desplegables "Alinear a la izquierda" o "Alinear a la derecha."

     ![Menú Formato de Visual Studio](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Uso de iconos con comandos
 Estar ahorrando en el uso de emparejamiento de iconos con comandos. Aunque asociar una imagen única con un comando acelera la capacidad del usuario para identificar ese comando, el desorden visual y la ineficiencia se producen con el uso excesivo de la imagen. Las siguientes reglas ayudan a decidir si se debe crear un icono de comando.

#### <a name="use-an-icon-with-a-command-only-if"></a>Utilice un icono con un comando solo si:

- El mismo comando tiene un icono asociado en otro producto de Microsoft prominente, como una de las aplicaciones de Microsoft Office.

- El comando se colocará en una barra de herramientas predeterminada.

- El comando es un comando de especialidad que es probable que los usuarios agreguen a una barra de herramientas mediante el cuadro de diálogo **"Personalizar...".**

## <a name="access-and-shortcut-keys"></a>Teclas de acceso y acceso directo

### <a name="overview"></a>Información general
 Hay dos tipos de asignaciones de teclas de teclado:

- **Las teclas** de acceso (también conocidas como aceleradores) permiten el acceso del teclado a través de los menús para los comandos y a cada etiqueta en la interfaz de usuario del cuadro de diálogo. Las teclas de acceso son principalmente para fines de accesibilidad, se asignan a todos los menús y la mayoría de los controles de cuadro de diálogo, no están diseñadas para memorizarse, afectan solo a la ventana actual y están localizadas.

- **Las teclas** de método abreviado utilizan principalmente secuencias de teclas Control (Ctrl) y Función (Fn). Están diseñados más para usuarios avanzados y ayudan en la productividad. Se asignan sólo a los comandos más utilizados y permiten un acceso rápido mientras se omite el menú principal. Las teclas de método abreviado están diseñadas para memorizarse y, por ese motivo, deben asignarse de forma coherente con el esquema de perfil. Los esquemas de teclas de acceso directo pueden variar de un perfil a un perfil. Un usuario puede personalizar las teclas de método abreviado a través de **Herramientas > Opciones > teclado**.

### <a name="assigning-access-keys"></a>Asignación de claves de acceso
 Las claves de acceso constan de Alt más claves alfanuméricas. Asigne una clave de acceso a cada elemento de menú sin excepción. Siga Windows y las convenciones comunes para asignar claves de acceso. por ejemplo, la clave de acceso para **file > New** siempre debe ser **Alt, F, N**.

 No utilice letras de un solo píxel de ancho como 'i' (en mayúsculas o minúsculas) o una 'l' minúscula, y evite usar caracteres con descendientes (g, j, p, q e y) ya que son difíciles de distinguir.

 Evite el uso de claves duplicadas cuando sea posible. En los casos en los que la duplicación es inevitable, el sistema de menús controla los conflictos recorriendo todos los comandos que utilizan la clave. Por ejemplo, para un comando hipotético "Número" en el menú Archivo que duplica la tecla de acceso "N", **Alt, F, N** crearía un nuevo archivo, y **Alt, F, N, N** realizaría el comando "Número".

### <a name="assigning-shortcut-keys"></a>Asignación de teclas de método abreviado
 Evite asignar nuevas teclas de método abreviado, ya que no son necesarias para cada comando e impuestos del sistema (y la memoria del usuario) si se utilizan en exceso. Los datos del Programa de mejora de la experiencia del usuario (CEIP) indican que los usuarios de Visual Studio solo usan un pequeño subconjunto de los accesos directos integrados.

 Al definir accesos directos, siga estas reglas:

- **Utilice las secuencias de teclas Control (Ctrl) y Función (Fn).**

- **Conservar accesos directos utilizados con frecuencia.** Mantenga los accesos directos más populares.

- **Haga que los accesos directos del editor sean fáciles de escribir.** Enlazar accesos directos fáciles de escribir a comandos que los desarrolladores necesitan más al escribir código. Por ejemplo, **Edit.InvokeSmartTag** debe tener una tecla de método abreviado rápido como Ctrl+/ y no Alt+Mayús+F10.

- **Esfuérzate por obtener accesos directos con temas consistentes.**

- **Siga las directrices de Windows para determinar qué claves modificadoras emplear.** Utilice las combinaciones de teclas Ctrl para los comandos que tienen efectos a gran escala, como los comandos que se aplican a todo un documento. Utilice las combinaciones de teclas Mayús para los comandos que amplían o complementan las acciones de la tecla de método abreviado estándar. No utilice las combinaciones Ctrl+Alt.

- **Eliminar accesos directos extraños.** Si usted tiene una característica heredada, considere quitar los accesos directos que se utilizan con la infrecuencia extrema (menos de 10 veces de los datos CEIP) o la infrecuencia moderada (menos de 100 veces de los datos CEIP) si una clave de acceso proporciona el acceso rápido al mismo comando. Por ejemplo: Alt, H, C abrirá Ayuda/Contenido.

  No hay una manera sencilla de comprobar la disponibilidad de accesos directos. Si desea agregar un acceso directo, siga estos pasos:

1. Compruebe la lista de [accesos directos de Visual Studio 2013](http://visualstudioshortcuts.com/2013/) para determinar si hay comandos similares con los que agrupar el suyo.

2. Vaya a **Herramientas > Opciones > Entorno > teclado** y pruebe el acceso directo. Compruebe cada esquema de asignación de teclado que aparece en "Aplicar el siguiente esquema de asignación de teclado adicional." Marque los perfiles General, C, VB y C++, ya que comparten accesos directos únicos. El acceso directo está disponible si no está asignado en ninguno de esos lugares.
