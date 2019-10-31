---
title: Creación. Archivos Vsct | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 82960de02c43a7c4002e189d573a914bb2a73f20
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186654"
---
# <a name="author-vsct-files"></a>Archivos Author. Vsct
En este documento se muestra cómo crear un archivo *. Vsct* para agregar elementos de menú, barras de herramientas y otros elementos de la interfaz de usuario (IU) al entorno de desarrollo integrado (IDE) de Visual Studio. Siga estos pasos al agregar elementos de interfaz de usuario a un paquete de Visual Studio (VSPackage) que todavía no tiene un archivo *. Vsct* .

 En el caso de los proyectos nuevos, se recomienda usar la plantilla de paquete de Visual Studio, ya que genera un archivo *. Vsct* que, en función de las selecciones, ya tiene los elementos necesarios para un comando de menú, una ventana de herramientas o un editor personalizado. Puede modificar este archivo *. Vsct* para cumplir los requisitos de su VSPackage. Para obtener más información sobre cómo modificar un archivo *. Vsct* , vea los ejemplos de los [menús y comandos de extensión](../../extensibility/extending-menus-and-commands.md).

## <a name="author-the-file"></a>Crear el archivo
 Cree un archivo *. Vsct* en estas fases: cree la estructura de archivos y recursos, declare los elementos de la interfaz de usuario, coloque los elementos de la interfaz de usuario en el IDE y agregue cualquier comportamiento especializado.

### <a name="file-structure"></a>Estructura de archivos
 La estructura básica de un archivo *. Vsct* es un elemento raíz [CommandTable](../../extensibility/commandtable-element.md) que contiene un elemento [Commands](../../extensibility/commands-element.md) y un elemento [Symbols](../../extensibility/symbols-element.md) .

#### <a name="to-create-the-file-structure"></a>Para crear la estructura de archivos

1. Agregue un archivo *. Vsct* al proyecto siguiendo los pasos descritos en [Cómo: crear un archivo. Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).

2. Agregue los espacios de nombres necesarios al elemento `CommandTable`, como se muestra en el ejemplo siguiente:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. En el elemento `CommandTable`, agregue un elemento `Commands` para hospedar todos los menús, barras de herramientas, grupos de comandos y comandos personalizados. Para que los elementos de la interfaz de usuario personalizados puedan cargarse, el elemento `Commands` debe tener su atributo `Package` establecido en el nombre del paquete.

     Después del elemento `Commands`, agregue un elemento `Symbols` para definir los GUID del paquete, así como los nombres y los identificadores de comando de los elementos de la interfaz de usuario.

### <a name="include-visual-studio-resources"></a>Incluir recursos de Visual Studio
 Use el elemento [extern](../../extensibility/extern-element.md) para tener acceso a los archivos que definen los comandos de Visual Studio y los menús necesarios para colocar los elementos de la interfaz de usuario en el IDE. Si va a utilizar comandos definidos fuera del paquete, use el elemento [UsedCommands](../../extensibility/usedcommands-element.md) para informar a Visual Studio.

#### <a name="to-include-visual-studio-resources"></a>Para incluir recursos de Visual Studio

1. En la parte superior del elemento `CommandTable`, agregue un elemento `Extern` para cada archivo externo al que se va a hacer referencia y establezca el atributo `href` en el nombre del archivo. Puede hacer referencia a los siguientes archivos de encabezado para tener acceso a los recursos de Visual Studio:

   - *Stdidcmd. h*: define los identificadores de todos los comandos expuestos por Visual Studio.

   - *Vsshlids. h*: contiene los identificadores de comando de los menús de Visual Studio.

