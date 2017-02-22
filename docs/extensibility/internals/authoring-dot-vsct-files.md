---
title: "Creaci&#243;n. Archivos de Vsct | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Creación de archivos VSCT, manuales"
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Creaci&#243;n. Archivos de Vsct
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Este documento muestra cómo crear un archivo .vsct para agregar elementos de menú, barras de herramientas y otros elementos de interfaz de usuario para el entorno de desarrollo integrado \(IDE\) de Visual Studio. Siga estos pasos cuando se agregan elementos de interfaz de usuario a un paquete de Visual Studio \(VSPackage\) que aún no tiene un archivo de vsct.  
  
 Para los proyectos nuevos, se recomienda que utilice la plantilla de paquete de Visual Studio ya que genera un archivo .vsct que, dependiendo de las selecciones, ya tiene los elementos necesarios para un editor personalizado, una ventana de herramientas o un comando de menú. Puede modificar este archivo .vsct para cumplir los requisitos de su paquete VSPackage. Para obtener más información acerca de cómo modificar un archivo .vsct, vea los ejemplos en [Comandos y menús de extensión](../../extensibility/extending-menus-and-commands.md).  
  
## Creación del archivo  
 Cree un archivo de vsct en estas fases: crear la estructura de archivos y recursos, declare los elementos de interfaz de usuario, coloca los elementos de interfaz de usuario en el IDE y agregue cualquier comportamiento especializado.  
  
### Estructura de archivos  
 La estructura básica de un archivo .vsct es un [CommandTable](../../extensibility/commandtable-element.md) elemento raíz que contiene un [comandos](../../extensibility/commands-element.md) elemento y un [símbolos](../../extensibility/symbols-element.md) elemento.  
  
##### Para crear la estructura de archivos  
  
