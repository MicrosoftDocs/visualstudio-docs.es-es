---
title: Cómo VSPackages agregar elementos de la interfaz de usuario | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
caps.latest.revision: 61
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a6265edea1044c1ee7be25725268a792d78a79cc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576482"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Cómo VSPackages agrega elementos de la interfaz de usuario
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [cómo VSPackages agregar elementos de la interfaz](https://docs.microsoft.com/visualstudio/extensibility/internals/how-vspackages-add-user-interface-elements).  
  
Un VSPackage puede agregar elementos de interfaz (IU) del usuario, por ejemplo, menús, barras de herramientas y las ventanas en Visual Studio mediante el archivo .vsct.  
  
 Puede encontrar directrices de diseño para los elementos de interfaz de usuario en [directrices de experiencia de usuario de Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="the-visual-studio-command-table-architecture"></a>La arquitectura de tabla de comandos de Visual Studio  
 Como se mencionó, la arquitectura de la tabla de comandos es compatible con los principios de arquitectura anteriores. Los principios detrás de las abstracciones, estructuras de datos y herramientas de la arquitectura de la tabla de comandos son los siguientes:  
  
-   Hay tres tipos básicos de elementos: menús, comandos y grupos. Los menús pueden exponerse en la interfaz de usuario como menús, submenús, barras de herramientas o ventanas de herramientas. Los comandos son procedimientos que el usuario puede ejecutar en el IDE, y pueden exponerse como elementos de menú, botones, cuadros de lista u otros controles. Los grupos son contenedores para los menús y comandos.  
  
-   Cada elemento viene especificada por una definición que describe el elemento, su prioridad relativa respecto a otros elementos y las marcas que modifican su comportamiento.  
  
-   Cada elemento tiene una selección de ubicación que describe al elemento primario del elemento. Un elemento puede tener varios elementos primarios, por lo que puede aparecer en varias ubicaciones de la interfaz de usuario.  
  
     Cada comando debe tener un grupo como su elemento primario, incluso si es el único elemento secundario de ese grupo. Cada menú estándar también debe tener un grupo primario. Las barras de herramientas y ventanas de herramientas actúan como sus propios elementos primarios. Un grupo puede tener como su elemento primario de la barra de menús de Visual Studio principal, o cualquier menú, barra de herramientas o ventana de herramientas.  
  
### <a name="how-items-are-defined"></a>Cómo se definen los elementos  
 . Archivos Vsct tienen formato XML. Un archivo .vsct define los elementos de interfaz de usuario para un paquete y determina dónde aparecen los elementos en el IDE. Cada menú, grupo o comando en el paquete primero se asigna un GUID y un identificador en el `Symbols` sección. En el resto del archivo .vsct archivo, cada menú, el comando y el grupo se identifican mediante su combinación de GUID y el ID. El ejemplo siguiente muestra una típica `Symbols` sección como el generado por la plantilla de paquete de Visual Studio cuando un **comando de menú** está seleccionado en la plantilla.  
  
```xml  
<Symbols>  
  <!-- This is the package guid. -->  
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />  
  
  <!-- This is the guid used to group the menu commands together -->  
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">  
  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
  </GuidSymbol>  
  
  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >  
    <IDSymbol name="bmpPic1" value="1" />  
    <IDSymbol name="bmpPic2" value="2" />  
    <IDSymbol name="bmpPicSearch" value="3" />  
    <IDSymbol name="bmpPicX" value="4" />  
    <IDSymbol name="bmpPicArrows" value="5" />  
  </GuidSymbol>  
</Symbols>  
```  
  
 El elemento de nivel superior de la `Symbols` sección es la [GuidSymbol (elemento)](../../extensibility/guidsymbol-element.md). `GuidSymbol` elementos asignan nombres a los GUID que se usan por el IDE para identificar los paquetes y sus componentes.  
  
> [!NOTE]
>  Los GUID se generan automáticamente la plantilla de paquete de Visual Studio. También puede crear un GUID único haciendo **crear GUID** en el **herramientas** menú.  
  
 La primera `GuidSymbol` elemento, "guid [nombre del paquete] Pkg", es el GUID del propio paquete. Este es el GUID que se usa Visual Studio para cargar el paquete. Normalmente, no tiene elementos secundarios.  
  
 Por convención, los menús y comandos se agrupan bajo un segundo `GuidSymbol` elemento, "guid [nombre del paquete] CmdSet", y los mapas de bits en un tercer `GuidSymbol` elemento, "guidImages". No es necesario seguir esta convención, pero cada menú, grupo, comandos y mapa de bits deben ser un elemento secundario de un `GuidSymbol` elemento.  
  
 En el segundo `GuidSymbol` elemento, que representa el conjunto de comandos de paquete, son varios `IDSymbol` elementos. Cada [IDSymbol (elemento)](../../extensibility/idsymbol-element.md) asigna un nombre a un valor numérico y puede representar un menú, grupo o comando que forma parte del conjunto de comandos. El `IDSymbol` elementos en la tercera `GuidSymbol` elemento representan los mapas de bits se pueden usar como iconos para los comandos. Como pares identificador/GUID deben ser únicos en una aplicación, no hay dos elementos secundarios del mismo `GuidSymbol` elemento puede tener el mismo valor.  
  
### <a name="menus-groups-and-commands"></a>Menús, grupos y comandos  
 Cuando un menú, grupo o comando tiene un GUID y un identificador, se puede agregar al IDE. Cada elemento de interfaz de usuario debe tener lo siguiente:  
  
-   Un `guid` atributo que coincida con el nombre de la `GuidSymbol` elemento definido en el elemento de interfaz de usuario.  
  
-   Un `id` atributo que coincida con el nombre del asociado `IDSymbol` elemento.  
  
     Juntos, el `guid` y `id` atributos componen el *firma* del elemento de interfaz de usuario.  
  
-   Un `priority` atributo que determina la posición del elemento de interfaz de usuario en su menú primario o un grupo.  
  
-   Un [elemento primario](../../extensibility/parent-element.md) cuya `guid` y `id` atributos que especifican la firma del menú primario o del grupo.  
  
#### <a name="menus"></a>Menús  
 Cada menú se define como un [Menu Element](../../extensibility/menu-element.md) en la `Menus` sección. Deben tener los menús `guid`, `id`, y `priority` atributos y un `Parent` elemento y también los siguientes atributos adicionales y elementos secundarios:  
  
-   Un `type` atributo que especifica si el menú debe aparecer en el IDE como una especie de menú o como una barra de herramientas.  
  
-   Un [Strings (elemento)](../../extensibility/strings-element.md) que contiene un [ButtonText (elemento)](../../extensibility/buttontext-element.md), que especifica el título del menú en el IDE y un [CommandName (elemento)](../../extensibility/commandname-element.md), que especifica el nombre que es utilizado en el **comando** ventana para acceder al menú.  
  
-   Marcas opcionales. Un [comando marca elemento](../../extensibility/command-flag-element.md) puede aparecer en una definición de menú para cambiar su apariencia o comportamiento en el IDE.  
  
 Cada `Menu` elemento debe tener un grupo como su elemento primario, a menos que sea un elemento, como una barra de herramientas acoplable. Un menú acoplable es su elemento primario. Para obtener más información acerca de los menús y los valores de la `type` atributo, vea el [Menu Element](../../extensibility/menu-element.md) documentación.  
  
 El ejemplo siguiente muestra un menú que aparece en la barra de menús de Visual Studio, junto a la **herramientas** menú.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet"  
id="TopLevelMenu" priority="0x700" type="Menu">  
  <Parent guid="guidSHLMainMenu"  
          id="IDG_VS_MM_TOOLSADDINS" />  
  <Strings>  
    <ButtonText>TestMenu</ButtonText>  
    <CommandName>TestMenu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="groups"></a>Grupos  
 Un grupo es un elemento que se define en el `Groups` sección del archivo .vsct. Los grupos son sólo contenedores. No aparecen en el IDE, excepto como una línea divisoria en un menú. Por lo tanto, un [elemento Group](../../extensibility/group-element.md) se define únicamente por su firma, la prioridad y el elemento primario.  
  
 Un grupo puede tener un menú de otro grupo o sí mismo como elemento primario. Sin embargo, el elemento primario es normalmente un menú o barra de herramientas. El menú en el ejemplo anterior es un elemento secundario de la `IDG_VS_MM_TOOLSADDINS` grupo y ese grupo es un elemento secundario de la barra de menús de Visual Studio. El grupo en el ejemplo siguiente es un elemento secundario del menú en el ejemplo anterior.  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 Dado que es parte de un menú, este grupo normalmente contendría los comandos. Sin embargo, también podría contener otros menús. Se trata de cómo se definen los submenús, tal como se muestra en el ejemplo siguiente.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"  
priority="0x0100" type="Menu">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>  
  <Strings>  
    <ButtonText>Sub Menu</ButtonText>  
    <CommandName>Sub Menu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="commands"></a>Comandos  
 Un comando que se proporciona en el IDE se define como un [elemento Button](../../extensibility/button-element.md) o un [Combo (elemento)](../../extensibility/combo-element.md). Para que aparezca en un menú o una barra de herramientas, el comando debe tener un grupo como su elemento primario.  
  
##### <a name="buttons"></a>Botones  
 Los botones se definen en el `Buttons` sección. Cualquier elemento de menú, botón u otro elemento que un usuario hace clic para ejecutar un comando único se considera un botón. Algunos tipos de botón también pueden incluir la funcionalidad de la lista. Los botones tienen la misma que se necesita y los atributos opcionales que tienen menús, y también puede tener un [Icon (elemento)](../../extensibility/icon-element.md) que especifica el GUID y el identificador del mapa de bits que representa el botón en el IDE. Para obtener más información sobre los botones y sus atributos, consulte el [Buttons (elemento)](../../extensibility/buttons-element.md) documentación.  
  
 El botón en el ejemplo siguiente es un elemento secundario del grupo en el ejemplo anterior y aparecerá en el IDE como elemento de menú en el menú principal de ese grupo.  
  
```  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
```  
  
##### <a name="combos"></a>Cuadro combinado  
 Cuadro combinado se define en el `Combos` sección. Cada `Combo` elemento representa un cuadro de lista desplegable en el IDE. El cuadro de lista puede ser o no puedan escribir los usuarios, dependiendo del valor de la `type` atributo combinado de la. Cuadro combinado tiene los mismos elementos y el comportamiento que los botones tienen y también puede tener los siguientes atributos adicionales:  
  
-   Un `defaultWidth` atributo que especifica el ancho en píxeles.  
  
-   Un `idCommandList` atributo que especifica una lista que contiene los elementos que se muestran en el cuadro de lista. La lista de comandos debe declararse en el mismo `GuidSymbol` nodo que contiene el cuadro combinado.  
  
 El ejemplo siguiente define un elemento de cuadro combinado.  
  
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
 Los comandos que se mostrará junto con un icono deben incluir un `Icon` elemento que hace referencia a un mapa de bits utilizando su GUID y un identificador. Cada mapa de bits se define como un [elemento de mapa de bits](../../extensibility/bitmap-element.md) en la `Bitmaps` sección. Los únicos atributos obligatorios de una `Bitmap` definition son `guid` y `href`, que apunta al archivo de origen. Si el archivo de origen es una tira de recursos, un **usedList** atributo también es necesario, para enumerar las imágenes disponibles en la franja. Para obtener más información, consulte el [elemento de mapa de bits](../../extensibility/bitmap-element.md) documentación.  
  
### <a name="parenting"></a>Relación jerárquica  
 Las siguientes reglas determinan cómo un elemento puede llamar a otro elemento como su elemento primario.  
  
|Elemento|Definidos en esta sección de la tabla de comandos|Pueden estar contenidos (como un elemento primario, o mediante la selección de ubicación en la `CommandPlacements` sección o ambos)|Puede contener (denominado un elemento primario)|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|Agrupar|[Elemento Groups](../../extensibility/groups-element.md), el IDE, otros VSPackages|Un menú, un grupo, el propio elemento|Menús, grupos y comandos|  
|Menú|[Menus (elemento)](../../extensibility/menus-element.md), el IDE, otros VSPackages|1 para *n* grupos|0 para *n* grupos|  
|Barra de herramientas|[Menus (elemento)](../../extensibility/menus-element.md), el IDE, otros VSPackages|El propio elemento|0 para *n* grupos|  
|Elemento de menú|[Botones elemento](../../extensibility/buttons-element.md), el IDE, otros VSPackages|1 para *n* agrupa, el propio elemento|-0 para *n* grupos|  
|Botón|[Botones elemento](../../extensibility/buttons-element.md), el IDE, otros VSPackages|1 para *n* agrupa, el propio elemento||  
|Cuadro combinado|[Combos (elemento)](../../extensibility/combos-element.md), el IDE, otros VSPackages|1 para *n* agrupa, el propio elemento||  
  
### <a name="menu-command-and-group-placement"></a>Menús, comandos y la ubicación de grupo  
 Un menú, grupo o comando puede aparecer en más de una ubicación en el IDE. Un elemento que aparezca en varias ubicaciones, debe agregarse a la `CommandPlacements` sección como un [CommandPlacement (elemento)](../../extensibility/commandplacement-element.md). Cualquier menú, grupo o comando se puede agregar como una ubicación del comando. Sin embargo, las barras de herramientas no se puede colocar de esta manera porque no aparecen en varias ubicaciones contextuales.  
  
 Ubicaciones de comando tienen `guid`, `id`, y `priority` atributos. El GUID y el identificador deben coincidir con los del elemento que se encuentra. El `priority` atributo rige la posición del elemento con respecto a otros elementos. Cuando el IDE combina dos o más elementos que tienen la misma prioridad, sus ubicaciones son indefinidos porque el IDE no garantiza que se leen los recursos del paquete en el mismo orden cada vez que se compila el paquete.  
  
 Si un menú o un grupo aparezca en varias ubicaciones, todos los elementos secundarios de ese menú o grupo aparecerá en cada instancia.  
  
## <a name="command-visibility-and-context"></a>Visibilidad de comandos y el contexto  
 Cuando se instalan varios VSPackages, una profusión de menús, elementos de menú y las barras de herramientas puede provocar un desorden en el IDE. Para evitar este problema, puede controlar la visibilidad de los elementos de interfaz de usuario individuales mediante *restricciones visibilidad* y marcadores de comando.  
  
##### <a name="visibility-constraints"></a>Restricción de visibilidad  
 Una restricción de visibilidad se establece como un [VisibilityItem elemento](../../extensibility/visibilityitem-element.md) en la `VisibilityConstraints` sección. Una restricción de visibilidad define los contextos de interfaz de usuario concretos en el que está visible el elemento de destino. Un menú o un comando que se incluye en esta sección solo está visible cuando uno de los contextos definidos está activa. Si un menú o un comando no se hace referencia en esta sección, siempre es visible de forma predeterminada. En esta sección no se aplica a los grupos.  
  
 `VisibilityItem` los elementos deben tener tres atributos, como sigue: el `guid` y `id` del elemento de interfaz de usuario de destino, y `context`. El `context` atributo especifica cuándo será visible el elemento de destino y toma cualquier contexto de interfaz de usuario válido como su valor. Las constantes de contexto de interfaz de usuario de Visual Studio son miembros de la <xref:Microsoft.VisualStudio.VSConstants> clase. Cada `VisibilityItem` elemento puede tomar el valor de solo un contexto. Para aplicar un segundo contexto, cree una segunda `VisibilityItem` elemento al que apunta al mismo elemento, tal como se muestra en el ejemplo siguiente.  
  
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
  
##### <a name="command-flags"></a>Marcadores de comando  
 Las siguientes marcas de comando pueden afectar a la visibilidad de los menús y comandos que se aplican.  
  
 AlwaysCreate  
 Incluso si no tiene botones ni grupos, se crea el menú.  
  
 Válido para: `Menu`  
  
 CommandWellOnly  
 Aplicar esta marca si el comando no aparece en el menú de nivel superior y desea que esté disponible para la personalización del shell adicionales, por ejemplo, enlazarlo a una clave. Después de instala el paquete VSPackage, un usuario puede personalizar estos comandos, abra el **opciones** cuadro de diálogo y, a continuación, editar la colocación de comandos en el **teclado entorno** categoría. No afecta a la ubicación en los menús contextuales, barras de herramientas, controladores de menús o submenús.  
  
 Válido para: `Button`, `Combo`  
  
 DefaultDisabled  
 De forma predeterminada, el comando está deshabilitado si no está cargado el VSPackage que implemente el comando o no se ha llamado al método QueryStatus.  
  
 Válido para: `Button`, `Combo`  
  
 DefaultInvisible  
 De forma predeterminada, el comando es invisible si el VSPackage que implemente el comando no está cargado o no se ha llamado al método QueryStatus.  
  
 Se debe combinar con el `DynamicVisibility` marca.  
  
 Válido para: `Button`, `Combo`, `Menu`  
  
 DynamicVisibility  
 Se puede cambiar la visibilidad del comando mediante el método QueryStatus o un GUID de contexto que se incluye en el `VisibilityConstraints` sección.  
  
 Se aplica a los comandos que aparecen en los menús, no en las barras de herramientas. Elementos de nivel superior de la barra de herramientas pueden deshabilitados, pero no ocultos, cuando se devuelve la marca OLECMDF_INVISIBLE desde el método QueryStatus.  
  
 En un menú, esta marca indica también que se debe ocultarse automáticamente cuando sus miembros están ocultos. Esta marca normalmente se asigna a los submenús porque menús de nivel superior ya tienen este comportamiento.  
  
 Se debe combinar con el `DefaultInvisible` marca.  
  
 Válido para: `Button`, `Combo`, `Menu`  
  
 NoShowOnMenuController  
 Si un comando que tiene este indicador se coloca en un controlador de menú, el comando no aparece en la lista desplegable.  
  
 Válido para: `Button`  
  
 Para obtener más información acerca de las marcas de comando, consulte el [comando marca elemento](../../extensibility/command-flag-element.md) documentación.  
  
##### <a name="general-requirements"></a>Requisitos generales  
 El comando debe pasar a la siguiente serie de pruebas antes de mostrarse y habilitado:  
  
-   El comando se coloca correctamente.  
  
-   El `DefaultInvisible` no se establece la marca.  
  
-   El menú primario o la barra de herramientas está visible.  
  
-   El comando no es invisible debido a una entrada de contexto en el [VisibilityConstraints (elemento)](../../extensibility/visibilityconstraints-element.md) sección.  
  
-   Código de VSPackage que implemente la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz muestra y permite que el comando. No hay código de la interfaz interceptado y ha actuado sobre él.  
  
-   Cuando un usuario hace clic en el comando, se convierte en sujeto al procedimiento que se describe en [algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="calling-pre-defined-commands"></a>Comandos predefinido que realiza la llamada  
 El [UsedCommands (elemento)](../../extensibility/usedcommands-element.md) habilita a VSPackages para acceder a los comandos que se proporcionan por otros VSPackages o por el IDE. Para ello, cree un [UsedCommand (elemento)](../../extensibility/usedcommand-element.md) que tiene el GUID y el identificador del comando que se va a usar. Esto garantiza que el comando se cargarán por Visual Studio, incluso si no es parte de la configuración actual de Visual Studio. Para obtener más información, consulte [UsedCommand (elemento)](../../extensibility/usedcommand-element.md).  
  
## <a name="interface-element-appearance"></a>Apariencia del elemento de interfaz  
 Consideraciones para seleccionar y colocar elementos de comando son los siguientes:  
  
-   [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ofrece muchos elementos de interfaz de usuario que aparecen de manera diferente dependiendo de la selección de ubicación.  
  
-   Un elemento de interfaz de usuario que se define utilizando el `DefaultInvisible` marca no se mostrará en el IDE a menos que se muestran en su implementación de VSPackage de la <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> método, o asociados con un determinado contexto de interfaz de usuario en el `VisibilityConstraints` sección.  
  
-   No puede mostrarse incluso un comando colocado correctamente. Esto es porque el IDE automáticamente oculta o muestra algunos comandos, dependiendo de las interfaces que el VSPackage tiene (o no) implementa. Por ejemplo, la implementación de un VSPackage de algunos crear interfaces de elementos de menú relacionadas con la compilación de las causas que se mostrará automáticamente.  
  
-   Aplicar el `CommandWellOnly` marca en la definición del elemento de interfaz de usuario significa que se puede agregar el comando sólo gracias a la personalización.  
  
-   Los comandos pueden estar disponibles solo en determinados contextos de interfaz de usuario, por ejemplo, solo cuando se muestra un cuadro de diálogo cuando el IDE está en la vista Diseño.  
  
-   Para hacer que algunos elementos de interfaz de usuario que se mostrará en el IDE, debe implementar uno o más interfaces o escribir algo de código.  
  
## <a name="see-also"></a>Vea también  
 [Ampliación de menús y comandos](../../extensibility/extending-menus-and-commands.md)

