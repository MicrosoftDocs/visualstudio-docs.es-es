---
title: "Creación. Archivos Vsct | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bad1a8cbd8bc0369d405bf0a0c26c4285e143e46
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="authoring-vsct-files"></a>Creación. Archivos Vsct
Este documento muestra cómo crear un archivo .vsct para agregar elementos de menú, barras de herramientas y otros elementos de interfaz de usuario para el entorno de desarrollo integrado (IDE) de Visual Studio. Cuando se agregan elementos de interfaz de usuario a un paquete de Visual Studio (VSPackage) que ya no tiene un archivo .vsct, siga estos pasos.  
  
 Para los proyectos nuevos, se recomienda que utilice la plantilla de paquete de Visual Studio porque genera un archivo .vsct que, dependiendo de las selecciones, ya tiene los elementos necesarios para un comando de menú, una ventana de herramientas o un editor personalizado. Puede modificar este archivo .vsct para cumplir los requisitos del paquete de VS. Para obtener más información sobre cómo modificar un archivo .vsct, vea los ejemplos de [extender menús y comandos de](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="authoring-the-file"></a>Crear el archivo  
 Cree un archivo .vsct en estas fases: crear la estructura de archivos y recursos, declare los elementos de interfaz de usuario, coloca los elementos de interfaz de usuario en el IDE y agregue cualquier comportamiento especializado.  
  
### <a name="file-structure"></a>Estructura de archivos  
 Es la estructura básica de un archivo .vsct una [CommandTable](../../extensibility/commandtable-element.md) elemento raíz que contiene un [comandos](../../extensibility/commands-element.md) elemento y un [símbolos](../../extensibility/symbols-element.md) elemento.  
  
##### <a name="to-create-the-file-structure"></a>Para crear la estructura de archivos  
  
1.  Agregar un archivo .vsct al proyecto siguiendo los pasos descritos en [Cómo: crear una. Archivo de Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2.  Agregar los espacios de nombres necesarios para la `CommandTable` elemento, tal como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  En el `CommandTable` elemento, agregue un `Commands` elemento para hospedar todos los menús personalizados, barras de herramientas, grupos de comandos y comandos. Para que pueden cargar sus elementos de interfaz de usuario personalizados, el `Commands` el elemento debe tener su `Package` atributo establecido en el nombre del paquete.  
  
     Después de la `Commands` elemento, agregue un `Symbols` elemento para definir los GUID para el paquete y los nombres e identificadores de comando para los elementos de interfaz de usuario.  
  
### <a name="including-visual-studio-resources"></a>Al incluir recursos de Visual Studio  
 Use la [Extern](../../extensibility/extern-element.md) elemento que se va a obtener acceso a los archivos que definen los comandos de Visual Studio y los menús que se necesitan para colocar los elementos de interfaz de usuario en el IDE. Si va a usar comandos definidos fuera de su paquete, use el [UsedCommands](../../extensibility/usedcommands-element.md) elemento para informar a Visual Studio.  
  
##### <a name="to-include-visual-studio-resources"></a>Para incluir recursos de Visual Studio  
  
1.  En la parte superior de la `CommandTable` elemento, agregue una `Extern` (elemento) para cada archivo externo al que hace referencia, y establecer el `href` atributo por el nombre del archivo. Puede hacer referencia a los siguientes archivos de encabezado para tener acceso a recursos de Visual Studio:  
  
    -   Stdidcmd.h, define los identificadores para todos los comandos que se exponen mediante Visual Studio.  
  
    -   Vsshlids.h, contiene los identificadores de comando para los menús de Visual Studio.  
  
2.  Si el paquete llama a los comandos que se definen por Visual Studio u otros paquetes, agregue un `UsedCommands` elemento tras el `Commands` elemento. Rellenar este elemento con un [UsedCommand](../../extensibility/usedcommand-element.md) (elemento) para cada comando que decir llamar no forma parte del paquete. Establecer el `guid` y `id` atributos de la `UsedCommand` elementos a los valores GUID y el ID de los comandos para llamar a. Para obtener más información acerca de cómo encontrar los comandos de GUID e identificadores de Visual Studio, vea [GUID e identificadores de comandos de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Para llamar a comandos desde otros paquetes, use el GUID y el Id. del comando tal como se define en el archivo .vsct para esos paquetes.  
  
### <a name="declaring-ui-elements"></a>Declarar elementos de interfaz de usuario  
 Declarar todos los elementos de interfaz de usuario nueva en la `Symbols` sección del archivo vsct.  
  
##### <a name="to-declare-ui-elements"></a>Para declarar elementos de interfaz de usuario  
  
1.  En el `Symbols` elemento, agregar tres [GuidSymbol](../../extensibility/guidsymbol-element.md) elementos. Cada `GuidSymbol` elemento tiene un `name` atributo y un `value` atributo. Establecer el `name` atributo para que refleje el propósito del elemento. El `value` atributo toma un GUID. (Para generar un GUID en el **herramientas** menú, haga clic en **crear GUID**y, a continuación, seleccione **formato del registro**.)  
  
     La primera `GuidSymbol` elemento representa el paquete y normalmente no tiene elementos secundarios. El segundo `GuidSymbol` elemento representa el comando establece y contendrá todos los símbolos que definen los menús, los grupos y los comandos. La tercera `GuidSymbol` elemento representa el almacén de imágenes y contiene los símbolos para todos los iconos para los comandos. Si no dispone de ningún comando que usan iconos, puede omitir la tercera `GuidSymbol` elemento.  
  
2.  En el `GuidSymbol` elemento que representa el conjunto de comandos, agregue uno o varios [IDSymbol](../../extensibility/idsymbol-element.md) elementos. Cada uno de ellos representa un menú, una barra de herramientas, un grupo o un comando que se va a agregar a la interfaz de usuario.  
  
     Para cada `IDSymbol` elemento, establezca la `name` atributo por el nombre que usará para hacer referencia al menú correspondiente, grupo o comando y, a continuación, establezca el `value` elemento a un número hexadecimal que representa el identificador de comando. No hay dos `IDSymbol` elementos que tienen el mismo elemento primario pueden tener el mismo valor.  
  
3.  Si cualquiera de los elementos de interfaz de usuario requieren iconos, agregue un `IDSymbol` (elemento) para cada icono para el `GuidSymbol` elemento que representa el almacén de imágenes.  
  
### <a name="putting-ui-elements-in-the-ide"></a>Colocar elementos de interfaz de usuario en el IDE  
 El [menús](../../extensibility/menus-element.md) elemento, [grupos](../../extensibility/groups-element.md) elemento, y [botones](../../extensibility/buttons-element.md) elemento contienen las definiciones de todos los menús, los grupos y los comandos que se definen en el paquete. Coloca estos menús, los grupos y los comandos en el IDE ya sea mediante un [primario](../../extensibility/parent-element.md) elemento, que forma parte de la definición de elemento de interfaz de usuario, o mediante un [CommandPlacement](../../extensibility/commandplacement-element.md) elemento que está definida en otra parte.  
  
 Cada `Menu`, `Group`, y `Button` elemento tiene un `guid` atributo y un `id` atributo. Siempre establece la `guid` atributo para que coincida con el nombre de la `GuidSymbol` elemento que representa el comando establecer y establecer el `id` atributo en el nombre de la `IDSymbol` elemento que representa el menú, grupo o comando en el `Symbols`sección.  
  
##### <a name="to-define-ui-elements"></a>Para definir elementos de interfaz de usuario  
  
1.  Si va a definir nuevos menús, submenús, menús contextuales ni las barras de herramientas, agregue un `Menus` elemento a la `Commands` elemento. A continuación, para que cada menú que se cree, agregue un [menú](../../extensibility/menu-element.md) elemento a la `Menus` elemento.  
  
     Establecer el `guid` y `id` atributos de la `Menu` elemento y, después, establezca el `type` atributo al tipo de menú que desee. También puede establecer el `priority` atributo para establecer la posición relativa del menú en el grupo primario.  
  
    > [!NOTE]
    >  El `priority` atributo no se aplica a las barras de herramientas y menús contextuales.  
  
2.  Todos los comandos en el IDE de Visual Studio se deben hospedar en grupos de comandos, que son los elementos secundarios directos de los menús y barras de herramientas. Si va a agregar nuevos menús o barras de herramientas en el IDE, se deben contener nuevos grupos de comandos. También se pueden agregar grupos de comandos a menús y barras de herramientas existentes para que se pueden agrupar visualmente los comandos.  
  
     Al agregar nuevos grupos de comandos, primero debe crear un `Groups` elemento y a continuación, agregarle una [grupo](../../extensibility/group-element.md) (elemento) para cada grupo de comandos.  
  
     Establecer el `guid` y `id` atributos de cada `Group` elemento y, después, establezca el `priority` atributo para establecer la posición relativa del grupo en el menú del elemento primario. Para obtener más información, consulte [crear grupos de reutilizable de botones](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3.  Si va a agregar nuevos comandos en el IDE, agregue un `Buttons` elemento a la `Commands` elemento. A continuación, para cada comando, agregue un [botón](../../extensibility/button-element.md) elemento a la `Buttons` elemento.  
  
    1.  Establecer el `guid` y `id` atributos de cada `Button` elemento y, después, establezca el `type` atributo al tipo de botón que desee. También puede establecer el `priority` atributo para establecer la posición relativa del comando en el grupo primario.  
  
        > [!NOTE]
        >  Use `type="button"` para botones de barras de herramientas y comandos de menú estándar.  
  
    2.  En el `Button` elemento, agregue un [cadenas](../../extensibility/strings-element.md) elemento que contiene un [ButtonText](../../extensibility/buttontext-element.md) elemento y un [CommandName](../../extensibility/commandname-element.md) elemento. El `ButtonText` elemento proporciona la etiqueta de texto para un elemento de menú o la información sobre herramientas para un botón de barra de herramientas. El `CommandName` elemento proporciona el nombre del comando que se va a utilizar en el comando.  
  
    3.  Si el comando tendrá un icono, cree un [icono](../../extensibility/icon-element.md) elemento en el `Button` y establezca su `guid` y `id` atributos a la `Bitmap` (elemento) para el icono.  
  
        > [!NOTE]
        >  Botones de barra de herramientas deben tener iconos.  
  
     Para obtener más información, vea [MenuCommands frente a. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
4.  Si cualquiera de los comandos de requerir iconos, agregue un [mapas de bits](../../extensibility/bitmaps-element.md) elemento a la `Commands` elemento. A continuación, para cada icono, agregue un [mapa de bits](../../extensibility/bitmap-element.md) elemento a la `Bitmaps` elemento. Aquí es donde se especifica la ubicación del recurso de mapa de bits. Para obtener más información, consulte [agregar iconos a los comandos de menú](../../extensibility/adding-icons-to-menu-commands.md).  
  
 Puede basarse en la estructura de relación jerárquica para colocar correctamente la mayoría de los menús, grupos y comandos. Para conjuntos de comandos muy grandes, o cuando un menú, grupo o comando debe aparecer en varios lugares, se recomienda que especifique la ubicación del comando.  
  
##### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Confiar en la relación jerárquica colocar los elementos de interfaz de usuario en el IDE  
  
1.  Para la relación jerárquica típico, cree un `Parent` elemento en cada `Menu`, `Group`, y `Command` elemento que se define en el paquete.  
  
     El destino de la `Parent` elemento es el menú o el grupo que contendrá el menú, el grupo o el comando.  
  
    1.  Establecer el `guid` de atributo en el nombre de la `GuidSymbol` elemento que define el conjunto de comandos. Si el elemento de destino no forma parte del paquete, use el guid para ese conjunto de comandos, tal como se define en el archivo .vsct correspondiente.  
  
    2.  Establecer el `id` atributo para que coincida con el `id` atributo del menú de destino o del grupo. Para obtener una lista de los menús y los grupos a los que se exponen mediante Visual Studio, vea [GUID e identificadores de menús de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o [GUID e identificadores de Visual Studio barras de herramientas](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
 Si tiene un gran número de elementos de interfaz de usuario que se va a colocar en el IDE, o si tiene elementos que deben aparecer en varios lugares, defina sus ubicaciones en el [CommandPlacements](../../extensibility/commandplacements-element.md) elemento, tal como se muestra en los pasos siguientes.  
  
##### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Para usar la ubicación de comando para colocar los elementos de interfaz de usuario en el IDE  
  
1.  Después de la `Commands` elemento, agregue un `CommandPlacements` elemento.  
  
2.  En el `CommandPlacements` elemento, agregue un `CommandPlacement` (elemento) para cada menú, grupo o comando para colocar.  
  
     Cada `CommandPlacement` elemento o `Parent` elemento coloca un menú, grupo o comando en una ubicación de IDE. Un elemento de interfaz de usuario sólo puede tener un elemento primario, pero puede tener varias ubicaciones de comando. Para colocar un elemento de interfaz de usuario en varias ubicaciones, agregue un `CommandPlacement` elemento para cada ubicación.  
  
3.  Establecer el `guid` y `id` atributos de cada `CommandPlacement` elemento en el menú de host o grupo, tal y como lo haría para un `Parent` elemento. También puede establecer el `priority` atributo para establecer la posición relativa del elemento de interfaz de usuario.  
  
 Puede mezclar colocación por relación jerárquica y ubicación del comando. Sin embargo, para los conjuntos de comandos muy grandes, recomendamos que use solo ubicación del comando.  
  
### <a name="adding-specialized-behaviors"></a>Agregar los comportamientos especializados  
 Puede usar [CommandFlag](../../extensibility/command-flag-element.md) elementos para modificar el comportamiento de los menús y comandos, por ejemplo, para cambiar su apariencia y la visibilidad. También pueden afectar a si el comando es visible mediante el uso de [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md), o agregar métodos abreviados de teclado mediante [enlaces de teclado](../../extensibility/keybindings-element.md). Ciertos tipos de menús y comandos ya dispone de especializado comportamientos integrados.  
  
##### <a name="to-add-specialized-behaviors"></a>Para agregar los comportamientos especializados  
  
1.  Para convertir un elemento de interfaz de usuario visible solo en ciertos contextos de interfaz de usuario, por ejemplo, cuando se carga una solución, utilice restricciones de visibilidad.  
  
    1.  Después de la `Commands` elemento, agregue un `VisibilityConstraints` elemento.  
  
    2.  Para que cada elemento de la interfaz de usuario restringir, agregue un [VisibilityItem](../../extensibility/visibilityitem-element.md) elemento.  
  
    3.  Para cada `VisibilityItem` elemento, establezca la `guid` y `id` atributos en el menú, grupo, o comando y, a continuación, ajuste la `context` de atributo en el contexto de la interfaz de usuario que desee, tal como se define en la <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> clase. Para obtener más información, consulte [VisibilityItem elemento](../../extensibility/visibilityitem-element.md).  
  
2.  Para establecer la visibilidad o la disponibilidad de un elemento de interfaz de usuario en el código, utilice uno o varios de los siguientes indicadores de comando:  
  
    -   DefaultDisabled  
  
    -   DefaultInvisible  
  
    -   DynamicItemStart  
  
    -   DynamicVisibility  
  
    -   NoShowOnMenuController  
  
    -   NotInTBList  
  
     Para obtener más información, consulte [comando marca elemento](../../extensibility/command-flag-element.md).  
  
3.  Para cambiar cómo aparece un elemento o cambiar su apariencia dinámicamente, use uno o varios de los siguientes indicadores de comando:  
  
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
  
     Para obtener más información, consulte [comando marca elemento](../../extensibility/command-flag-element.md).  
  
4.  Para cambiar cómo un elemento reacciona cuando recibe comandos, utilice uno o varios de los siguientes indicadores de comando:  
  
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
  
     Para obtener más información, consulte [comando marca elemento](../../extensibility/command-flag-element.md).  
  
5.  Para asociar un método abreviado de teclado dependiente de menú a un menú o un elemento en un menú, agregue un carácter de "y" comercial ('& ') en el `ButtonText` elemento del menú o un elemento de menú. El carácter que sigue a la y comercial es el método abreviado de teclado activa cuando se abre el menú del elemento primario.  
  
6.  Para asociar un método abreviado de teclado independiente de menú a un comando, utilice [enlaces de teclado](../../extensibility/keybindings-element.md). Para obtener más información, consulte [KeyBinding elemento](../../extensibility/keybinding-element.md).  
  
7.  Para localizar el texto de menú, use la `LocCanonicalName` elemento. Para obtener más información, consulte [elemento Strings](../../extensibility/strings-element.md).  
  
 Algunos tipos de menú y botón incluyen comportamientos especializados. En la tabla siguiente se describe algunas menú especializada y tipos de botones. Para otros tipos, vea la `types` atributo descripciones en [el elemento de menú](../../extensibility/menu-element.md), [elemento Button](../../extensibility/button-element.md), y [elemento combinado](../../extensibility/combo-element.md).  
  
 Cuadro combinado  
 Un cuadro combinado es una lista desplegable que se puede usar en una barra de herramientas. Para agregar cuadros combinados a la interfaz de usuario, cree un [combinaciones](../../extensibility/combos-element.md) elemento en el `Commands` elemento. A continuación, agregue el `Combos` elemento un `Combo` elemento para cada cuadro combinado agregar. `Combo`elementos tienen los mismos atributos y elementos secundarios como `Button` elementos y también tienen `DefaultWidth` y `idCommandList` atributos. El `DefaultWidth` atributo establece el ancho en píxeles y el `idCommandList` atributo apunta a un identificador de comando que se usa para rellenar el cuadro combinado. Para obtener más información, consulte el `Combo` documentación del elemento.  
  
 MenuController  
 Un controlador de menú es un botón que tiene una flecha situada junto a él. Haga clic en la flecha abre una lista. Para agregar un controlador de menú a la interfaz de usuario, cree un `Menu` y establezca su `type` atribuir a **MenuController** o **MenuControllerLatched**, según el comportamiento que desee. Para rellenar un controlador de menú, establézcalo como el elemento primario de un `Group` elemento. El controlador de menú mostrará a todos los elementos secundarios de ese grupo en la lista desplegable.  
  
## <a name="see-also"></a>Vea también  
 [Extender menús y comandos](../../extensibility/extending-menus-and-commands.md)   
 [Tabla de comandos de Visual Studio (. Archivos Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)