1.  Agregar un archivo .vsct al proyecto siguiendo los pasos descritos en [Cómo: crear una. Archivo de Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2.  Agregar espacios de nombres necesarios para la `CommandTable` elemento, tal como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
    	xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  En el `CommandTable` elemento, agregue un `Commands` elemento para hospedar todos los menús personalizados, barras de herramientas, grupos de comandos y comandos. Para que pueden cargar sus elementos de interfaz de usuario personalizados, el `Commands` elemento debe tener su `Package` atributo establecido en el nombre del paquete.  
  
     Después de la `Commands` elemento, agregue un `Symbols` elemento para definir los GUID para el paquete y los nombres e identificadores de comando para los elementos de interfaz de usuario.  
  
### Incluir recursos de Visual Studio  
 Utilice la [Extern](../../extensibility/extern-element.md) elemento para tener acceso a los archivos que definen los comandos de Visual Studio y los menús que se requieren para colocar los elementos de interfaz de usuario en el IDE. Si va a utilizar los comandos definidos fuera de su paquete, use el [UsedCommands](../../extensibility/usedcommands-element.md) elemento para informar a Visual Studio.  
  
##### Para incluir recursos de Visual Studio  
  
1.  En la parte superior de la `CommandTable` elemento, agregar una `Extern` \(elemento\) para cada archivo externo al que hace referencia, y establecer el `href` de atributo en el nombre del archivo. Puede hacer referencia a los siguientes archivos de encabezado para tener acceso a recursos de Visual Studio:  
  
    -   Stdidcmd.h, define los identificadores para todos los comandos expuestos por Visual Studio.  
  
    -   Vsshlids.h, contiene los identificadores de comando para los menús de Visual Studio.  
  
2.  Si el paquete llama a los comandos que se definen mediante Visual Studio o mediante otros paquetes, agregue un `UsedCommands` elemento tras el `Commands` elemento. Rellenar este elemento con un [UsedCommand](../../extensibility/usedcommand-element.md) \(elemento\) para cada comando que es llamar no forma parte del paquete. Establecer el `guid` y `id` atributos de la `UsedCommand` a los valores GUID y el ID de los comandos para llamar a los elementos. Para obtener más información acerca de cómo encontrar los comandos de GUID e identificadores de Visual Studio, consulte [GUID e identificadores de comandos de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Para llamar a comandos de otros paquetes, utilice el GUID y el identificador del comando tal como se define en el archivo .vsct para los paquetes.  
  
### Declarar elementos de interfaz de usuario  
 Declarar todos los elementos de la interfaz de usuario nueva en la `Symbols` sección del archivo vsct.  
  
##### Declarar elementos de interfaz de usuario  
  
1.  En el `Symbols` elemento, agregar tres [GuidSymbol](../../extensibility/guidsymbol-element.md) elementos. Cada `GuidSymbol` elemento tiene un `name` atributo y un `value` atributo. Establecer el `name` de atributo para que refleje el propósito del elemento. El `value` atributo toma un GUID. \(Para generar un GUID en el **herramientas** menú, haga clic en **Crear GUID**, y, a continuación, seleccione **formato del registro**.\)  
  
     La primera `GuidSymbol` elemento representa el paquete y normalmente no tiene elementos secundarios. El segundo `GuidSymbol` elemento representa el comando establece y contendrá todos los símbolos que definen los menús, grupos y comandos. La tercera `GuidSymbol` elemento representa el almacén de imágenes y contiene los símbolos para todos los iconos para los comandos. Si no dispone de ningún comando que usan iconos, puede omitir la tercera `GuidSymbol` elemento.  
  
2.  En el `GuidSymbol` elemento que representa el conjunto de comandos, agregue uno o varios [IDSymbol](../../extensibility/idsymbol-element.md) elementos. Cada una de ellas representa un menú, una barra de herramientas, un grupo o un comando que se va a agregar a la interfaz de usuario.  
  
     Para cada `IDSymbol` elemento, establezca la `name` de atributo en el nombre que se utilizará para hacer referencia al menú correspondiente, el grupo o el comando y, a continuación, establecer el `value` elemento a un número hexadecimal que representa el identificador de comando. No hay dos `IDSymbol` los elementos que tienen el mismo elemento primario pueden tener el mismo valor.  
  
3.  Si alguno de los elementos de interfaz de usuario requiere iconos, agregue un `IDSymbol` \(elemento\) para cada icono para el `GuidSymbol` elemento que representa el almacén de imágenes.  
  
### Colocar elementos de interfaz de usuario en el IDE  
 El [menús](../../extensibility/menus-element.md) elemento, [grupos](../../extensibility/groups-element.md) elemento, y [botones](../../extensibility/buttons-element.md) elemento contienen las definiciones de todos los menús, grupos y comandos que se definen en el paquete. Poner estos menús, grupos y comandos en el IDE mediante un [principal](../../extensibility/parent-element.md) elemento, que forma parte de la definición del elemento de interfaz de usuario o mediante un [CommandPlacement](../../extensibility/commandplacement-element.md) elemento que está definida en otra parte.  
  
 Cada `Menu`, `Group`, y `Button` elemento tiene un `guid` atributo y un `id` atributo. Siempre establece la `guid` atributo para que coincida con el nombre de la `GuidSymbol` establece el elemento que representa el comando y establece la `id` atributo en el nombre de la `IDSymbol` elemento que representa el menú, el grupo o el comando en el `Symbols` sección.  
  
##### Para definir elementos de interfaz de usuario  
  
1.  Si está definiendo nuevos menús, submenús, menús contextuales ni barras de herramientas, agregue un `Menus` elemento a la `Commands` elemento. A continuación, para que cada menú crear, agregue un [menú](../../extensibility/menu-element.md) elemento a la `Menus` elemento.  
  
     Establecer el `guid` y `id` atributos de la `Menu` y, a continuación, establezca el `type` atributo al tipo de menú que desee. También puede establecer el `priority` atributo para establecer la posición relativa del menú en el grupo primario.  
  
    > [!NOTE]
    >  El `priority` atributo no se aplica a las barras de herramientas y menús contextuales.  
  
2.  Todos los comandos del IDE de Visual Studio se deben hospedar en grupos de comando, que son los secundarios directos de menús y barras de herramientas. Si va a agregar nuevos menús o barras de herramientas del IDE, estos deben contener nuevos grupos de comandos. También puede agregar grupos de comandos a menús y barras de herramientas existentes para que se pueden agrupar visualmente los comandos.  
  
     Al agregar nuevos grupos de comandos, primero debe crear un `Groups` elemento y a continuación, agregarle una [grupo](../../extensibility/group-element.md) \(elemento\) para cada grupo de comandos.  
  
     Establecer el `guid` y `id` atributos de cada `Group` elemento y, a continuación, establecer el `priority` atributo para establecer la posición relativa del grupo en el menú primario. Para obtener más información, consulta [Creación de grupos reutilizables de botones](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3.  Si va a agregar nuevos comandos del IDE, agregue un `Buttons` elemento a la `Commands` elemento. A continuación, para cada comando, agregue un [botón](../../extensibility/button-element.md) elemento a la `Buttons` elemento.  
  
    1.  Establecer el `guid` y `id` atributos de cada `Button` elemento y, a continuación, establecer el `type` atributo al tipo de botón que desee. También puede establecer el `priority` atributo para establecer la posición relativa del comando en el grupo primario.  
  
        > [!NOTE]
        >  Use `type="button"` para botones de barras de herramientas y comandos de menú estándar.  
  
    2.  En el `Button` elemento, agregue un [cadenas](../../extensibility/strings-element.md) elemento que contiene un [ButtonText](../../extensibility/buttontext-element.md) elemento y un [CommandName](../../extensibility/commandname-element.md) elemento. El `ButtonText` elemento proporciona la etiqueta de texto para un elemento de menú o la información sobre herramientas para un botón de barra de herramientas. El `CommandName` elemento proporciona el nombre del comando que se usará en el comando también.  
  
    3.  Si el comando tiene un icono, crear un [icono](../../extensibility/icon-element.md) elemento en el `Button` y establezca su `guid` y `id` atributos a la `Bitmap` \(elemento\) para el icono.  
  
        > [!NOTE]
        >  Botones de barra de herramientas deben tener iconos.  
  
     Para obtener más información, consulta [MenuCommands frente a OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
4.  Si cualquiera de los comandos requieren iconos, agregue un [mapas de bits](../../extensibility/bitmaps-element.md) elemento a la `Commands` elemento. A continuación, para cada icono, agregue un [Bitmap](../../extensibility/bitmap-element.md) elemento a la `Bitmaps` elemento. Esto es donde se especifica la ubicación del recurso de mapa de bits. Para obtener más información, consulta [Agregar iconos a los comandos de menú](../../extensibility/adding-icons-to-menu-commands.md).  
  
 Puede confiar en la estructura de asociación para colocar correctamente la mayoría de los menús, grupos y comandos. Para conjuntos de comandos muy grande, o cuando un menú, el grupo o el comando debe aparecer en varios lugares, se recomienda que especifique la colocación del comando.  
  
##### Confiar en la asociación para colocar los elementos de interfaz de usuario en el IDE  
  
1.  Para la asociación típico, cree un `Parent` elemento en cada `Menu`, `Group`, y `Command` elemento que se define en el paquete.  
  
     El destino de la `Parent` elemento es el menú o el grupo que contiene el menú, el grupo o el comando.  
  
    1.  Establecer el `guid` de atributo en el nombre de la `GuidSymbol` elemento que define el conjunto de comandos. Si el elemento de destino no forma parte del paquete, use el guid para ese conjunto de comandos, tal como se define en el archivo .vsct correspondiente.  
  
    2.  Establecer el `id` atributo para que coincida con el `id` atributo del menú destino o el grupo. Para obtener una lista de los menús y los grupos que se exponen mediante Visual Studio, consulte [GUID e identificadores de menús de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o [GUID e identificadores de las barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
 Si tiene un gran número de elementos de interfaz de usuario para colocar en el IDE, o si tiene elementos que deben aparecer en varios lugares, defina sus posiciones en la [CommandPlacements](../../extensibility/commandplacements-element.md) elemento, tal como se muestra en los pasos siguientes.  
  
##### Usar selección de ubicación de comando para colocar los elementos de interfaz de usuario en el IDE  
  
1.  Después de la `Commands` elemento, agregue un `CommandPlacements` elemento.  
  
2.  En el `CommandPlacements` elemento, agregue un `CommandPlacement` \(elemento\) para cada menú, un grupo o un comando para colocar.  
  
     Cada `CommandPlacement` elemento o `Parent` elemento coloca un menú, grupo o comando en una ubicación del IDE. Un elemento de interfaz de usuario sólo puede tener un elemento primario, pero puede tener varias ubicaciones de comando. Para colocar un elemento de interfaz de usuario en varias ubicaciones, agregue un `CommandPlacement` \(elemento\) para cada ubicación.  
  
3.  Establecer el `guid` y `id` atributos de cada `CommandPlacement` elemento al menú de hospedaje o grupo, igual que haría para un `Parent` elemento. También puede establecer el `priority` atributo para establecer la posición relativa del elemento de interfaz de usuario.  
  
 Puede mezclar ubicación por relación jerárquica y colocación de comando. Sin embargo, para conjuntos de comandos muy grandes, se recomienda que utilice sólo la colocación de comando.  
  
### Adición de comportamientos especializados  
 Puede usar [CommandFlag](../../extensibility/command-flag-element.md) elementos para modificar el comportamiento de los menús y comandos, por ejemplo, para cambiar su apariencia y visibilidad. También puede afectar a si el comando es visible mediante el uso de [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md), o agregar métodos abreviados de teclado mediante [KeyBindings](../../extensibility/keybindings-element.md). Ciertos tipos de menús y comandos ya dispone de especializado comportamientos integrados.  
  
##### Para agregar comportamientos especializados  
  
1.  Para hacer que un elemento de interfaz de usuario visible sólo en determinados contextos de interfaz de usuario, por ejemplo, cuando se carga una solución, utilice las restricciones de visibilidad.  
  
    1.  Después de la `Commands` elemento, agregue un `VisibilityConstraints` elemento.  
  
    2.  Para que cada elemento de la interfaz de usuario limitar, agregue un [VisibilityItem](../../extensibility/visibilityitem-element.md) elemento.  
  
    3.  Para cada `VisibilityItem` elemento, establezca la `guid` y `id` atributos al menú, grupo, o comando y, después, establezca el `context` de atributo en el contexto de la interfaz de usuario que desee, como se define en la <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> clase. Para obtener más información, consulta [Elemento VisibilityItem](../../extensibility/visibilityitem-element.md).  
  
2.  Para establecer la visibilidad o la disponibilidad de un elemento de interfaz de usuario en el código, utilice uno o varios de los siguientes indicadores de comando:  
  
    -   DefaultDisabled  
  
    -   DefaultInvisible  
  
    -   DynamicItemStart  
  
    -   DynamicVisibility  
  
    -   NoShowOnMenuController  
  
    -   NotInTBList  
  
     Para obtener más información, consulta [Elemento de indicador de comando](../../extensibility/command-flag-element.md).  
  
3.  Para cambiar cómo aparece un elemento o cambiar su apariencia dinámicamente, utilice uno o varios de los siguientes indicadores de comando:  
  
    -   AlwaysCreate  
  
    -   CommandWellOnly  
  
    -   DefaultDocked  
  
    -   DontCache  
  
    -   DynamicItemStart  
  
    -   FixMenuController  
  
    -   IconAndText  
  
    -   PICT  
  
    -   StretchHorizontally  
  
    -   TextMenuUseButton  
  
    -   TextoCambia  
  
    -   TextOnly  
  
     Para obtener más información, consulta [Elemento de indicador de comando](../../extensibility/command-flag-element.md).  
  
4.  Para cambiar la forma en que un elemento reacciona cuando recibe comandos, utilice uno o varios de los siguientes indicadores de comando:  
  
    -   AllowParams  
  
    -   CaseSensitive  
  
    -   CommandWellOnly  
  
    -   FilterKeys  
  
    -   NoAutoComplete  
  
    -   NoButtonCustomize  
  
    -   NoKeyCustomize  
  
    -   NoToolbarClose  
  
    -   PostExec  
  
    -   RouteToDocs  
  
    -   TextIsAnchorCommand  
  
     Para obtener más información, consulta [Elemento de indicador de comando](../../extensibility/command-flag-element.md).  
  
5.  Para asociar un método abreviado dependiente de menú a un menú o un elemento en un menú, agregue un carácter de y comercial \('& '\) en el `ButtonText` elemento del menú o elemento de menú. El carácter que sigue la y comercial es el método abreviado de teclado activa cuando se abre el menú principal.  
  
6.  Para asociar un método abreviado de teclado independientes del menú a un comando, utilice [KeyBindings](../../extensibility/keybindings-element.md). Para obtener más información, consulta [Elemento KeyBinding](../../extensibility/keybinding-element.md).  
  
7.  Para localizar el texto de menú, utilice la `LocCanonicalName` elemento. Para obtener más información, consulta [Elemento de cadenas](../../extensibility/strings-element.md).  
  
 Algunos tipos de menú y el botón incluyen comportamientos especializados. La tabla siguiente describen algunos tipos de botón y un menú especializada. Para otros tipos, vea la `types` descripciones en el atributo [Elemento de menú](../../extensibility/menu-element.md), [Elemento Button](../../extensibility/button-element.md), y [Elemento de cuadro combinado](../../extensibility/combo-element.md).  
  
 Cuadro combinado  
 Un cuadro combinado es una lista desplegable que se puede usar en una barra de herramientas. Para agregar cuadros combinados a la interfaz de usuario, cree una [combinaciones](../../extensibility/combos-element.md) elemento en el `Commands` elemento. A continuación, agregue a la `Combos` elemento un `Combo` elemento para cada cuadro combinado agregar.`Combo` elementos tienen los mismos atributos y elementos secundarios como `Button` elementos y también tienen `DefaultWidth` y `idCommandList` atributos. El `DefaultWidth` atributo establece el ancho en píxeles y el `idCommandList` atributo puntos a un identificador de comando que se utiliza para rellenar el cuadro combinado. Para obtener más información, consulte el `Combo` documentación del elemento.  
  
 MenuController  
 Un controlador de menú es un botón que tiene una flecha situada junto a él. Haga clic en la flecha abre la lista. Para agregar un controlador de menú a la interfaz de usuario, cree un `Menu` y establezca su `type` atributo **MenuController** o **MenuControllerLatched**, según el comportamiento que desee. Para rellenar un controlador del menú, establecerlo como el elemento primario de un `Group` elemento. El controlador del menú mostrará a todos los elementos secundarios de ese grupo en su lista desplegable.  
  
## Vea también  
 [Comandos y menús de extensión](../../extensibility/extending-menus-and-commands.md)   
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)