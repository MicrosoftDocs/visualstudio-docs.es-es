---
title: Cómo VSPackages Agregar elementos de interfaz de usuario ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d9cc3184009dd98e743064db1b8eb2abe6059d1
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649594"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Cómo VSPackages agregan elementos de interfaz de usuario
Un VSPackage puede agregar elementos de interfaz de usuario (UI), por ejemplo, menús, barras de herramientas y ventanas de herramientas, a Visual Studio mediante el archivo *.vsct.*

Puede encontrar directrices de diseño para elementos de interfaz de usuario en las directrices de experiencia de usuario de [Visual Studio.](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

## <a name="the-visual-studio-command-table-architecture"></a>La arquitectura de la tabla de comandos de Visual Studio
Como se ha indicado, la arquitectura de la tabla de comandos admite los principios arquitectónicos anteriores. Los principios detrás de las abstracciones, estructuras de datos y herramientas de la arquitectura de la tabla de comandos son los siguientes:

- Hay tres tipos básicos de elementos: menús, comandos y grupos. Los menús se pueden exponer en la interfaz de usuario como menús, submenús, barras de herramientas o ventanas de herramientas. Los comandos son procedimientos que el usuario puede ejecutar en el IDE y se pueden exponer como elementos de menú, botones, cuadros de lista u otros controles. Los grupos son contenedores para menús y comandos.

- Cada elemento se especifica mediante una definición que describe el elemento, su prioridad con respecto a otros elementos y las marcas que modifican su comportamiento.

- Cada elemento tiene una ubicación que describe el elemento primario del elemento. Un elemento puede tener varios elementos primarios, por lo que puede aparecer en varias ubicaciones de la interfaz de usuario.

Cada comando debe tener un grupo como su elemento primario, incluso si es el único elemento secundario de ese grupo. Cada menú estándar también debe tener un grupo primario. Las barras de herramientas y las ventanas de herramientas actúan como sus propios padres. Un grupo puede tener como elemento primario la barra de menús principal de Visual Studio o cualquier menú, barra de herramientas o ventana de herramientas.

### <a name="how-items-are-defined"></a>Cómo se definen los elementos
Un archivo *.vsct* tiene formato XML. Define los elementos de la interfaz de usuario para un paquete y determina dónde aparecen esos elementos en el IDE. A cada menú, grupo o comando del paquete se `Symbols` le asigna primero un GUID y un identificador en la sección. En el resto del archivo *.vsct,* cada menú, comando y grupo se identifica mediante su combinación GUID e ID. En el ejemplo `Symbols` siguiente se muestra una sección típica generada por la plantilla de paquete de Visual Studio cuando se selecciona un comando de **menú** en la plantilla.

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

El elemento de nivel `Symbols` superior de la sección es el [elemento GuidSymbol](../../extensibility/guidsymbol-element.md). `GuidSymbol`los elementos asignan nombres a GUID que utiliza el IDE para identificar paquetes y sus componentes.

> [!NOTE]
> Los GUID se generan automáticamente mediante la plantilla de paquete de Visual Studio. También puede crear un GUID único haciendo clic en **Crear GUID** en el menú **Herramientas.**

El `GuidSymbol` primer `guid<PackageName>Pkg`elemento, , es el GUID del propio paquete. Este es el GUID que usa Visual Studio para cargar el paquete. Normalmente, no tiene elementos secundarios.

Por convención, los menús `GuidSymbol` y `guid<PackageName>CmdSet`los comandos se agrupan `GuidSymbol` en `guidImages`un segundo elemento, y los mapas de bits están bajo un tercer elemento, . No es necesario seguir esta convención, pero cada menú, grupo, comando `GuidSymbol` y mapa de bits debe ser un elemento secundario de un elemento.

En el `GuidSymbol` segundo elemento, que representa el `IDSymbol` conjunto de comandos de paquete, hay varios elementos. Cada [elemento IDSymbol](../../extensibility/idsymbol-element.md) asigna un nombre a un valor numérico y puede representar un menú, grupo o comando que forma parte del conjunto de comandos. Los `IDSymbol` elementos `GuidSymbol` del tercer elemento representan mapas de bits que se pueden utilizar como iconos para los comandos. Dado que los pares GUID/ID deben ser únicos `GuidSymbol` en una aplicación, no hay dos elementos secundarios del mismo elemento puede tener el mismo valor.

### <a name="menus-groups-and-commands"></a>Menús, grupos y comandos
Cuando un menú, grupo o comando tiene un GUID y un identificador, se puede agregar al IDE. Cada elemento de interfaz de usuario debe tener las siguientes cosas:

- Atributo `guid` que coincide con `GuidSymbol` el nombre del elemento en el que se define el elemento de interfaz de usuario.

- Atributo `id` que coincide con el `IDSymbol` nombre del elemento asociado.

Juntos, `guid` `id` los atributos y componen la *firma* del elemento de interfaz de usuario.

- Atributo `priority` que determina la ubicación del elemento de interfaz de usuario en su menú o grupo primario.

- Un [elemento](../../extensibility/parent-element.md) Primario `guid` que tiene y `id` atributos que especifican la firma del menú o grupo primario.

#### <a name="menus"></a>Menús
Cada menú se define como `Menus` un elemento [Menu](../../extensibility/menu-element.md) en la sección. Los menús `id`deben `priority` tener `guid`, `Parent` , y atributos, y un elemento, así como los siguientes atributos adicionales y elementos secundarios:

- Atributo `type` que especifica si el menú debe aparecer en el IDE como un tipo de menú o como una barra de herramientas.

- Un [elemento Strings](../../extensibility/strings-element.md) que contiene un elemento [ButtonText](../../extensibility/buttontext-element.md), que especifica el título del menú en el IDE, y un [elemento CommandName](../../extensibility/commandname-element.md), que especifica el nombre que se utiliza en la ventana **Comando** para tener acceso al menú.

- Marcas opcionales. Un [CommandFlag elemento](../../extensibility/command-flag-element.md) puede aparecer en una definición de menú para cambiar su apariencia o comportamiento en el IDE.

Cada `Menu` elemento debe tener un grupo como su elemento primario, a menos que sea un elemento acoplable como una barra de herramientas. Un menú acoplable es su propio elemento primario. Para obtener más información acerca `type` de los menús y valores para el atributo, consulte la menu [elemento](../../extensibility/menu-element.md) documentación.

En el ejemplo siguiente se muestra un menú que aparece en la barra de menús de Visual Studio, junto al menú **Herramientas.**

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
Un grupo es un elemento `Groups` que se define en la sección del archivo *.vsct.* Los grupos son sólo contenedores. No aparecen en el IDE excepto como una línea divisoria en un menú. Por lo tanto, un [Group elemento](../../extensibility/group-element.md) se define sólo por su firma, prioridad y elemento primario.

Un grupo puede tener un menú, otro grupo o a sí mismo como elemento primario. Sin embargo, el elemento primario suele ser un menú o una barra de herramientas. El menú del ejemplo anterior es `IDG_VS_MM_TOOLSADDINS` un elemento secundario del grupo y ese grupo es un elemento secundario de la barra de menús de Visual Studio. El grupo del ejemplo siguiente es un elemento secundario del menú en el ejemplo anterior.

```xml
<Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" priority="0x0600">
  <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
</Group>
```

Dado que forma parte de un menú, este grupo normalmente contendría comandos. Sin embargo, también podría contener otros menús. Así es como se definen los submenús, como se muestra en el ejemplo siguiente.

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
Un comando que se proporciona al IDE se define como un [Button elemento](../../extensibility/button-element.md) o un [Combo elemento](../../extensibility/combo-element.md). Para aparecer en un menú o una barra de herramientas, el comando debe tener un grupo como su elemento primario.

##### <a name="buttons"></a>Botones
Los botones `Buttons` se definen en la sección. Cualquier elemento de menú, botón u otro elemento en el que un usuario haga clic para ejecutar un único comando se considera un botón. Algunos tipos de botones también pueden incluir la funcionalidad de lista. Los botones tienen los mismos atributos obligatorios y opcionales que los menús y también pueden tener un [elemento Icon](../../extensibility/icon-element.md) que especifica el GUID y el identificador del mapa de bits que representa el botón en el IDE. Para obtener más información acerca de los botones y sus atributos, consulte la documentación [del elemento Buttons.](../../extensibility/buttons-element.md)

El botón del ejemplo siguiente es un elemento secundario del grupo en el ejemplo anterior y aparecería en el IDE como un elemento de menú en el menú primario de ese grupo.

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

##### <a name="combos"></a>Combos
Los combos se `Combos` definen en la sección. Cada `Combo` elemento representa un cuadro de lista desplegable en el IDE. El cuadro de lista puede o no ser grabable por `type` los usuarios, dependiendo del valor del atributo del combo. Los combos tienen los mismos elementos y comportamiento que los botones y también pueden tener los siguientes atributos adicionales:

- Atributo `defaultWidth` que especifica el ancho de píxel.

- Atributo `idCommandList` que especifica una lista que contiene los elementos que se muestran en el cuadro de lista. La lista de comandos `GuidSymbol` debe declararse en el mismo nodo que contiene el combo.

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
Los comandos que se mostrarán junto `Icon` con un icono deben incluir un elemento que haga referencia a un mapa de bits mediante su GUID e identificador. Cada mapa de bits se `Bitmaps` define como un elemento [Bitmap](../../extensibility/bitmap-element.md) en la sección. Los únicos atributos necesarios para una `Bitmap` definición son `guid` y `href`, que apunta al archivo de origen. Si el archivo de origen es una tira de recursos, también se requiere un atributo **usedList** para enumerar las imágenes disponibles en la tira. Para obtener más información, consulte la documentación del [elemento Bitmap.](../../extensibility/bitmap-element.md)

### <a name="parenting"></a>Crianza
Las siguientes reglas rigen cómo un elemento puede llamar a otro elemento como su elemento primario.

|Elemento|Definido en esta sección de la tabla de comandos|Puede estar contenido (como padre, o `CommandPlacements` por colocación en la sección, o ambos)|Puede contener (denominado padre)|
|-------------| - | - | - |
|Grupo|[Grupos,](../../extensibility/groups-element.md)el IDE, otros VSPackages|Un menú, un grupo, el elemento en sí|Menús, grupos y comandos|
|Menú|[Menus,](../../extensibility/menus-element.md)el IDE, otros VSPackages|1 a *n* grupos|0 a *n* grupos|
|Barra de herramientas|[Menus,](../../extensibility/menus-element.md)el IDE, otros VSPackages|El artículo en sí|0 a *n* grupos|
|Elemento de menú|[Buttons ,](../../extensibility/buttons-element.md)el IDE, otros VSPackages|1 a *n* grupos, el elemento en sí|De -0 a *n* grupos|
|Botón|[Buttons ,](../../extensibility/buttons-element.md)el IDE, otros VSPackages|1 a *n* grupos, el elemento en sí||
|Combinado|[Combos,](../../extensibility/combos-element.md)el IDE, otros VSPackages|1 a *n* grupos, el elemento en sí||

### <a name="menu-command-and-group-placement"></a>Menú, comando y colocación de grupos
Un menú, grupo o comando puede aparecer en más de una ubicación en el IDE. Para que un elemento aparezca en varias ubicaciones, debe agregarse a la `CommandPlacements` sección como un elemento [CommandPlacement](../../extensibility/commandplacement-element.md). Cualquier menú, grupo o comando se puede agregar como una ubicación de comandos. Sin embargo, las barras de herramientas no se pueden colocar de esta manera porque no pueden aparecer en varias ubicaciones sensibles al contexto.

Las ubicaciones `guid` `id`de `priority` comando stienen , , y atributos. El GUID y el identificador deben coincidir con los del elemento que se coloca. El `priority` atributo rige la colocación del elemento con respecto a otros elementos. Cuando el IDE combina dos o más elementos que tienen la misma prioridad, sus ubicaciones son indefinidas porque el IDE no garantiza que los recursos del paquete se leen en el mismo orden cada vez que se compila el paquete.

Si un menú o grupo aparece en varias ubicaciones, todos los elementos secundarios de ese menú o grupo aparecerán en cada instancia.

## <a name="command-visibility-and-context"></a>Visibilidad y contexto de comandos
Cuando se instalan varios VSPackages, una profusión de menús, elementos de menú y barras de herramientas puede saturar el IDE. Para evitar este problema, puede controlar la visibilidad de elementos de interfaz de usuario individuales mediante restricciones de *visibilidad* y indicadores de comando.

### <a name="visibility-constraints"></a>Restricciones de visibilidad
Una restricción de visibilidad se establece `VisibilityConstraints` como un [VisibilityItem elemento](../../extensibility/visibilityitem-element.md) en la sección. Una restricción de visibilidad define contextos de interfaz de usuario específicos en los que el elemento de destino está visible. Un menú o comando que se incluye en esta sección solo es visible cuando uno de los contextos definidos está activo. Si no se hace referencia a un menú o comando en esta sección, siempre está visible de forma predeterminada. Esta sección no se aplica a los grupos.

`VisibilityItem`los elementos deben tener tres `guid` atributos, como se indica a continuación: el elemento de interfaz de usuario de `id` destino y `context`. El `context` atributo especifica cuándo estará visible el elemento de destino y toma cualquier contexto de interfaz de usuario válido como su valor. Las constantes de contexto de interfaz de usuario para Visual Studio son miembros de la <xref:Microsoft.VisualStudio.VSConstants> clase. Cada `VisibilityItem` elemento puede tomar solo un valor de contexto. Para aplicar un segundo contexto, cree un segundo `VisibilityItem` elemento que apunte al mismo elemento, como se muestra en el ejemplo siguiente.

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

### <a name="command-flags"></a>Banderas de mando
Los siguientes indicadores de comando pueden afectar a la visibilidad de los menús y comandos a los que se aplican.

`AlwaysCreate`El menú se crea incluso si no tiene grupos ni botones.

Válido para:`Menu`

`CommandWellOnly`Aplique esta marca si el comando no aparece en el menú de nivel superior y desea que esté disponible para la personalización de shell adicional, por ejemplo, enlazarlo a una clave. Después de instalar el VSPackage, un usuario puede personalizar estos comandos abriendo el cuadro de diálogo **Opciones** y, a continuación, editando la ubicación del comando en la categoría Entorno de **teclado.** No afecta a la colocación en menús contextuales, barras de herramientas, controladores de menú o submenús.

Válido para: `Button`,`Combo`

`DefaultDisabled`De forma predeterminada, el comando está deshabilitado si el VSPackage que implementa el comando no está cargado o el QueryStatus no se ha llamado al método.

Válido para: `Button`,`Combo`

`DefaultInvisible`De forma predeterminada, el comando es invisible si el VSPackage que implementa el comando no está cargado o el QueryStatus no se ha llamado al método.

Debe combinarse `DynamicVisibility` con la bandera.

Válido `Button`para: `Combo`, ,`Menu`

`DynamicVisibility`La visibilidad del comando se puede `QueryStatus` cambiar mediante el método o `VisibilityConstraints` un GUID de contexto que se incluye en la sección.

Se aplica a los comandos que aparecen en los menús, no en las barras de herramientas. Los elementos de la barra de herramientas `OLECMDF_INVISIBLE` de nivel superior `QueryStatus` se pueden deshabilitar, pero no ocultar, cuando se devuelve la marca desde el método.

En un menú, esta marca también indica que debe ocultarse automáticamente cuando sus miembros están ocultos. Esta marca se asigna normalmente a los submenús porque los menús de nivel superior ya tienen este comportamiento.

Debe combinarse `DefaultInvisible` con la bandera.

Válido `Button`para: `Combo`, ,`Menu`

`NoShowOnMenuController`Si un comando que tiene esta marca se coloca en un controlador de menú, el comando no aparece en la lista desplegable.

Válido para:`Button`

Para obtener más información acerca de los indicadores de comando, consulte la documentación del [elemento CommandFlag.](../../extensibility/command-flag-element.md)

#### <a name="general-requirements"></a>Requisitos generales
El comando debe pasar la siguiente serie de pruebas antes de que se pueda mostrar y habilitar:

- El comando se coloca correctamente.

- La `DefaultInvisible` marca no está establecida.

- El menú principal o la barra de herramientas está visible.

- El comando no es invisible debido a una entrada de contexto en la sección del [elemento VisibilityConstraints.](../../extensibility/visibilityconstraints-element.md)

- Código vsPackage que <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementa la interfaz muestra y habilita el comando. Ningún código de interfaz lo interceptó y actuó en él.

- Cuando un usuario hace clic en el comando, está sujeto al procedimiento que se describe en Algoritmo de [enrutamiento](../../extensibility/internals/command-routing-algorithm.md).

## <a name="call-pre-defined-commands"></a>Llamar a comandos predefinidos
El [elemento UsedCommands](../../extensibility/usedcommands-element.md) permite a VSPackages tener acceso a comandos proporcionados por otros VSPackages o por el IDE. Para ello, cree un [elemento UsedCommand](../../extensibility/usedcommand-element.md) que tenga el GUID y el identificador del comando que se va a usar. Esto garantiza que Visual Studio cargará el comando, incluso si no forma parte de la configuración actual de Visual Studio. Para obtener más información, vea [Elemento UsedCommand](../../extensibility/usedcommand-element.md).

## <a name="interface-element-appearance"></a>Apariencia del elemento de interfaz
Las consideraciones para seleccionar y colocar elementos de comando son las siguientes:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ofrece muchos elementos de interfaz de usuario que aparecen de forma diferente dependiendo de la ubicación.

- Un elemento de interfaz `DefaultInvisible` de usuario que se define mediante el uso de la marca no <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> se mostrará en el IDE `VisibilityConstraints` a menos que se muestra por su implementación de VSPackage del método o asociado a un contexto de interfaz de usuario determinado en la sección.

- Es posible que no se muestre incluso un comando colocado correctamente. Esto se debe a que el IDE oculta o muestra automáticamente algunos comandos, dependiendo de las interfaces que el VSPackage tiene (o no) implementado. Por ejemplo, la implementación de un VSPackage de algunas interfaces de compilación hace que los elementos de menú relacionados con la compilación se muestren automáticamente.

- Aplicar la `CommandWellOnly` marca en la definición de elemento de interfaz de usuario significa que el comando solo se puede agregar mediante personalización.

- Los comandos pueden estar disponibles solo en determinados contextos de interfaz de usuario, por ejemplo, solo cuando se muestra un cuadro de diálogo cuando el IDE está en la vista de diseño.

- Para hacer que ciertos elementos de la interfaz de usuario se muestren en el IDE, debe implementar una o varias interfaces o escribir código.

## <a name="see-also"></a>Consulte también
- [Extender menús y comandos](../../extensibility/extending-menus-and-commands.md)
