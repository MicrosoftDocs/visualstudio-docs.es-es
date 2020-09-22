---
title: Creación. Archivos Vsct | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85e466e7ebb6294a77e89040260c16fe0043e372
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842842"
---
# <a name="authoring-vsct-files"></a>Creación de archivos .Vsct
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En este documento se muestra cómo crear un archivo. Vsct para agregar elementos de menú, barras de herramientas y otros elementos de la interfaz de usuario (IU) al entorno de desarrollo integrado (IDE) de Visual Studio. Siga estos pasos al agregar elementos de interfaz de usuario a un paquete de Visual Studio (VSPackage) que todavía no tiene un archivo. Vsct.  
  
 En el caso de los proyectos nuevos, se recomienda usar la plantilla de paquete de Visual Studio, ya que genera un archivo. Vsct que, en función de las selecciones, ya tiene los elementos necesarios para un comando de menú, una ventana de herramientas o un editor personalizado. Puede modificar este archivo. Vsct para cumplir los requisitos de su VSPackage. Para obtener más información sobre cómo modificar un archivo. Vsct, vea los ejemplos de [extensión de menús y comandos](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="authoring-the-file"></a>Crear el archivo  
 Cree un archivo. Vsct en estas fases: cree la estructura de archivos y recursos, declare los elementos de la interfaz de usuario, coloque los elementos de la interfaz de usuario en el IDE y agregue cualquier comportamiento especializado.  
  
### <a name="file-structure"></a>Estructura de archivos  
 La estructura básica de un archivo. Vsct es un elemento raíz [CommandTable](../../extensibility/commandtable-element.md) que contiene un elemento [Commands](../../extensibility/commands-element.md) y un elemento [Symbols](../../extensibility/symbols-element.md) .  
  
##### <a name="to-create-the-file-structure"></a>Para crear la estructura de archivos  
  
1. Agregue un archivo. Vsct al proyecto siguiendo los pasos descritos en [Cómo: crear un. Archivo Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2. Agregue los espacios de nombres necesarios al `CommandTable` elemento, tal y como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3. En el `CommandTable` elemento, agregue un `Commands` elemento para hospedar todos los menús, barras de herramientas, grupos de comandos y comandos personalizados. Para que los elementos de la interfaz de usuario personalizados puedan cargarse, el `Commands` elemento debe tener su `Package` atributo establecido en el nombre del paquete.  
  
     Después del `Commands` elemento, agregue un `Symbols` elemento para definir los GUID para el paquete y los nombres y los identificadores de comando de los elementos de la interfaz de usuario.  
  
### <a name="including-visual-studio-resources"></a>Incluir recursos de Visual Studio  
 Use el elemento [extern](../../extensibility/extern-element.md) para tener acceso a los archivos que definen los comandos de Visual Studio y los menús necesarios para colocar los elementos de la interfaz de usuario en el IDE. Si va a utilizar comandos definidos fuera del paquete, use el elemento [UsedCommands](../../extensibility/usedcommands-element.md) para informar a Visual Studio.  
  
##### <a name="to-include-visual-studio-resources"></a>Para incluir recursos de Visual Studio  
  
1. En la parte superior del `CommandTable` elemento, agregue un `Extern` elemento para cada archivo externo al que se va a hacer referencia y establezca el `href` atributo en el nombre del archivo. Puede hacer referencia a los siguientes archivos de encabezado para tener acceso a los recursos de Visual Studio:  
  
    - Stdidcmd. h define los identificadores de todos los comandos expuestos por Visual Studio.  
  
    - Vsshlids. h contiene los identificadores de comando para los menús de Visual Studio.  
  
2. Si el paquete llama a cualquier comando definido por Visual Studio u otros paquetes, agregue un `UsedCommands` elemento después del `Commands` elemento. Rellene este elemento con un elemento [UsedCommand](../../extensibility/usedcommand-element.md) para cada comando al que llame y que no forme parte del paquete. Establezca los `guid` `id` atributos y de los `UsedCommand` elementos en los valores GUID y ID de los comandos a los que se va a llamar. Para obtener más información sobre cómo buscar los GUID e identificadores de los comandos de Visual Studio, vea [GUID e identificadores de comandos de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Para llamar a comandos desde otros paquetes, use el GUID y el identificador del comando, tal como se define en el archivo. Vsct para esos paquetes.  
  
### <a name="declaring-ui-elements"></a>Declarar elementos de la interfaz de usuario  
 Declare todos los nuevos elementos de la interfaz de usuario en la `Symbols` sección del archivo. Vsct.  
  
##### <a name="to-declare-ui-elements"></a>Para declarar elementos de la interfaz de usuario  
  
1. En el `Symbols` elemento, agregue tres elementos [GuidSymbol](../../extensibility/guidsymbol-element.md) . Cada `GuidSymbol` elemento tiene un `name` atributo y un `value` atributo. Establezca el `name` atributo para que refleje el propósito del elemento. El `value` atributo toma un GUID. (Para generar un GUID, en el menú **herramientas** , haga clic en **crear GUID**y, a continuación, seleccione **formato del registro**).  
  
     El primer `GuidSymbol` elemento representa el paquete y normalmente no tiene elementos secundarios. El segundo `GuidSymbol` elemento representa el conjunto de comandos y contendrá todos los símbolos que definen los menús, los grupos y los comandos. El tercer `GuidSymbol` elemento representa el almacén de imágenes y contiene símbolos para todos los iconos de los comandos. Si no tiene comandos que usen iconos, puede omitir el tercer `GuidSymbol` elemento.  
  
2. En el `GuidSymbol` elemento que representa el conjunto de comandos, agregue uno o más elementos [IDSymbol](../../extensibility/idsymbol-element.md) . Cada una de ellas representa un menú, una barra de herramientas, un grupo o un comando que se va a agregar a la interfaz de usuario.  
  
     Para cada `IDSymbol` elemento, establezca el `name` atributo en el nombre que va a utilizar para hacer referencia al menú, grupo o comando correspondiente y, a continuación, establezca el `value` elemento en un número hexadecimal que representará su identificador de comando. Dos `IDSymbol` elementos que tienen el mismo elemento primario no pueden tener el mismo valor.  
  
3. Si alguno de los elementos de la interfaz de usuario requiere iconos, agregue un `IDSymbol` elemento para cada icono al `GuidSymbol` elemento que representa el almacén de imágenes.  
  
### <a name="putting-ui-elements-in-the-ide"></a>Colocar elementos de la interfaz de usuario en el IDE  
 El elemento [menus](../../extensibility/menus-element.md) , [Groups](../../extensibility/groups-element.md) y [Buttons](../../extensibility/buttons-element.md) contiene las definiciones de todos los menús, grupos y comandos definidos en el paquete. Coloque estos menús, grupos y comandos en el IDE mediante el uso de un elemento [primario](../../extensibility/parent-element.md) , que forma parte de la definición del elemento de la interfaz de usuario o mediante el uso de un elemento [CommandPlacement](../../extensibility/commandplacement-element.md) que se define en otro lugar.  
  
 Cada `Menu` `Group` elemento, y `Button` tiene un `guid` atributo y un `id` atributo. Establezca siempre el `guid` atributo para que coincida con el nombre del `GuidSymbol` elemento que representa el conjunto de comandos y establezca el `id` atributo en el nombre del `IDSymbol` elemento que representa el menú, el grupo o el comando en la `Symbols` sección.  
  
##### <a name="to-define-ui-elements"></a>Para definir los elementos de la interfaz de usuario  
  
1. Si va a definir nuevos menús, submenús, menús contextuales o barras de herramientas, agregue un `Menus` elemento al `Commands` elemento. A continuación, para cada menú que se va a crear, agregue un elemento de [menú](../../extensibility/menu-element.md) al `Menus` elemento.  
  
    Establezca los `guid` `id` atributos y del `Menu` elemento y, a continuación, establezca el `type` atributo en el tipo de menú que desee. También puede establecer el `priority` atributo para establecer la posición relativa del menú en el grupo primario.  
  
   > [!NOTE]
   > El `priority` atributo no se aplica a las barras de herramientas y los menús contextuales.  
  
2. Todos los comandos del IDE de Visual Studio se deben hospedar en grupos de comandos, que son los elementos secundarios directos de los menús y las barras de herramientas. Si va a agregar nuevos menús o barras de herramientas al IDE, estos deben contener nuevos grupos de comandos. También puede agregar grupos de comandos a los menús y las barras de herramientas existentes para que pueda agrupar visualmente los comandos.  
  
    Al agregar nuevos grupos de comandos, primero debe crear un `Groups` elemento y, a continuación, agregarlo a un elemento de [Grupo](../../extensibility/group-element.md) para cada grupo de comandos.  
  
    Establezca los `guid` `id` atributos y de cada `Group` elemento y, a continuación, establezca el `priority` atributo para establecer la posición relativa del grupo en el menú primario. Para obtener más información, vea [crear grupos reutilizables de botones](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3. Si va a agregar nuevos comandos al IDE, agregue un `Buttons` elemento al `Commands` elemento. A continuación, para cada comando, agregue un elemento [botón](../../extensibility/button-element.md) al `Buttons` elemento.  
  
   1. Establezca los `guid` `id` atributos y de cada `Button` elemento y, a continuación, establezca el `type` atributo en el tipo de botón que desee. También puede establecer el `priority` atributo para establecer la posición relativa del comando en el grupo primario.  
  
      > [!NOTE]
      > Se usa `type="button"` para los botones y comandos de menú estándar en las barras de herramientas.  
  
   2. En el `Button` elemento, agregue un elemento [Strings](../../extensibility/strings-element.md) que contenga un elemento [ButtonText](../../extensibility/buttontext-element.md) y un elemento [CommandName](../../extensibility/commandname-element.md) . El `ButtonText` elemento proporciona la etiqueta de texto de un elemento de menú o la información sobre herramientas para un botón de la barra de herramientas. El `CommandName` elemento proporciona el nombre del comando que se va a usar en el cuadro de comandos.  
  
   3. Si el comando va a tener un icono, cree un elemento [Icon](../../extensibility/icon-element.md) en el `Button` elemento y establezca sus `guid` `id` atributos y en el `Bitmap` elemento para el icono.  
  
      > [!NOTE]
      > Los botones de la barra de herramientas deben tener iconos.  
  
      Para obtener más información, consulte [MenuCommands frente a OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
4. Si alguno de los comandos requiere iconos, agregue un elemento [bitmaps](../../extensibility/bitmaps-element.md) al `Commands` elemento. A continuación, para cada icono, agregue un elemento [Bitmap](../../extensibility/bitmap-element.md) al `Bitmaps` elemento. Aquí es donde se especifica la ubicación del recurso de mapa de bits. Para obtener más información, vea [Agregar iconos a comandos de menú](../../extensibility/adding-icons-to-menu-commands.md).  
  
   Puede confiar en la estructura de control parental para colocar correctamente la mayoría de los menús, grupos y comandos. En el caso de conjuntos de comandos muy grandes, o cuando un menú, un grupo o un comando deben aparecer en varios lugares, se recomienda especificar la ubicación del comando.  
  
##### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Basarse en el control parental para colocar elementos de la interfaz de usuario en el IDE  
  
1. En el caso de la protección típica, cree un `Parent` elemento en cada `Menu` `Group` elemento, y `Command` que se define en el paquete.  
  
    El destino del `Parent` elemento es el menú o grupo que contendrá el menú, el grupo o el comando.  
  
   1. Establezca el `guid` atributo en el nombre del `GuidSymbol` elemento que define el conjunto de comandos. Si el elemento de destino no forma parte del paquete, use el GUID para ese conjunto de comandos, tal y como se define en el archivo. Vsct correspondiente.  
  
   2. Establezca el `id` atributo para que coincida con el `id` atributo del menú o grupo de destino. Para obtener una lista de los menús y los grupos que se exponen en Visual Studio, vea [GUID e identificadores de los menús de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o [GUID e identificadores de las barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
   Si tiene un gran número de elementos de interfaz de usuario para colocar en el IDE, o si tiene elementos que deben aparecer en varios lugares, defina sus ubicaciones en el elemento [CommandPlacements](../../extensibility/commandplacements-element.md) , tal como se muestra en los pasos siguientes.  
  
##### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Para usar la colocación de comandos para colocar elementos de la interfaz de usuario en el IDE  
  
1. Después del elemento `Commands`, agregue un elemento `CommandPlacements`.  
  
2. En el `CommandPlacements` elemento, agregue un `CommandPlacement` elemento para cada menú, grupo o comando que se va a colocar.  
  
    Cada `CommandPlacement` elemento o `Parent` elemento coloca un menú, un grupo o un comando en una ubicación del IDE. Un elemento de la interfaz de usuario solo puede tener un elemento primario, pero puede tener varias ubicaciones de comandos. Para colocar un elemento de la interfaz de usuario en varias ubicaciones, agregue un `CommandPlacement` elemento para cada ubicación.  
  
3. Establezca los `guid` `id` atributos y de cada `CommandPlacement` elemento en el menú o grupo de hospedaje, del mismo modo que lo haría para un `Parent` elemento. También puede establecer el `priority` atributo para establecer la posición relativa del elemento de la interfaz de usuario.  
  
   Puede mezclar la selección de ubicación mediante el control parental y la ubicación del comando. Sin embargo, en el caso de conjuntos de comandos muy grandes, se recomienda usar solo la selección de ubicación del comando.  
  
### <a name="adding-specialized-behaviors"></a>Agregar comportamientos especializados  
 Puede usar elementos [CommandFlag](../../extensibility/command-flag-element.md) para modificar el comportamiento de los menús y comandos, por ejemplo, para cambiar su apariencia y visibilidad. También puede influir en el momento en que un comando esté visible mediante [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md), o bien agregar métodos abreviados de teclado mediante los [enlaces](../../extensibility/keybindings-element.md)de teclado. Ciertos tipos de menús y comandos ya tienen comportamientos especializados integrados.  
  
##### <a name="to-add-specialized-behaviors"></a>Para agregar comportamientos especializados  
  
1. Para hacer que un elemento de la interfaz de usuario solo esté visible en determinados contextos de la interfaz de usuario, por ejemplo, cuando se carga una solución, utilice restricciones de visibilidad.  
  
   1. Después del elemento `Commands`, agregue un elemento `VisibilityConstraints`.  
  
   2. Para cada elemento de la interfaz de usuario que se va a restringir, agregue un elemento [VisibilityItem](../../extensibility/visibilityitem-element.md) .  
  
   3. Para cada `VisibilityItem` elemento, establezca los `guid` `id` atributos y en el menú, grupo o comando y, a continuación, establezca el `context` atributo en el contexto de la interfaz de usuario que desee, tal como se define en la <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> clase. Para obtener más información, consulte [elemento VisibilityItem](../../extensibility/visibilityitem-element.md).  
  
2. Para establecer la visibilidad o la disponibilidad de un elemento de la interfaz de usuario en el código, use una o varias de las siguientes marcas de comando:  
  
   - DefaultDisabled  
  
   - DefaultInvisible  
  
   - DynamicItemStart  
  
   - DynamicVisibility  
  
   - NoShowOnMenuController  
  
   - NotInTBList  
  
     Para obtener más información, vea [elemento de marca de comandos](../../extensibility/command-flag-element.md).  
  
3. Para cambiar el modo en que aparece un elemento o cambiar su apariencia dinámicamente, use una o varias de las siguientes marcas de comando:  
  
   - AlwaysCreate  
  
   - CommandWellOnly  
  
   - DefaultDocked  
  
   - DontCache  
  
   - DynamicItemStart  
  
   - FixMenuController  
  
   - IconAndText  
  
   - PICT  
  
   - StretchHorizontally  
  
   - TextMenuUseButton  
  
   - Textchanges al  
  
   - TextOnly  
  
     Para obtener más información, vea [elemento de marca de comandos](../../extensibility/command-flag-element.md).  
  
4. Para cambiar el modo en que un elemento reacciona cuando recibe comandos, use una o varias de las siguientes marcas de comando:  
  
   - AllowParams  
  
   - CaseSensitive  
  
   - CommandWellOnly  
  
   - Activar  
  
   - NoAutoComplete  
  
   - NoButtonCustomize  
  
   - NoKeyCustomize  
  
   - NoToolbarClose  
  
   - Postexec  
  
   - RouteToDocs  
  
   - TextIsAnchorCommand  
  
     Para obtener más información, vea [elemento de marca de comandos](../../extensibility/command-flag-element.md).  
  
5. Para adjuntar un método abreviado de teclado dependiente del menú a un menú o un elemento de un menú, agregue un carácter de y comercial (' & ') en el `ButtonText` elemento para el menú o el elemento de menú. El carácter que sigue a la y comercial es el método abreviado de teclado activo cuando el menú primario está abierto.  
  
6. Para adjuntar un método abreviado de teclado independiente del menú a un comando, use [KeyBindings](../../extensibility/keybindings-element.md). Para obtener más información, vea [KeyBinding (elemento](../../extensibility/keybinding-element.md)).  
  
7. Para localizar el texto del menú, use el `LocCanonicalName` elemento. Para obtener más información, vea [Strings (elemento](../../extensibility/strings-element.md)).  
  
   Algunos tipos de menú y botón incluyen comportamientos especializados. En la tabla siguiente se describen algunos tipos de menús y botones especializados. Para otros tipos, vea las `types` descripciones de atributo en [elemento de menú](../../extensibility/menu-element.md), [elemento de botón](../../extensibility/button-element.md)y [elemento combinado](../../extensibility/combo-element.md).  
  
   Cuadro combinado  
   Un cuadro combinado es una lista desplegable que se puede usar en una barra de herramientas. Para agregar cuadros combinados a la interfaz de usuario, cree un elemento [Combo](../../extensibility/combos-element.md) en el `Commands` elemento. A continuación, agregue al `Combos` elemento un `Combo` elemento para cada cuadro combinado que se va a agregar. `Combo` los elementos tienen los mismos atributos y elementos secundarios que los `Button` elementos y también tienen `DefaultWidth` `idCommandList` atributos y. El `DefaultWidth` atributo establece el ancho en píxeles y el `idCommandList` atributo apunta a un identificador de comando que se usa para rellenar el cuadro combinado. Para obtener más información, vea la `Combo` documentación del elemento.  
  
   MenuController  
   Un controlador de menú es un botón que tiene una flecha al lado. Al hacer clic en la flecha, se abre una lista. Para agregar un controlador de menú a la interfaz de usuario, cree un `Menu` elemento y establezca su `type` atributo en **MenuController** o **MenuControllerLatched**, según el comportamiento que desee. Para rellenar un controlador de menú, establézcalo como elemento primario de un `Group` elemento. El controlador de menú mostrará todos los elementos secundarios de ese grupo en la lista desplegable.  
  
## <a name="see-also"></a>Consulte también  
 [Extensión de menús y comandos](../../extensibility/extending-menus-and-commands.md)   
 [Tabla de comandos de Visual Studio (. Archivos de Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)