2. Si el paquete llama a cualquier comando definido por Visual Studio u otros paquetes, agregue un elemento `UsedCommands` después del elemento `Commands`. Rellene este elemento con un elemento [UsedCommand](../../extensibility/usedcommand-element.md) para cada comando al que llame y que no forme parte del paquete. Establezca los atributos `guid` y `id` de los elementos `UsedCommand` en los valores GUID y ID de los comandos a los que se va a llamar.

   Para obtener más información sobre cómo buscar los GUID e identificadores de los comandos de Visual Studio, vea [GUID e identificadores de comandos de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Para llamar a comandos desde otros paquetes, use el GUID y el identificador del comando, tal como se define en el archivo *. Vsct* para esos paquetes.

### <a name="declare-ui-elements"></a>Declarar elementos de interfaz de usuario
 Declare todos los nuevos elementos de la interfaz de usuario en la sección `Symbols` del archivo *. Vsct* .

#### <a name="to-declare-ui-elements"></a>Para declarar elementos de la interfaz de usuario

1. En el elemento `Symbols`, agregue tres elementos [GuidSymbol](../../extensibility/guidsymbol-element.md) . Cada `GuidSymbol` elemento tiene un atributo `name` y un atributo `value`. Establezca el atributo `name` para que refleje el propósito del elemento. El atributo `value` toma un GUID. (Para generar un GUID, en el menú **herramientas** , seleccione **crear GUID**y, a continuación, seleccione **formato del registro**).

     El primer elemento `GuidSymbol` representa el paquete y normalmente no tiene elementos secundarios. El segundo elemento `GuidSymbol` representa el conjunto de comandos y contendrá todos los símbolos que definen los menús, los grupos y los comandos. El tercer elemento `GuidSymbol` representa el almacén de imágenes y contiene símbolos para todos los iconos de los comandos. Si no tiene comandos que usen iconos, puede omitir el tercer elemento de `GuidSymbol`.

2. En el elemento `GuidSymbol` que representa el conjunto de comandos, agregue uno o varios elementos [IDSymbol](../../extensibility/idsymbol-element.md) . Cada una de ellas representa un menú, una barra de herramientas, un grupo o un comando que se va a agregar a la interfaz de usuario.

     Para cada elemento `IDSymbol`, establezca el atributo `name` en el nombre que va a utilizar para hacer referencia al menú, grupo o comando correspondiente y, a continuación, establezca el elemento `value` en un número hexadecimal que representará su identificador de comando. Dos elementos `IDSymbol` que tienen el mismo elemento primario pueden tener el mismo valor.

3. Si alguno de los elementos de la interfaz de usuario requiere iconos, agregue un elemento `IDSymbol` para cada icono al elemento `GuidSymbol` que representa el almacén de imágenes.

### <a name="put-ui-elements-in-the-ide"></a>Colocar elementos de la interfaz de usuario en el IDE
 Los elementos [menus](../../extensibility/menus-element.md), [Groups](../../extensibility/groups-element.md)y [Buttons](../../extensibility/buttons-element.md) contienen las definiciones de todos los menús, grupos y comandos definidos en el paquete. Coloque estos menús, grupos y comandos en el IDE mediante el uso de un elemento [primario](../../extensibility/parent-element.md) , que forma parte de la definición del elemento de la interfaz de usuario o mediante el uso de un elemento [CommandPlacement](../../extensibility/commandplacement-element.md) que se define en otro lugar.

 Cada `Menu`, `Group`y `Button` elemento tiene un atributo `guid` y un atributo `id`. Establezca siempre el atributo `guid` para que coincida con el nombre del elemento `GuidSymbol` que representa el conjunto de comandos y establezca el atributo `id` en el nombre del elemento `IDSymbol` que representa el menú, el grupo o el comando en la sección `Symbols`.

#### <a name="to-define-ui-elements"></a>Para definir los elementos de la interfaz de usuario

1. Si va a definir nuevos menús, submenús, menús contextuales o barras de herramientas, agregue un elemento `Menus` al elemento `Commands`. A continuación, para cada menú que se va a crear, agregue un elemento de [menú](../../extensibility/menu-element.md) al elemento `Menus`.

    Establezca los atributos `guid` y `id` del elemento `Menu` y, a continuación, establezca el atributo `type` en el tipo de menú que desee. También puede establecer el atributo `priority` para establecer la posición relativa del menú en el grupo primario.

   > [!NOTE]
   > El atributo `priority` no se aplica a las barras de herramientas y los menús contextuales.

2. Todos los comandos del IDE de Visual Studio se deben hospedar en grupos de comandos, que son los elementos secundarios directos de los menús y las barras de herramientas. Si va a agregar nuevos menús o barras de herramientas al IDE, estos deben contener nuevos grupos de comandos. También puede agregar grupos de comandos a los menús y las barras de herramientas existentes para que pueda agrupar visualmente los comandos.

    Al agregar nuevos grupos de comandos, primero debe crear un elemento de `Groups` y, a continuación, agregarlo a un elemento de [Grupo](../../extensibility/group-element.md) para cada grupo de comandos.

    Establezca los atributos `guid` y `id` de cada elemento `Group` y, a continuación, establezca el atributo `priority` para establecer la posición relativa del grupo en el menú primario. Para obtener más información, vea [crear grupos reutilizables de botones](../../extensibility/creating-reusable-groups-of-buttons.md).

3. Si va a agregar nuevos comandos al IDE, agregue un elemento `Buttons` al elemento `Commands`. A continuación, para cada comando, agregue un elemento [botón](../../extensibility/button-element.md) al elemento `Buttons`.

   1. Establezca los atributos `guid` y `id` de cada elemento `Button` y, a continuación, establezca el atributo `type` en el tipo de botón que desee. También puede establecer el atributo `priority` para establecer la posición relativa del comando en el grupo primario.

       > [!NOTE]
       > Use `type="button"` para botones y comandos de menú estándar en las barras de herramientas.

   2. En el elemento `Button`, agregue un elemento [Strings](../../extensibility/strings-element.md) que contenga un elemento [ButtonText](../../extensibility/buttontext-element.md) y un elemento [CommandName](../../extensibility/commandname-element.md) . El elemento `ButtonText` proporciona la etiqueta de texto de un elemento de menú o la información sobre herramientas para un botón de la barra de herramientas. El elemento `CommandName` proporciona el nombre del comando que se va a usar en el cuadro de comandos.

   3. Si el comando va a tener un icono, cree un elemento [Icon](../../extensibility/icon-element.md) en el elemento `Button` y establezca sus atributos `guid` y `id` en el elemento `Bitmap` del icono.

       > [!NOTE]
       > Los botones de la barra de herramientas deben tener iconos.

   Para obtener más información, consulte [MenuCommands frente a OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

4. Si alguno de los comandos requiere iconos, agregue un elemento [bitmaps](../../extensibility/bitmaps-element.md) al elemento `Commands`. A continuación, para cada icono, agregue un elemento [Bitmap](../../extensibility/bitmap-element.md) al elemento `Bitmaps`. Aquí es donde se especifica la ubicación del recurso de mapa de bits. Para obtener más información, vea [Agregar iconos a comandos de menú](../../extensibility/adding-icons-to-menu-commands.md).

   Puede confiar en la estructura de control parental para colocar correctamente la mayoría de los menús, grupos y comandos. En el caso de conjuntos de comandos muy grandes, o cuando un menú, un grupo o un comando deben aparecer en varios lugares, se recomienda especificar la ubicación del comando.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Basarse en el control parental para colocar elementos de la interfaz de usuario en el IDE

1. En el caso de la protección típica, cree un elemento `Parent` en cada `Menu`, `Group`y `Command` elemento que se define en el paquete.

    El destino del elemento `Parent` es el menú o grupo que contendrá el menú, el grupo o el comando.

   1. Establezca el atributo `guid` en el nombre del elemento `GuidSymbol` que define el conjunto de comandos. Si el elemento de destino no forma parte del paquete, use el GUID para ese conjunto de comandos, tal y como se define en el archivo *. Vsct* correspondiente.

   2. Establezca el atributo `id` para que coincida con el atributo `id` del menú o grupo de destino. Para obtener una lista de los menús y los grupos que se exponen en Visual Studio, vea [GUID e identificadores de los menús de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o [GUID e identificadores de las barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   Si tiene un gran número de elementos de interfaz de usuario para colocar en el IDE, o si tiene elementos que deben aparecer en varios lugares, defina sus ubicaciones en el elemento [CommandPlacements](../../extensibility/commandplacements-element.md) , tal como se muestra en los pasos siguientes.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Para usar la colocación de comandos para colocar elementos de la interfaz de usuario en el IDE

1. Después del elemento `Commands`, agregue un elemento `CommandPlacements`.

2. En el elemento `CommandPlacements`, agregue un elemento `CommandPlacement` para cada menú, grupo o comando que se va a colocar.

    Cada `CommandPlacement` elemento o elemento `Parent` coloca un menú, un grupo o un comando en una ubicación del IDE. Un elemento de la interfaz de usuario solo puede tener un elemento primario, pero puede tener varias ubicaciones de comandos. Para colocar un elemento de la interfaz de usuario en varias ubicaciones, agregue un elemento `CommandPlacement` para cada ubicación.

3. Establezca los atributos `guid` y `id` de cada elemento `CommandPlacement` en el menú o grupo de hospedaje, de la misma forma que lo haría para un elemento de `Parent`. También puede establecer el atributo `priority` para establecer la posición relativa del elemento de la interfaz de usuario.

   Puede mezclar la selección de ubicación mediante el control parental y la ubicación del comando. Sin embargo, en el caso de conjuntos de comandos muy grandes, se recomienda usar solo la selección de ubicación del comando.

### <a name="add-specialized-behaviors"></a>Agregar comportamientos especializados
 Puede usar el elemento [CommandFlag](../../extensibility/command-flag-element.md) para modificar el comportamiento de los menús y comandos, por ejemplo, para cambiar su apariencia y visibilidad. También puede influir en el momento en que un comando esté visible mediante el elemento [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) o agregar métodos abreviados de teclado mediante el elemento [KeyBindings](../../extensibility/keybindings-element.md) . Ciertos tipos de menús y comandos ya tienen comportamientos especializados integrados.

#### <a name="to-add-specialized-behaviors"></a>Para agregar comportamientos especializados

1. Para hacer que un elemento de la interfaz de usuario solo esté visible en determinados contextos de la interfaz de usuario, por ejemplo, cuando se carga una solución, utilice restricciones de visibilidad.

   1. Después del elemento `Commands`, agregue un elemento `VisibilityConstraints`.

   2. Para cada elemento de la interfaz de usuario que se va a restringir, agregue un elemento [VisibilityItem](../../extensibility/visibilityitem-element.md) .

   3. Para cada elemento `VisibilityItem`, establezca los atributos `guid` y `id` en el menú, grupo o comando y, a continuación, establezca el atributo `context` en el contexto de la interfaz de usuario que desee, tal como se define en la clase <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>.

2. Para establecer la visibilidad o la disponibilidad de un elemento de la interfaz de usuario en el código, use una o varias de las siguientes marcas de comando:

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   Para obtener más información, vea el elemento [CommandFlag](../../extensibility/command-flag-element.md) .

3. Para cambiar el modo en que aparece un elemento o cambiar su apariencia dinámicamente, use una o varias de las siguientes marcas de comando:

   - `AlwaysCreate`

   - `CommandWellOnly`

   - `DefaultDocked`

   - `DontCache`

   - `DynamicItemStart`

   - `FixMenuController`

   - `IconAndText`

   - `Pict`

   - `StretchHorizontally`

   - `TextMenuUseButton`

   - `TextChanges`

   - `TextOnly`

   Para obtener más información, vea el elemento [CommandFlag](../../extensibility/command-flag-element.md) .

4. Para cambiar el modo en que un elemento reacciona cuando recibe comandos, use una o varias de las siguientes marcas de comando:

   - `AllowParams`

   - `CaseSensitive`

   - `CommandWellOnly`

   - `FilterKeys`

   - `NoAutoComplete`

   - `NoButtonCustomize`

   - `NoKeyCustomize`

   - `NoToolbarClose`

   - `PostExec`

   - `RouteToDocs`

   - `TextIsAnchorCommand`

   Para obtener más información, vea el elemento [CommandFlag](../../extensibility/command-flag-element.md) .

5. Para adjuntar un método abreviado de teclado dependiente del menú a un menú o un elemento de un menú, agregue un carácter de y comercial (&) en el elemento `ButtonText` para el menú o el elemento de menú. El carácter que sigue a la y comercial es el método abreviado de teclado activo cuando el menú primario está abierto.

6. Para adjuntar un método abreviado de teclado independiente del menú a un comando, utilice el elemento [KeyBindings](../../extensibility/keybindings-element.md) . Para obtener más información, vea el elemento [KeyBinding](../../extensibility/keybinding-element.md) .

7. Para localizar el texto del menú, use el elemento `LocCanonicalName`. Para obtener más información, vea el elemento [Strings](../../extensibility/strings-element.md) .

   Algunos tipos de menú y botón incluyen comportamientos especializados. En la lista siguiente se describen algunos tipos de menús y botones especializados. Para otros tipos, vea las descripciones de los atributos de `types` en el [menú](../../extensibility/menu-element.md), [botón](../../extensibility/button-element.md)y elementos [combinados](../../extensibility/combo-element.md) .

   - Cuadro combinado: un cuadro combinado es una lista desplegable que se puede usar en una barra de herramientas. Para agregar cuadros combinados a la interfaz de usuario, cree un elemento [Combo](../../extensibility/combos-element.md) en el elemento `Commands`. A continuación, agregue al elemento `Combos` un elemento `Combo` para cada cuadro combinado que se va a agregar. `Combo` elementos tienen los mismos atributos y elementos secundarios que los elementos `Button` y también tienen atributos `DefaultWidth` y `idCommandList`. El atributo `DefaultWidth` establece el ancho en píxeles y el atributo `idCommandList` apunta a un identificador de comando que se usa para rellenar el cuadro combinado.

   - Controlador de menú: un controlador de menú es un botón que tiene una flecha al lado. Al hacer clic en la flecha, se abre una lista. Para agregar un controlador de menú a la interfaz de usuario, cree un `Menu` elemento y establezca su `type` atributo en `MenuController` o `MenuControllerLatched`, según el comportamiento que desee. Para rellenar un controlador de menú, establézcalo como elemento primario de un elemento `Group`. El controlador de menú mostrará todos los elementos secundarios de ese grupo en la lista desplegable.

## <a name="see-also"></a>Vea también
- [Extender menús y comandos](../../extensibility/extending-menus-and-commands.md)
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)