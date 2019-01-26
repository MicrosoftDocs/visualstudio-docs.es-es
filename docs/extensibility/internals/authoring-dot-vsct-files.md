---
title: Creación. Archivos Vsct | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b780a426423b1d974bb4ab78ee586ca3e6b943ca
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55039060"
---
# <a name="author-vsct-files"></a>Archivos .vsct de autor
Este documento muestra cómo crear un *.vsct* archivo para agregar elementos de menú, barras de herramientas y otros elementos de interfaz de usuario para el entorno de desarrollo integrado (IDE) de Visual Studio. Siga estos pasos al agregar elementos de interfaz de usuario a un paquete de Visual Studio (VSPackage) que no tenga ya una *.vsct* archivo.  
  
 Para proyectos nuevos, se recomienda usar la plantilla de paquete de Visual Studio porque genera un *.vsct* archivo que, dependiendo de las selecciones, ya tiene los elementos necesarios para un comando de menú, una ventana de herramientas o un editor personalizado . Puede modificar este *.vsct* archivo para cumplir los requisitos del paquete VSPackage. Para obtener más información sobre cómo modificar un *.vsct* de archivos, vea los ejemplos de [amplían los menús y comandos](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="author-the-file"></a>Cree el archivo  
 Crear un *.vsct* archivo en estas fases: Crear la estructura de archivos y recursos, declare los elementos de interfaz de usuario, coloque los elementos de interfaz de usuario en el IDE y agregue cualquier comportamiento especializado.  
  
### <a name="file-structure"></a>Estructura de archivos  
 La estructura básica de un *.vsct* archivo es un [CommandTable](../../extensibility/commandtable-element.md) elemento raíz que contiene un [comandos](../../extensibility/commands-element.md) elemento y un [símbolos](../../extensibility/symbols-element.md) elemento.  
  
#### <a name="to-create-the-file-structure"></a>Para crear la estructura de archivos  
  
1.  Agregar un *.vsct* archivo al proyecto siguiendo los pasos descritos en [Cómo: Crear un archivo .vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2. Agregar los espacios de nombres necesarios para la `CommandTable` elemento, como se muestra en el ejemplo siguiente:  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  En el `CommandTable` elemento, agregue un `Commands` elemento para hospedar todos los menús personalizados, las barras de herramientas, grupos de comandos y los comandos. Para que pueden cargar sus elementos de interfaz de usuario personalizados, el `Commands` elemento debe tener su `Package` atributo establecido en el nombre del paquete.  
  
     Después de la `Commands` elemento, agregue un `Symbols` elemento para definir los GUID para el paquete y los nombres e identificadores de comando para los elementos de interfaz de usuario.  
  
### <a name="include-visual-studio-resources"></a>Incluir recursos de Visual Studio  
 Use la [Extern](../../extensibility/extern-element.md) elemento para tener acceso a los archivos que definen los comandos de Visual Studio y los menús que se deben colocar los elementos de interfaz de usuario en el IDE. Si va a usar los comandos definidos fuera de su paquete, use el [UsedCommands](../../extensibility/usedcommands-element.md) elemento para informar a Visual Studio.  
  
#### <a name="to-include-visual-studio-resources"></a>Para incluir recursos de Visual Studio  
  
1. En la parte superior de la `CommandTable` elemento, agregue uno `Extern` (elemento) para cada archivo externo hacer referencia y establecer el `href` atributo por el nombre del archivo. Puede hacer referencia a los archivos de encabezado siguiente para obtener acceso a recursos de Visual Studio:  
  
   -   *Stdidcmd.h*: Define identificadores para todos los comandos que expone Visual Studio.  
  
   -   *Vsshlids.h*: Contiene los identificadores de comando para los menús de Visual Studio.  
  
2. Si el paquete llama a los comandos que se definen mediante Visual Studio o mediante otros paquetes, agregue un `UsedCommands` elemento tras el `Commands` elemento. Rellenar este elemento con un [UsedCommand](../../extensibility/usedcommand-element.md) (elemento) para cada comando que es llamar no forma parte del paquete. Establecer el `guid` y `id` los atributos de la `UsedCommand` elementos a los valores GUID y el Id. de los comandos para llamar a. 

   Para obtener más información acerca de cómo encontrar los comandos de GUID e identificadores de Visual Studio, consulte [comandos GUID e identificadores de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Para llamar a los comandos de otros paquetes, use el GUID y el identificador del comando tal como se define en el *.vsct* archivo para esos paquetes.
  
### <a name="declare-ui-elements"></a>Declare los elementos de interfaz de usuario  
 Declarar todos los elementos de interfaz de usuario nueva en el `Symbols` sección de la *.vsct* archivo.  
  
#### <a name="to-declare-ui-elements"></a>Para declarar elementos de interfaz de usuario  
  
1.  En el `Symbols` elemento, agregue tres [GuidSymbol](../../extensibility/guidsymbol-element.md) elementos. Cada `GuidSymbol` elemento tiene un `name` atributo y un `value` atributo. Establecer el `name` atributo para que refleje el propósito del elemento. El `value` atributo toma un GUID. (Para generar un GUID, en el **herramientas** menú, seleccione **crear GUID**y, a continuación, seleccione **formato del registro**.)  
  
     La primera `GuidSymbol` elemento representa el paquete y normalmente no tiene elementos secundarios. El segundo `GuidSymbol` elemento representa el comando establece y contendrá todos los símbolos que definen los menús, grupos y comandos. La tercera `GuidSymbol` elemento representa el almacén de imágenes y contiene los símbolos para todos los iconos para los comandos. Si no dispone de ningún comando que usan iconos, puede omitir la tercera `GuidSymbol` elemento.  
  
2.  En el `GuidSymbol` elemento que representa el conjunto de comandos, agregue uno o varios [IDSymbol](../../extensibility/idsymbol-element.md) elementos. Cada una de estas representan un menú, barra de herramientas, grupo o comando que se va a agregar a la interfaz de usuario.  
  
     Para cada `IDSymbol` elemento, establezca el `name` atributo por el nombre que usará para hacer referencia a la correspondiente menú, grupo o comando y, a continuación, establezca el `value` elemento a un número hexadecimal que representa el identificador de comando. No hay dos `IDSymbol` los elementos que tienen el mismo elemento primario pueden tener el mismo valor.  
  
3.  Si alguno de los elementos de interfaz de usuario requiere iconos, agregue un `IDSymbol` (elemento) para cada icono para el `GuidSymbol` elemento que representa el almacén de imágenes.  
  
### <a name="put-ui-elements-in-the-ide"></a>Colocar elementos de interfaz de usuario en el IDE  
 El [menús](../../extensibility/menus-element.md), [grupos](../../extensibility/groups-element.md), y [botones](../../extensibility/buttons-element.md) elementos contienen las definiciones de todos los menús, grupos y los comandos que se definen en el paquete. Poner estos menús, grupos y comandos en el IDE, ya sea mediante un [primario](../../extensibility/parent-element.md) elemento, que forma parte de la definición de elemento de interfaz de usuario o mediante un [CommandPlacement](../../extensibility/commandplacement-element.md) elemento que está definida en otra parte.  
  
 Cada `Menu`, `Group`, y `Button` elemento tiene un `guid` atributo y un `id` atributo. Siempre establece la `guid` atributo para que coincida con el nombre de la `GuidSymbol` establezca el elemento que representa el comando y establezca el `id` atributo en el nombre de la `IDSymbol` elemento que representa el menú, grupo o comando en el `Symbols`sección.  
  
#### <a name="to-define-ui-elements"></a>Para definir los elementos de interfaz de usuario  
  
1. Si va a definir nuevos menús, submenús, menús contextuales ni las barras de herramientas, agregue un `Menus` elemento a la `Commands` elemento. A continuación, para que cada menú se puede crear, agregue un [menú](../../extensibility/menu-element.md) elemento a la `Menus` elemento.  
  
    Establecer el `guid` y `id` los atributos de la `Menu` elemento y, después, establezca el `type` atributo al tipo de menú que desea. También puede establecer el `priority` atributo para establecer la posición relativa del menú en el grupo primario.  
  
   > [!NOTE]
   >  El `priority` atributo no es aplicable a las barras de herramientas y menús contextuales.  
  
2. Todos los comandos en el IDE de Visual Studio deben hospedarse en grupos de comandos que son elementos secundarios directos de los menús y barras de herramientas. Si va a agregar nuevos menús o barras de herramientas al IDE, estos deben contener nuevos grupos de comandos. También puede agregar grupos de comandos a menús y barras de herramientas existentes para que se pueden agrupar visualmente los comandos.  
  
    Al agregar nuevos grupos de comandos, debe crear primero un `Groups` elemento y, a continuación, agregarle una [grupo](../../extensibility/group-element.md) (elemento) para cada grupo de comandos.  
  
    Establecer el `guid` y `id` atributos de cada uno `Group` elemento y, después, establezca el `priority` atributo para establecer la posición relativa del grupo en el menú primario. Para obtener más información, consulte [crear grupos reutilizables de botones](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3. Si va a agregar nuevos comandos en el IDE, agregue un `Buttons` elemento a la `Commands` elemento. A continuación, para cada comando, agregue un [botón](../../extensibility/button-element.md) elemento a la `Buttons` elemento.  
  
   1.  Establecer el `guid` y `id` atributos de cada uno `Button` elemento y, después, establezca el `type` atributo al tipo de botón que desee. También puede establecer el `priority` atributo para establecer la posición relativa del comando en el grupo primario.  
  
       > [!NOTE]
       >  Use `type="button"` para los botones de las barras de herramientas y comandos de menú estándar.  
  
   2.  En el `Button` elemento, agregue un [cadenas](../../extensibility/strings-element.md) elemento que contiene un [ButtonText](../../extensibility/buttontext-element.md) elemento y un [CommandName](../../extensibility/commandname-element.md) elemento. El `ButtonText` elemento proporciona la etiqueta de texto para un elemento de menú o la información sobre herramientas para un botón de barra de herramientas. El `CommandName` elemento proporciona el nombre del comando para usar en el comando.  
  
   3.  Si el comando tendrá un icono, cree un [icono](../../extensibility/icon-element.md) elemento en el `Button` y establezca su `guid` y `id` atributos a la `Bitmap` (elemento) para el icono.  
  
       > [!NOTE]
       >  Botones de barra de herramientas deben tener iconos.  
  
   Para obtener más información, consulte [MenuCommands frente a. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
4. Si cualquiera de los comandos requieren iconos, agregue un [mapas de bits](../../extensibility/bitmaps-element.md) elemento a la `Commands` elemento. A continuación, para cada icono, agregue un [mapa de bits](../../extensibility/bitmap-element.md) elemento a la `Bitmaps` elemento. Aquí es donde se especifica la ubicación del recurso de mapa de bits. Para obtener más información, consulte [agregar iconos a comandos de menú](../../extensibility/adding-icons-to-menu-commands.md).  
  
   Puede confiar en la estructura de la relación jerárquica para colocar correctamente la mayoría de los menús, grupos y comandos. Para conjuntos de comandos muy grandes, o cuando un menú, grupo o comando debe aparecer en varios lugares, se recomienda que especifique la ubicación del comando.  
  
#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Confiar en la relación jerárquica colocar los elementos de interfaz de usuario en el IDE  
  
1. Para crianza típico, cree un `Parent` cada elemento `Menu`, `Group`, y `Command` elemento que se define en el paquete.  
  
    El destino de la `Parent` elemento es el menú o grupo que contiene el menú, grupo o comando.  
  
   1.  Establecer el `guid` atributo en el nombre de la `GuidSymbol` elemento que define el conjunto de comandos. Si el elemento de destino no forma parte del paquete, use el guid para ese conjunto de comandos, tal como se define en las correspondientes *.vsct* archivo.  
  
   2.  Establecer el `id` atributo para que coincida con el `id` atributo del grupo o menú de destino. Para obtener una lista de los menús y los grupos que se exponen mediante Visual Studio, consulte [menús GUID e identificadores de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o [las barras de herramientas de GUID e identificadores de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
   Si tiene un gran número de elementos de interfaz de usuario para colocar en el IDE, o si tiene elementos que deben aparecer en varios lugares, defina sus ubicaciones en el [CommandPlacements](../../extensibility/commandplacements-element.md) elemento, como se muestra en los pasos siguientes.  
  
#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Para usar la ubicación del comando colocar los elementos de interfaz de usuario en el IDE  
  
1. Después de la `Commands` elemento, agregue un `CommandPlacements` elemento.  
  
2. En el `CommandPlacements` elemento, agregue un `CommandPlacement` (elemento) para cada menú, grupo o comando para colocar.  
  
    Cada `CommandPlacement` elemento o `Parent` elemento coloca un menú, grupo o comando en una ubicación de IDE. Un elemento de interfaz de usuario solo puede tener un elemento primario, pero puede tener varias ubicaciones de comando. Para colocar un elemento de interfaz de usuario en varias ubicaciones, agregue un `CommandPlacement` (elemento) para cada ubicación.  
  
3. Establecer el `guid` y `id` atributos de cada uno `CommandPlacement` elemento en el menú de hospedaje o grupo, igual que haría para un `Parent` elemento. También puede establecer el `priority` atributo para establecer la posición relativa del elemento de interfaz de usuario.  
  
   Puede mezclar la selección de ubicación mediante la relación jerárquica y ubicación del comando. Sin embargo, para conjuntos de comandos muy grandes, recomendamos que use solo la colocación de comando.  
  
### <a name="add-specialized-behaviors"></a>Agregar comportamientos especializados  
 Puede usar el [CommandFlag](../../extensibility/command-flag-element.md) elemento para modificar el comportamiento de los menús y comandos, por ejemplo, para cambiar su apariencia y la visibilidad. También puede afectar a si el comando es visible mediante el uso de la [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) elemento, o agregar métodos abreviados de teclado mediante el [KeyBindings](../../extensibility/keybindings-element.md) elemento. Ciertos tipos de menús y comandos ya dispone de los comportamientos integrados especializado.  
  
#### <a name="to-add-specialized-behaviors"></a>Para agregar comportamientos especializados  
  
1. Para hacer que un elemento de interfaz de usuario visible solo en determinados contextos de interfaz de usuario, por ejemplo, cuando se carga una solución, utilice restricciones de visibilidad.  
  
   1.  Después de la `Commands` elemento, agregue un `VisibilityConstraints` elemento.  
  
   2.  Para que cada elemento de interfaz de usuario restringir, agregue un [VisibilityItem](../../extensibility/visibilityitem-element.md) elemento.  
  
   3.  Para cada `VisibilityItem` elemento, establezca el `guid` y `id` atributos en el menú, grupo o comando y, después, establezca el `context` atributo en el contexto de interfaz de usuario que desee, como se define en el <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> clase.   
  
2. Para establecer la visibilidad o la disponibilidad de un elemento de interfaz de usuario en el código, utilice uno o varios de los siguientes marcadores de comando:  
  
   -   `DefaultDisabled`
  
   -   `DefaultInvisible`
  
   -   `DynamicItemStart` 
  
   -   `DynamicVisibility`
  
   -   `NoShowOnMenuController`
  
   -   `NotInTBList`
  
   Para obtener más información, consulte el [CommandFlag](../../extensibility/command-flag-element.md) elemento.  
  
3. Para cambiar cómo aparece un elemento, o cambiar su apariencia dinámicamente, use uno o varios de los siguientes marcadores de comando:  
  
   -   `AlwaysCreate`  
  
   -   `CommandWellOnly`  
  
   -   `DefaultDocked`  
  
   -   `DontCache`  
  
   -   `DynamicItemStart`  
  
   -   `FixMenuController`  
  
   -   `IconAndText`  
  
   -   `Pict`  
  
   -   `StretchHorizontally`  
  
   -   `TextMenuUseButton`  
  
   -   `TextChanges`  
  
   -   `TextOnly`  
  
   Para obtener más información, consulte el [CommandFlag](../../extensibility/command-flag-element.md) elemento.  
  
4. Para cambiar el modo en que un elemento reacciona cuando recibe los comandos, use uno o varios de los siguientes marcadores de comando:  
  
   -   `AllowParams`  
  
   -   `CaseSensitive`  
  
   -   `CommandWellOnly`  
  
   -   `FilterKeys`  
  
   -   `NoAutoComplete`  
  
   -   `NoButtonCustomize`  
  
   -   `NoKeyCustomize`  
  
   -   `NoToolbarClose`  
  
   -   `PostExec`  
  
   -   `RouteToDocs`  
  
   -   `TextIsAnchorCommand`  
  
   Para obtener más información, consulte el [CommandFlag](../../extensibility/command-flag-element.md) elemento.  
  
5. Para asociar un método abreviado dependiente de menú a un menú o un elemento en un menú, agregue un carácter de y comercial (&) en el `ButtonText` (elemento) para el elemento de menú o menú. El carácter que sigue a la y comercial es el método abreviado de teclado activa cuando se abre el menú primario.  
  
6. Para asociar el método abreviado de teclado del menú independiente a un comando, use el [KeyBindings](../../extensibility/keybindings-element.md) elemento. Para obtener más información, consulte el [KeyBinding](../../extensibility/keybinding-element.md) elemento.  
  
7. Para localizar el texto de menú, use el `LocCanonicalName` elemento. Para obtener más información, consulte el [cadenas](../../extensibility/strings-element.md) elemento.  
  
   Algunos tipos de menú y el botón incluir comportamientos especializados. En la lista siguiente se describe algunos tipos de botón y un menú especializado. Para otros tipos, vea la `types` atributo descripciones en el [menú](../../extensibility/menu-element.md), [botón](../../extensibility/button-element.md), y [combinado](../../extensibility/combo-element.md) elementos.  
  
   - Cuadro combinado:  
   Un cuadro combinado es una lista desplegable que se puede usar en una barra de herramientas. Para agregar los cuadros combinados de la interfaz de usuario, cree un [Combos](../../extensibility/combos-element.md) elemento en el `Commands` elemento. A continuación, agregar a la `Combos` elemento un `Combo` (elemento) para cada cuadro combinado agregar. `Combo` los elementos tienen los mismos atributos y elementos secundarios como `Button` elementos y también tener `DefaultWidth` y `idCommandList` atributos. El `DefaultWidth` atributo establece el ancho en píxeles y el `idCommandList` atributo apunta a un identificador de comando que se usa para rellenar el cuadro combinado. 
  
   - Controlador de menú:  
   Un controlador de menú es un botón que tiene una flecha junto a él. Al hacer clic en la flecha abre una lista. Para agregar un controlador de menú a la interfaz de usuario, cree un `Menu` y establezca su `type` atributo `MenuController` o `MenuControllerLatched`, según el comportamiento que desee. Para rellenar un controlador de menú, establézcalo como el elemento primario de un `Group` elemento. El controlador de menú mostrará a todos los elementos secundarios de ese grupo en su lista desplegable.  
  
## <a name="see-also"></a>Vea también  
 [Extender los menús y comandos](../../extensibility/extending-menus-and-commands.md)   
 [Archivos visuales Studio comando table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)