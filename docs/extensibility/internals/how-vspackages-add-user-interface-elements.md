---
title: Cómo agrega VSPackages los elementos de la interfaz de usuario | Microsoft Docs
description: Obtenga información sobre cómo los paquetes de interfaz de usuario (UI) de Visual Studio, como los menús, las barras de herramientas y las ventanas de herramientas, se agregan a Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fc9e80f549a5bf8cbf151ee224a9f503470a90de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934134"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Cómo agrega VSPackages los elementos de la interfaz de usuario
Un VSPackage puede agregar elementos de interfaz de usuario (IU), por ejemplo, menús, barras de herramientas y ventanas de herramientas, a Visual Studio por medio del archivo *. Vsct* .

Puede encontrar directrices de diseño para elementos de la interfaz de usuario en instrucciones para la [experiencia del usuario de Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="the-visual-studio-command-table-architecture"></a>Arquitectura de la tabla de comandos de Visual Studio
Como se indicó, la arquitectura de la tabla de comandos admite los principios arquitectónicos anteriores. Los principios subyacentes a las abstracciones, estructuras de datos y herramientas de la arquitectura de la tabla de comandos son los siguientes:

- Hay tres tipos básicos de elementos: menús, comandos y grupos. Los menús se pueden exponer en la interfaz de usuario como menús, submenús, barras de herramientas o ventanas de herramientas. Los comandos son procedimientos que el usuario puede ejecutar en el IDE y se pueden exponer como elementos de menú, botones, cuadros de lista u otros controles. Los grupos son contenedores para menús y comandos.

- Cada elemento se especifica mediante una definición que describe el elemento, su prioridad relativa a otros elementos y las marcas que modifican su comportamiento.

- Cada elemento tiene una posición que describe el elemento primario del elemento. Un elemento puede tener varios elementos primarios, por lo que puede aparecer en varias ubicaciones en la interfaz de usuario.

Cada comando debe tener un grupo como primario, incluso si es el único elemento secundario de ese grupo. Cada menú estándar también debe tener un grupo primario. Las barras de herramientas y las ventanas de herramientas actúan como sus propios elementos primarios. Un grupo puede tener como su elemento primario la barra de menús principal de Visual Studio, o cualquier menú, barra de herramientas o ventana de herramientas.

### <a name="how-items-are-defined"></a>Cómo se definen los elementos
Se da formato A un archivo *. Vsct* en XML. Define los elementos de la interfaz de usuario para un paquete y determina dónde aparecen esos elementos en el IDE. Cada menú, grupo o comando del paquete se asigna primero a un GUID y un identificador en la `Symbols` sección. A lo largo del resto del archivo *. Vsct* , cada menú, comando y grupo se identifica mediante su combinación GUID y identificador. En el ejemplo siguiente se muestra una `Symbols` sección típica generada por la plantilla de paquete de Visual Studio cuando se selecciona un **comando de menú** en la plantilla.

```xml
<Symbols>
  <!-- This is the package guid. -->
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />

  <!-- This is the guid used to group the menu commands together -->
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
  </GuidSymbol>

  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}">
    <IDSymbol name="bmpPic1" value="1" />
    <IDSymbol name="bmpPic2" value="2" />
    <IDSymbol name="bmpPicSearch" value="3" />
    <IDSymbol name="bmpPicX" value="4" />
    <IDSymbol name="bmpPicArrows" value="5" />
  </GuidSymbol>
</Symbols>
```

El elemento de nivel superior de la `Symbols` sección es el [elemento GuidSymbol](../../extensibility/guidsymbol-element.md). `GuidSymbol` los elementos asignan nombres a los GUID que usa el IDE para identificar los paquetes y sus partes componentes.

> [!NOTE]
> La plantilla de paquete de Visual Studio genera automáticamente los GUID. También puede crear un GUID único haciendo clic en **crear GUID** en el menú **herramientas** .

El primer `GuidSymbol` elemento, `guid<PackageName>Pkg` , es el GUID del propio paquete. Este es el GUID que usa Visual Studio para cargar el paquete. Normalmente, no tiene elementos secundarios.

Por Convención, los menús y los comandos se agrupan bajo un segundo `GuidSymbol` elemento, `guid<PackageName>CmdSet` , y los mapas de bits están bajo un tercer `GuidSymbol` elemento, `guidImages` . No es necesario seguir esta Convención, pero cada menú, grupo, comando y mapa de bits debe ser un elemento secundario de un `GuidSymbol` elemento.

En el segundo `GuidSymbol` elemento, que representa el conjunto de comandos de paquete, son varios `IDSymbol` elementos. Cada [elemento IDSymbol](../../extensibility/idsymbol-element.md) asigna un nombre a un valor numérico y puede representar un menú, grupo o comando que forma parte del conjunto de comandos. Los `IDSymbol` elementos del tercer `GuidSymbol` elemento representan los mapas de bits que se pueden usar como iconos para los comandos. Dado que los pares GUID/identificador deben ser únicos en una aplicación, dos elementos secundarios del mismo `GuidSymbol` elemento pueden tener el mismo valor.

### <a name="menus-groups-and-commands"></a>Menús, grupos y comandos
Cuando un menú, grupo o comando tiene un GUID y un identificador, se pueden agregar al IDE. Cada elemento de la interfaz de usuario debe tener lo siguiente:

- `guid`Atributo que coincide con el nombre del `GuidSymbol` elemento en el que se define el elemento de la interfaz de usuario.

- `id`Atributo que coincide con el nombre del elemento asociado `IDSymbol` .

Juntos, los `guid` `id` atributos y componen la *firma* del elemento de la interfaz de usuario.

- `priority`Atributo que determina la posición del elemento de la interfaz de usuario en el menú o grupo primario.

- [Elemento primario](../../extensibility/parent-element.md) que tiene `guid` `id` los atributos y que especifican la firma del menú o grupo primario.

#### <a name="menus"></a>Menús
Cada menú se define como un [elemento de menú](../../extensibility/menu-element.md) en la `Menus` sección. Los menús deben `guid` tener `id` `priority` los atributos, y, y un `Parent` elemento, así como los siguientes atributos y elementos secundarios adicionales:

- `type`Atributo que especifica si el menú debe aparecer en el IDE como un tipo de menú o como una barra de herramientas.

- Un [elemento Strings](../../extensibility/strings-element.md) que contiene un [elemento ButtonText](../../extensibility/buttontext-element.md), que especifica el título del menú en el IDE y un [elemento CommandName](../../extensibility/commandname-element.md), que especifica el nombre que se usa en la ventana de **comandos** para tener acceso al menú.

- Marcas opcionales. Un [elemento CommandFlag](../../extensibility/command-flag-element.md) puede aparecer en una definición de menú para cambiar su apariencia o comportamiento en el IDE.

Cada `Menu` elemento debe tener un grupo como su elemento primario, a menos que sea un elemento acoplable como, por ejemplo, una barra de herramientas. Un menú acoplable es su propio elemento primario. Para obtener más información sobre los menús y los valores para el `type` atributo, vea la documentación del [elemento de menú](../../extensibility/menu-element.md) .

En el ejemplo siguiente se muestra un menú que aparece en la barra de menús de Visual Studio, junto al menú **herramientas** .

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
  <Parent guid="guidSHLMainMenu" id="IDG_VS_MM_TOOLSADDINS" />
  <Strings>
    <ButtonText>TestMenu</ButtonText>
    <CommandName>TestMenu</CommandName>
  </Strings>
</Menu>
```

#### <a name="groups"></a>Grupos
Un grupo es un elemento que se define en la `Groups` sección del archivo *. Vsct* . Los grupos son simplemente contenedores. No aparecen en el IDE excepto como una línea divisoria en un menú. Por lo tanto, un [elemento Group](../../extensibility/group-element.md) solo se define por su firma, prioridad y elemento primario.

Un grupo puede tener un menú, otro grupo o él mismo como primario. Sin embargo, el elemento primario suele ser un menú o una barra de herramientas. El menú del ejemplo anterior es un elemento secundario del `IDG_VS_MM_TOOLSADDINS` grupo y ese grupo es un elemento secundario de la barra de menús de Visual Studio. El grupo del ejemplo siguiente es un elemento secundario del menú en el ejemplo anterior.

```xml
<Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" priority="0x0600">
  <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
</Group>
```

Dado que forma parte de un menú, este grupo normalmente contendría comandos. Sin embargo, también podría contener otros menús. Así es cómo se definen los submenús, tal y como se muestra en el ejemplo siguiente.

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu" priority="0x0100" type="Menu">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>
  <Strings>
    <ButtonText>Sub Menu</ButtonText>
    <CommandName>Sub Menu</CommandName>
  </Strings>
</Menu>
```

#### <a name="commands"></a>Comandos:
Un comando que se proporciona al IDE se define como un elemento de [botón](../../extensibility/button-element.md) o como un [elemento combinado](../../extensibility/combo-element.md). Para que aparezca en un menú o una barra de herramientas, el comando debe tener un grupo como su elemento primario.

##### <a name="buttons"></a>Botones
Los botones se definen en la `Buttons` sección. Cualquier elemento de menú, botón u otro elemento en el que un usuario haga clic para ejecutar un solo comando se considera un botón. Algunos tipos de botón también pueden incluir funcionalidad de lista. Los botones tienen los mismos atributos obligatorios y opcionales que los menús, y también pueden tener un [elemento Icon](../../extensibility/icon-element.md) que especifique el GUID y el identificador del mapa de bits que representa el botón en el IDE. Para obtener más información sobre los botones y sus atributos, vea la documentación del [elemento Buttons](../../extensibility/buttons-element.md) .

El botón en el ejemplo siguiente es un elemento secundario del grupo en el ejemplo anterior y aparecería en el IDE como un elemento de menú en el menú primario de ese grupo.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>
```

##### <a name="combos"></a>Cuadros combinados
Los combinados se definen en la `Combos` sección. Cada `Combo` elemento representa un cuadro de lista desplegable en el IDE. Los usuarios pueden escribir en el cuadro de lista o no, dependiendo del valor del `type` atributo del cuadro combinado. Los cuadros combinados tienen los mismos elementos y comportamiento que los botones, y también pueden tener los siguientes atributos adicionales:

- `defaultWidth`Atributo que especifica el ancho en píxeles.

- `idCommandList`Atributo que especifica una lista que contiene los elementos que se muestran en el cuadro de lista. La lista de comandos debe declararse en el mismo `GuidSymbol` nodo que contiene el combinado.

En el ejemplo siguiente se define un elemento combinado.

```xml
<Combos>
  <Combo guid="guidFirstToolWinCmdSet"
         id="cmdidWindowsMediaFilename"
         priority="0x0100" type="DynamicCombo"
         idCommandList="cmdidWindowsMediaFilenameGetList"
         defaultWidth="130">
    <Parent guid="guidFirstToolWinCmdSet"
            id="ToolbarGroupID" />
    <CommandFlag>IconAndText</CommandFlag>
    <CommandFlag>CommandWellOnly</CommandFlag>
    <CommandFlag>StretchHorizontally</CommandFlag>
    <Strings>
      <CommandName>Filename</CommandName>
      <ButtonText>Enter a Filename</ButtonText>
    </Strings>
  </Combo>
</Combos>
```

##### <a name="bitmaps"></a>Mapas de bits
Los comandos que se mostrarán junto con un icono deben incluir un `Icon` elemento que haga referencia a un mapa de bits mediante el GUID y el identificador. Cada mapa de bits se define como un [elemento Bitmap](../../extensibility/bitmap-element.md) en la `Bitmaps` sección. Los únicos atributos necesarios para una `Bitmap` definición son `guid` y `href` , que apuntan al archivo de código fuente. Si el archivo de origen es una franja de recursos, también se requiere un atributo **usedList** para enumerar las imágenes disponibles en la franja. Para obtener más información, vea la documentación del [elemento Bitmap](../../extensibility/bitmap-element.md) .

### <a name="parenting"></a>Relación jerárquica
Las siguientes reglas rigen el modo en que un elemento puede llamar a otro elemento como su elemento primario.

|Elemento|Definido en esta sección de la tabla de comandos|Puede estar contenido (como un elemento primario o por la selección de ubicación en la `CommandPlacements` sección, o ambos).|Puede contener (conocido como primario)|
|-------------| - | - | - |
|Group (Grupo)|[Elemento Groups](../../extensibility/groups-element.md), IDE, otros VSPackages|Un menú, un grupo, el propio elemento|Menús, grupos y comandos|
|Menú|[Menus (elemento](../../extensibility/menus-element.md)), IDE, otros VSPackages|de 1 a *n* grupos|de 0 a *n* grupos|
|Barra de herramientas|[Menus (elemento](../../extensibility/menus-element.md)), IDE, otros VSPackages|El propio elemento|de 0 a *n* grupos|
|Elemento de menú|[Buttons, elemento](../../extensibility/buttons-element.md), el IDE, otros VSPackages|de 1 a *n* grupos, el propio elemento|de-0 a *n* grupos|
|Botón|[Buttons, elemento](../../extensibility/buttons-element.md), el IDE, otros VSPackages|de 1 a *n* grupos, el propio elemento||
|Combinado|[Elemento combos](../../extensibility/combos-element.md), IDE, otros VSPackages|de 1 a *n* grupos, el propio elemento||

### <a name="menu-command-and-group-placement"></a>Selección de ubicación de menús, comandos y grupos
Un menú, grupo o comando puede aparecer en más de una ubicación en el IDE. Para que un elemento aparezca en varias ubicaciones, debe agregarse a la `CommandPlacements` sección como [elemento CommandPlacement](../../extensibility/commandplacement-element.md). Cualquier menú, grupo o comando se puede agregar como ubicación del comando. Sin embargo, las barras de herramientas no se pueden colocar de esta manera porque no pueden aparecer en varias ubicaciones contextuales.

Las ubicaciones de comandos `guid` tienen `id` `priority` los atributos, y. El GUID y el identificador deben coincidir con los del elemento que se coloca. El `priority` atributo rige la colocación del elemento con respecto a otros elementos. Cuando el IDE combina dos o más elementos que tienen la misma prioridad, sus ubicaciones no están definidas porque el IDE no garantiza que los recursos del paquete se lean en el mismo orden cada vez que se compila el paquete.

Si un menú o grupo aparece en varias ubicaciones, todos los elementos secundarios de ese menú o grupo aparecerán en cada instancia.

## <a name="command-visibility-and-context"></a>Visibilidad y contexto del comando
Cuando se instalan varios VSPackages, una profusión de menús, elementos de menú y barras de herramientas puede abarrotar el IDE. Para evitar este problema, puede controlar la visibilidad de los elementos de la interfaz de usuario individuales mediante el uso de *restricciones de visibilidad* y marcas de comandos.

### <a name="visibility-constraints"></a>Restricciones de visibilidad
Una restricción de visibilidad se establece como un [elemento VisibilityItem](../../extensibility/visibilityitem-element.md) en la `VisibilityConstraints` sección. Una restricción de visibilidad define contextos de interfaz de usuario específicos en los que el elemento de destino está visible. Un menú o comando que se incluye en esta sección solo es visible cuando uno de los contextos definidos está activo. Si no se hace referencia a un menú o comando en esta sección, siempre es visible de forma predeterminada. Esta sección no se aplica a los grupos.

`VisibilityItem` los elementos deben tener tres atributos, de la siguiente manera: `guid` y `id` del elemento de la interfaz de usuario de destino, y `context` . El `context` atributo especifica cuándo se verá el elemento de destino y toma cualquier contexto de interfaz de usuario válido como su valor. Las constantes de contexto de la interfaz de usuario de Visual Studio son miembros de la <xref:Microsoft.VisualStudio.VSConstants> clase. Cada `VisibilityItem` elemento solo puede tomar un valor de contexto. Para aplicar un segundo contexto, cree un segundo `VisibilityItem` elemento que apunte al mismo elemento, tal y como se muestra en el ejemplo siguiente.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidSolutionToolbarCmdSet"
        id="cmdidTestCmd"
        context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidSolutionToolbarCmdSet"
        id="cmdidTestCmd"
        context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

### <a name="command-flags"></a>Marcas de comandos
Las marcas de comandos siguientes pueden afectar a la visibilidad de los menús y los comandos a los que se aplican.

`AlwaysCreate` El menú se crea incluso si no tiene grupos o botones.

Válido para: `Menu`

`CommandWellOnly` Aplique esta marca si el comando no aparece en el menú de nivel superior y desea que esté disponible para la personalización de Shell adicional, por ejemplo, para enlazarlo a una clave. Una vez instalado el VSPackage, un usuario puede personalizar estos comandos; para ello, abra el cuadro de diálogo **Opciones** y, a continuación, edite la ubicación del comando en la categoría **entorno del teclado** . No afecta a la colocación de los menús contextuales, las barras de herramientas, los controladores de menú o los submenús.

Válido para: `Button` , `Combo`

`DefaultDisabled` De forma predeterminada, el comando se deshabilita si el VSPackage que implementa el comando no está cargado o si no se ha llamado al método QueryStatus.

Válido para: `Button` , `Combo`

`DefaultInvisible` De forma predeterminada, el comando es invisible si el VSPackage que implementa el comando no está cargado o si no se ha llamado al método QueryStatus.

Debe combinarse con la `DynamicVisibility` marca.

Válido para: `Button` , `Combo` , `Menu`

`DynamicVisibility` La visibilidad del comando se puede cambiar mediante el `QueryStatus` método o un GUID de contexto que se incluye en la `VisibilityConstraints` sección.

Se aplica a los comandos que aparecen en los menús, no en las barras de herramientas. Los elementos de la barra de herramientas de nivel superior pueden deshabilitarse, pero no ocultarse, cuando el `OLECMDF_INVISIBLE` método devuelve la marca `QueryStatus` .

En un menú, esta marca también indica que se debe ocultar automáticamente cuando sus miembros están ocultos. Esta marca normalmente se asigna a submenús, ya que los menús de nivel superior ya tienen este comportamiento.

Debe combinarse con la `DefaultInvisible` marca.

Válido para: `Button` , `Combo` , `Menu`

`NoShowOnMenuController` Si un comando que tiene esta marca se coloca en un controlador de menú, el comando no aparece en la lista desplegable.

Válido para: `Button`

Para obtener más información sobre las marcas de comandos, consulte la documentación del [elemento CommandFlag](../../extensibility/command-flag-element.md) .

#### <a name="general-requirements"></a>Requisitos generales
El comando debe pasar la siguiente serie de pruebas para que se pueda mostrar y habilitar:

- El comando está colocado correctamente.

- `DefaultInvisible`No se ha establecido la marca.

- El menú o la barra de herramientas primarios están visibles.

- El comando no es invisible debido a una entrada de contexto en la sección del [elemento VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) .

- El código VSPackage que implementa la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz muestra y habilita el comando. Ningún código de interfaz lo ha interceptado y ha actuado sobre él.

- Cuando un usuario hace clic en el comando, se somete al procedimiento que se describe en el algoritmo de [enrutamiento](../../extensibility/internals/command-routing-algorithm.md).

## <a name="call-pre-defined-commands"></a>Llamar a comandos predefinidos
El [elemento UsedCommands](../../extensibility/usedcommands-element.md) habilita los VSPackages para tener acceso a los comandos proporcionados por otros VSPackages o por el IDE. Para ello, cree un [elemento UsedCommand](../../extensibility/usedcommand-element.md) que tenga el GUID y el identificador del comando que se va a usar. Esto garantiza que Visual Studio cargará el comando, aunque no forme parte de la configuración actual de Visual Studio. Para obtener más información, consulte [elemento UsedCommand](../../extensibility/usedcommand-element.md).

## <a name="interface-element-appearance"></a>Apariencia del elemento de la interfaz
Las consideraciones para seleccionar y colocar elementos de comandos son las siguientes:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ofrece muchos elementos de interfaz de usuario que aparecen de manera diferente en función de la selección de ubicación.

- Un elemento de la interfaz de usuario que se define mediante la `DefaultInvisible` marca no se mostrará en el IDE a menos que sea mostrado por su implementación de VSPackage del <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> método o asociado a un contexto de interfaz de usuario determinado en la `VisibilityConstraints` sección.

- Incluso puede que no se muestre un comando colocado correctamente. Esto se debe a que el IDE oculta o muestra automáticamente algunos comandos, dependiendo de las interfaces que el VSPackage tenga implementado (o no). Por ejemplo, la implementación de un VSPackage de algunas interfaces de compilación hace que los elementos de menú relacionados con la compilación se muestren automáticamente.

- Aplicar la `CommandWellOnly` marca en la definición del elemento de la interfaz de usuario significa que el comando solo se puede agregar mediante la personalización.

- Los comandos pueden estar disponibles solo en determinados contextos de la interfaz de usuario, por ejemplo, solo cuando se muestra un cuadro de diálogo cuando el IDE está en la vista Diseño.

- Para que algunos elementos de la interfaz de usuario se muestren en el IDE, debe implementar una o más interfaces o escribir código.

## <a name="see-also"></a>Vea también
- [Extender menús y comandos](../../extensibility/extending-menus-and-commands.md)
