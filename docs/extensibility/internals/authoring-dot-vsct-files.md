---
title: Edición. Archivos vsct ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfa276d04e2d312d7ff00b1e9bc0015beb1e254e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709994"
---
# <a name="author-vsct-files"></a>Crear archivos .vsct
En este documento se muestra cómo crear un archivo *.vsct* para agregar elementos de menú, barras de herramientas y otros elementos de interfaz de usuario (UI) al entorno de desarrollo integrado (IDE) de Visual Studio. Siga estos pasos al agregar elementos de interfaz de usuario a un paquete de Visual Studio (VSPackage) que aún no tiene un archivo *.vsct.*

 Para los nuevos proyectos, se recomienda usar la plantilla de paquete de Visual Studio porque genera un archivo *.vsct* que, dependiendo de las selecciones, ya tiene los elementos necesarios para un comando de menú, una ventana de herramientas o un editor personalizado. Puede modificar este archivo *.vsct* para cumplir los requisitos de su VSPackage. Para obtener más información sobre cómo modificar un archivo *.vsct,* consulte los ejemplos de [Extender menús y comandos](../../extensibility/extending-menus-and-commands.md).

## <a name="author-the-file"></a>Crear el archivo
 Crear un archivo *.vsct* en estas fases: cree la estructura de archivos y recursos, declare los elementos de la interfaz de usuario, coloque los elementos de la interfaz de usuario en el IDE y agregue comportamientos especializados.

### <a name="file-structure"></a>Estructura de archivos
 La estructura básica de un archivo *.vsct* es un elemento raíz [CommandTable](../../extensibility/commandtable-element.md) que contiene un elemento [Commands](../../extensibility/commands-element.md) y un elemento [Symbols.](../../extensibility/symbols-element.md)

#### <a name="to-create-the-file-structure"></a>Para crear la estructura de archivos

1. Agregue un archivo *.vsct* al proyecto siguiendo los pasos descritos en [Cómo: Crear un archivo .vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).

2. Agregue los espacios de `CommandTable` nombres necesarios al elemento, como se muestra en el ejemplo siguiente:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. En `CommandTable` el elemento, `Commands` agregue un elemento para hospedar todos los menús personalizados, barras de herramientas, grupos de comandos y comandos. Para que los elementos de `Commands` interfaz `Package` de usuario personalizados se puedan cargar, el elemento debe tener su atributo establecido en el nombre del paquete.

     Después `Commands` del elemento, agregue un `Symbols` elemento para definir los GUID para el paquete y los nombres y los id de comando para los elementos de la interfaz de usuario.

### <a name="include-visual-studio-resources"></a>Incluir recursos de Visual Studio
 Use el elemento [Extern](../../extensibility/extern-element.md) para tener acceso a los archivos que definen los comandos de Visual Studio y los menús necesarios para colocar los elementos de interfaz de usuario en el IDE. Si va a usar comandos definidos fuera del paquete, use el elemento [UsedCommands](../../extensibility/usedcommands-element.md) para informar a Visual Studio.

#### <a name="to-include-visual-studio-resources"></a>Para incluir recursos de Visual Studio

1. En la parte `CommandTable` superior del `Extern` elemento, agregue un elemento para `href` cada archivo externo al que se haga referencia y establezca el atributo en el nombre del archivo. Puede hacer referencia a los siguientes archivos de encabezado para tener acceso a los recursos de Visual Studio:

   - *Stdidcmd.h*: Define los iDs para todos los comandos expuestos por Visual Studio.

   - *Vsshlids.h*: Contiene los elementos de comando de los menús de Visual Studio.

2. Si el paquete llama a los comandos definidos por `UsedCommands` Visual `Commands` Studio o por otros paquetes, agregue un elemento después del elemento. Rellene este elemento con un [elemento UsedCommand](../../extensibility/usedcommand-element.md) para cada comando al que llame que no forme parte del paquete. Establezca `guid` los `id` atributos `UsedCommand` y de los elementos en los valores GUID e ID de los comandos que se llamarán.

   Para obtener más información acerca de cómo buscar los GUID y los GUID de los comandos de Visual Studio, vea [GUID e iD de comandos de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Para llamar a comandos de otros paquetes, use el GUID y el identificador del comando tal como se define en el archivo *.vsct* para esos paquetes.

### <a name="declare-ui-elements"></a>Declarar elementos de interfaz de usuario
 Declare todos los nuevos `Symbols` elementos de la interfaz de usuario en la sección del archivo *.vsct.*

#### <a name="to-declare-ui-elements"></a>Para declarar elementos de interfaz de usuario

1. En `Symbols` el elemento, agregue tres [GuidSymbol](../../extensibility/guidsymbol-element.md) elementos. Cada `GuidSymbol` elemento `name` tiene un `value` atributo y un atributo. Establezca `name` el atributo para que refleje el propósito del elemento. El `value` atributo toma un GUID. (Para generar un GUID, en el menú **Herramientas,** seleccione **Crear GUID**y, a continuación, seleccione Formato **del Registro**.)

     El `GuidSymbol` primer elemento representa el paquete y normalmente no tiene elementos secundarios. El `GuidSymbol` segundo elemento representa el conjunto de comandos y contendrá todos los símbolos que definen los menús, grupos y comandos. El `GuidSymbol` tercer elemento representa el almacén de imágenes y contiene símbolos para todos los iconos de los comandos. Si no tiene comandos que utilicen `GuidSymbol` iconos, puede omitir el tercer elemento.

2. En `GuidSymbol` el elemento que representa el conjunto de comandos, agregue uno o varios [elementos IDSymbol.](../../extensibility/idsymbol-element.md) Cada uno de ellos representa un menú, barra de herramientas, grupo o comando que se agrega a la interfaz de usuario.

     Para `IDSymbol` cada elemento, `name` establezca el atributo en el nombre que utilizará para hacer referencia `value` al menú, grupo o comando correspondiente y, a continuación, establezca el elemento en un número hexadecimal que representará su identificador de comando. No `IDSymbol` hay dos elementos que tengan el mismo elemento primario puede tener el mismo valor.

3. Si alguno de los elementos `IDSymbol` de la interfaz `GuidSymbol` de usuario requiere iconos, agregue un elemento para cada icono al elemento que representa el almacén de imágenes.

### <a name="put-ui-elements-in-the-ide"></a>Colocar elementos de interfaz de usuario en el IDE
 Los [elementos Menus](../../extensibility/menus-element.md), [Groups](../../extensibility/groups-element.md)y [Buttons](../../extensibility/buttons-element.md) contienen las definiciones de todos los menús, grupos y comandos definidos en el paquete. Coloque estos menús, grupos y comandos en el IDE mediante un [elemento Parent,](../../extensibility/parent-element.md) que forma parte de la definición del elemento UI, o mediante un elemento [CommandPlacement](../../extensibility/commandplacement-element.md) que se define en otro lugar.

 Cada `Menu` `Group`, `Button` , y `guid` elemento `id` tiene un atributo y un atributo. Establezca siempre `guid` el atributo para `GuidSymbol` que coincida con el nombre del `id` elemento que representa `IDSymbol` el conjunto de comandos y establezca `Symbols` el atributo en el nombre del elemento que representa el menú, grupo o comando de la sección.

#### <a name="to-define-ui-elements"></a>Para definir elementos de interfaz de usuario

1. Si está definiendo nuevos menús, submenús, menús `Menus` contextuales `Commands` o barras de herramientas, agregue un elemento al elemento. A continuación, para cada menú que se `Menus` va a crear, agregue un elemento [Menu](../../extensibility/menu-element.md) al elemento.

    Establezca `guid` los `id` atributos `Menu` y del elemento `type` y, a continuación, establezca el atributo en el tipo de menú que desee. También puede establecer `priority` el atributo para establecer la posición relativa del menú en el grupo primario.

   > [!NOTE]
   > El `priority` atributo no se aplica a las barras de herramientas y los menús contextuales.

2. Todos los comandos del IDE de Visual Studio deben hospedarse en grupos de comandos, que son los elementos secundarios directos de los menús y las barras de herramientas. Si va a agregar nuevos menús o barras de herramientas al IDE, estos deben contener nuevos grupos de comandos. También puede agregar grupos de comandos a los menús y barras de herramientas existentes para que pueda agrupar visualmente los comandos.

    Al agregar nuevos grupos de comandos, primero debe crear un `Groups` elemento y, a continuación, agregarle un elemento [Group](../../extensibility/group-element.md) para cada grupo de comandos.

    Establezca `guid` los `id` atributos `Group` y de cada `priority` elemento y, a continuación, establezca el atributo para establecer la posición relativa del grupo en el menú primario. Para obtener más información, consulte [Crear grupos de botones reutilizables.](../../extensibility/creating-reusable-groups-of-buttons.md)

3. Si va a agregar nuevos comandos `Buttons` al IDE, agregue un elemento al `Commands` elemento. A continuación, para cada comando, `Buttons` agregue un elemento [Button](../../extensibility/button-element.md) al elemento.

   1. Establezca `guid` los `id` atributos `Button` y de cada `type` elemento y, a continuación, establezca el atributo en el tipo de botón que desee. También puede establecer `priority` el atributo para establecer la posición relativa del comando en el grupo primario.

       > [!NOTE]
       > Se `type="button"` utiliza para los comandos de menú estándar y los botones de las barras de herramientas.

   2. En `Button` el elemento, agregue un [elemento Strings](../../extensibility/strings-element.md) que contenga un elemento [ButtonText](../../extensibility/buttontext-element.md) y un elemento [CommandName.](../../extensibility/commandname-element.md) El `ButtonText` elemento proporciona la etiqueta de texto para un elemento de menú o la información sobre herramientas para un botón de barra de herramientas. El `CommandName` elemento proporciona el nombre del comando que se va a utilizar en el pozo de comandos.

   3. Si el comando tendrá un icono, cree un `Button` elemento [Icon](../../extensibility/icon-element.md) `id` en el `Bitmap` elemento y establezca sus `guid` atributos y sus atributos en el elemento del icono.

       > [!NOTE]
       > Los botones de la barra de herramientas deben tener iconos.

   Para obtener más información, vea [MenuCommands vs OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

4. Si alguno de los comandos requiere iconos, `Commands` agregue un elemento [Bitmaps](../../extensibility/bitmaps-element.md) al elemento. A continuación, para cada [Bitmap](../../extensibility/bitmap-element.md) icono, agregue `Bitmaps` un elemento Bitmap al elemento. Aquí es donde se especifica la ubicación del recurso de mapa de bits. Para obtener más información, consulte [Agregar iconos a los comandos](../../extensibility/adding-icons-to-menu-commands.md)de menú .

   Puede confiar en la estructura de crianza para colocar correctamente la mayoría de los menús, grupos y comandos. Para conjuntos de comandos muy grandes, o cuando un menú, grupo o comando debe aparecer en varios lugares, se recomienda especificar la colocación del comando.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Confiar en la crianza para colocar elementos de interfaz de usuario en el IDE

1. Para la crianza típica, `Parent` cree `Menu` `Group`un `Command` elemento en cada , , y elemento que se define en el paquete.

    El destino `Parent` del elemento es el menú o grupo que contendrá el menú, grupo o comando.

   1. Establezca `guid` el atributo en `GuidSymbol` el nombre del elemento que define el conjunto de comandos. Si el elemento de destino no forma parte del paquete, utilice el guid para ese conjunto de comandos, tal como se define en el archivo *.vsct* correspondiente.

   2. Establezca `id` el atributo `id` para que coincida con el atributo del menú o grupo de destino. Para obtener una lista de los menús y grupos expuestos por Visual Studio, vea [GUID e iD de menús](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) de Visual Studio o [GUID e iDs de barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   Si tiene un gran número de elementos de interfaz de usuario para colocar en el IDE, o si tiene elementos que deben aparecer en varios lugares, defina sus ubicaciones en el [Elemento CommandPlacements,](../../extensibility/commandplacements-element.md) como se muestra en los pasos siguientes.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Para usar la colocación de comandos para colocar elementos de interfaz de usuario en el IDE

1. Después del elemento `Commands`, agregue un elemento `CommandPlacements`.

2. En `CommandPlacements` el elemento, `CommandPlacement` agregue un elemento para cada menú, grupo o comando que se va a colocar.

    Cada `CommandPlacement` elemento `Parent` o elemento coloca un menú, grupo o comando en una ubicación IDE. Un elemento de interfaz de usuario solo puede tener un elemento primario, pero puede tener varias ubicaciones de comandos. Para colocar un elemento de interfaz de usuario en varias ubicaciones, agregue un `CommandPlacement` elemento para cada ubicación.

3. Establezca `guid` los `id` atributos `CommandPlacement` y de cada elemento en el menú `Parent` o grupo de hospedaje, tal como lo haría para un elemento. También puede establecer `priority` el atributo para establecer la posición relativa del elemento de interfaz de usuario.

   Puede mezclar la ubicación mediante la colocación de la crianza y la colocación de comandos. Sin embargo, para conjuntos de comandos muy grandes, se recomienda utilizar solo la colocación de comandos.

### <a name="add-specialized-behaviors"></a>Añadir comportamientos especializados
 Puede utilizar el elemento [CommandFlag](../../extensibility/command-flag-element.md) para modificar el comportamiento de los menús y comandos, por ejemplo, para cambiar su apariencia y visibilidad. También puede afectar cuando un comando está visible mediante el [elemento VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) o agregar métodos abreviados de teclado mediante el elemento [KeyBindings.](../../extensibility/keybindings-element.md) Ciertos tipos de menús y comandos ya tienen comportamientos especializados integrados.

#### <a name="to-add-specialized-behaviors"></a>Para agregar comportamientos especializados

1. Para que un elemento de interfaz de usuario sea visible solo en determinados contextos de interfaz de usuario, por ejemplo, cuando se carga una solución, use restricciones de visibilidad.

   1. Después del elemento `Commands`, agregue un elemento `VisibilityConstraints`.

   2. Para que cada elemento de interfaz de usuario se restrinja, agregue un elemento [VisibilityItem.](../../extensibility/visibilityitem-element.md)

   3. Para `VisibilityItem` cada elemento, `guid` `id` establezca los atributos y en el menú, grupo o comando y, a continuación, establezca el `context` atributo en el contexto de interfaz de usuario que desee, tal como se define en la <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> clase.

2. Para establecer la visibilidad o la disponibilidad de un elemento de interfaz de usuario en el código, utilice uno o varios de los siguientes indicadores de comando:

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   Para obtener más información, vea el [elemento CommandFlag.](../../extensibility/command-flag-element.md)

3. Para cambiar la forma en que aparece un elemento o cambiar su apariencia dinámicamente, utilice uno o varios de los siguientes indicadores de comando:

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

   Para obtener más información, vea el [elemento CommandFlag.](../../extensibility/command-flag-element.md)

4. Para cambiar cómo reacciona un elemento cuando recibe comandos, utilice uno o varios de los siguientes indicadores de comando:

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

   Para obtener más información, vea el [elemento CommandFlag.](../../extensibility/command-flag-element.md)

5. Para adjuntar un método abreviado de teclado dependiente del menú a un menú o un `ButtonText` elemento de un menú, agregue un carácter de y comercial (&) en el elemento del menú o elemento de menú. El carácter que sigue a la y comosigue es el método abreviado de teclado activo cuando el menú principal está abierto.

6. Para asociar un método abreviado de teclado independiente del menú a un comando, utilice el [KeyBindings](../../extensibility/keybindings-element.md) elemento. Para obtener más información, vea el [KeyBinding](../../extensibility/keybinding-element.md) elemento.

7. Para localizar el texto `LocCanonicalName` del menú, utilice el elemento. Para obtener más información, consulte el [strings](../../extensibility/strings-element.md) elemento.

   Algunos tipos de menús y botones incluyen comportamientos especializados. En la lista siguiente se describen algunos tipos de menús y botones especializados. Para otros tipos, `types` consulte las descripciones de atributos en los elementos [Menu](../../extensibility/menu-element.md), [Button](../../extensibility/button-element.md)y [Combo.](../../extensibility/combo-element.md)

   - Cuadro combinado: un cuadro combinado es una lista desplegable que se puede utilizar en una barra de herramientas. Para agregar cuadros combinados a la interfaz de usuario, cree un [combos](../../extensibility/combos-element.md) elemento en el `Commands` elemento. A continuación, `Combos` agregue `Combo` al elemento un elemento para cada cuadro combinado que desee agregar. `Combo`los elementos tienen los `Button` mismos `DefaultWidth` atributos y elementos secundarios que los elementos y también tienen y `idCommandList` atributos. El `DefaultWidth` atributo establece el ancho `idCommandList` en píxeles y el atributo apunta a un identificador de comando que se utiliza para rellenar el cuadro combinado.

   - Controlador de menú: Un controlador de menú es un botón que tiene una flecha junto a él. Al hacer clic en la flecha se abre una lista. Para agregar un controlador de menú `Menu` a la `type` interfaz de usuario, cree un elemento y establezca su atributo en `MenuController` o `MenuControllerLatched`, dependiendo del comportamiento que desee. Para rellenar un controlador de menú, `Group` establézcalo como el elemento primario de un elemento. El controlador de menú mostrará todos los elementos secundarios de ese grupo en su lista desplegable.

## <a name="see-also"></a>Vea también
- [Extender menús y comandos](../../extensibility/extending-menus-and-commands.md)
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referencia de esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)
