---
title: ¿Cómo VSPackages agregar elementos de la interfaz de usuario | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 930ab9e741b2fd5bbc0ca2954192fe5e2c4313d4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-vspackages-add-user-interface-elements"></a>¿Cómo VSPackages agregar elementos de la interfaz de usuario
Un VSPackage puede agregar elementos de interfaz (UI) de usuario, por ejemplo, menús, barras de herramientas y herramientas de windows, Visual Studio mediante el archivo .vsct.  
  
 Puede encontrar instrucciones de diseño para los elementos de interfaz de usuario en [instrucciones para la experiencia del usuario de Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="the-visual-studio-command-table-architecture"></a>La arquitectura de tabla de comandos de Visual Studio  
 Como se mencionó, la arquitectura de la tabla de comandos es compatible con los principios de arquitectura anteriores. Los principios detrás del abstracciones, estructuras de datos y las herramientas de generación de la arquitectura de la tabla de comandos son los siguientes:  
  
-   Hay tres tipos básicos de elementos: menús, comandos y grupos. Los menús pueden exponerse en la interfaz de usuario como menús, submenús, barras de herramientas o las ventanas de herramientas. Los comandos son procedimientos que el usuario puede ejecutar en el IDE, y se puede exponer como elementos de menú, botones, cuadros de lista u otros controles. Los grupos son contenedores para los menús y comandos.  
  
-   Cada elemento se especifica mediante una definición que describe el elemento, su prioridad en relación con otros elementos y las marcas que modifiquen su comportamiento.  
  
-   Cada elemento tiene una selección de ubicación que describe al elemento primario del elemento. Un elemento puede tener varios elementos primarios, por lo que puede aparecer en varias ubicaciones en la interfaz de usuario.  
  
     Cada comando debe tener un grupo como su elemento principal, incluso si es el único elemento secundario de ese grupo. Cada menú estándar también debe tener un grupo primario. Barras de herramientas y ventanas de herramientas actúan como sus propios elementos primarios. Un grupo puede tener como su elemento primario de la barra de menús principal de Visual Studio, o cualquier menú, barra de herramientas o ventana de herramientas.  
  
### <a name="how-items-are-defined"></a>Cómo se definen los elementos  
 . Archivos Vsct tienen formato XML. Un archivo .vsct define los elementos de interfaz de usuario para un paquete y determina dónde aparecen los elementos en el IDE. Cada menú, grupo o comando en el paquete primero se asigna un GUID y un identificador en la `Symbols` sección. En el resto de la .vsct archivo, cada menú, el comando y el grupo se identifican mediante su combinación de GUID y el ID. En el ejemplo siguiente se muestra una típica `Symbols` sección como las generadas por la plantilla de paquete de Visual Studio cuando un **comando de menú** está seleccionado en la plantilla.  
  
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
  
 El elemento de nivel superior de la `Symbols` sección es el [GuidSymbol elemento](../../extensibility/guidsymbol-element.md). `GuidSymbol` elementos asignan nombres a GUID que se usan por el IDE para identificar los paquetes y sus componentes.  
  
> [!NOTE]
>  GUID se generan automáticamente con la plantilla de paquete de Visual Studio. También puede crear un GUID único haciendo clic en **crear GUID** en el **herramientas** menú.  
  
 La primera `GuidSymbol` elemento, "guid [PackageName] Pkg", es el GUID del propio paquete. Este es el GUID que se utiliza Visual Studio para cargar el paquete. Por lo general, no tiene elementos secundarios.  
  
 Por convención, los menús y comandos están agrupadas en un segundo `GuidSymbol` elemento, "guid [PackageName] CmdSet", y los mapas de bits en un tercer `GuidSymbol` elemento, "guidImages". No es necesario seguir esta convención, pero cada menú, el grupo, el comando y el mapa de bits deben ser un elemento secundario de un `GuidSymbol` elemento.  
  
 En el segundo `GuidSymbol` elemento, que representa el conjunto de comandos de paquete, son varios `IDSymbol` elementos. Cada [IDSymbol elemento](../../extensibility/idsymbol-element.md) asigna un nombre a un valor numérico y puede representar un menú, grupo o comando que forma parte del conjunto de comandos. El `IDSymbol` elementos en la tercera `GuidSymbol` elemento representan los mapas de bits que puede utilizarse como iconos para los comandos. Como pares GUID/identificador deben ser únicos en una aplicación, no hay dos elementos secundarios del mismo `GuidSymbol` elemento puede tener el mismo valor.  
  
### <a name="menus-groups-and-commands"></a>Los menús, los grupos y los comandos  
 Cuando un menú, grupo o comando tiene un GUID y un identificador, y puede agregar al IDE. Cada elemento de interfaz de usuario debe tener lo siguiente:  
  
-   A `guid` atributo que coincida con el nombre de la `GuidSymbol` elemento definido en el elemento de interfaz de usuario.  
  
-   Un `id` atributo que coincida con el nombre del asociado `IDSymbol` elemento.  
  
     Juntos, el `guid` y `id` atributos componen la *firma* del elemento de interfaz de usuario.  
  
-   Un `priority` atributo que determina la posición del elemento de interfaz de usuario de su menú primario o un grupo.  
  
-   A [elemento primario](../../extensibility/parent-element.md) cuya `guid` y `id` atributos que especifican la firma del menú primario o del grupo.  
  
#### <a name="menus"></a>Menús  
 Cada menú se define como un [el elemento de menú](../../extensibility/menu-element.md) en la `Menus` sección. Deben tener los menús `guid`, `id`, y `priority` atributos y un `Parent` elemento y también los siguientes atributos adicionales y elementos secundarios:  
  
-   Un `type` atributo que especifica si el menú debe aparecer en el IDE como un tipo de menú o una barra de herramientas.  
  
-   A [elemento Strings](../../extensibility/strings-element.md) que contiene un [ButtonText elemento](../../extensibility/buttontext-element.md), que especifica el título del menú en el IDE y un [CommandName elemento](../../extensibility/commandname-element.md), que especifica el nombre que es utilizado en el **comando** ventana para acceder al menú.  
  
-   Marcas opcionales. A [comando marca elemento](../../extensibility/command-flag-element.md) puede aparecer en una definición de menú para cambiar su apariencia o comportamiento en el IDE.  
  
 Cada `Menu` elemento debe tener un grupo como su elemento primario, a menos que sea un elemento acoplable como una barra de herramientas. Un menú acoplable es su propio elemento primario. Para obtener más información acerca de los menús y los valores de la `type` de atributo, vea la [el elemento de menú](../../extensibility/menu-element.md) documentación.  
  
 En el ejemplo siguiente se muestra un menú que aparece en la barra de menús de Visual Studio, junto a la **herramientas** menú.  
  
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
 Un grupo es un elemento que se define en la `Groups` sección del archivo vsct. Los grupos son sólo contenedores. No aparecen en el IDE excepto como una línea divisoria en un menú. Por lo tanto, un [elemento Group](../../extensibility/group-element.md) se define únicamente por su firma, la prioridad y el elemento primario.  
  
 Un grupo puede tener un menú de otro grupo o sí mismo como elemento primario. Sin embargo, el elemento primario es normalmente un menú o barra de herramientas. El menú en el ejemplo anterior es un elemento secundario de la `IDG_VS_MM_TOOLSADDINS` grupos y que es un elemento secundario de la barra de menús de Visual Studio. El grupo en el ejemplo siguiente es un elemento secundario del menú en el ejemplo anterior.  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 Dado que forma parte de un menú, este grupo se suelen contener los comandos. Sin embargo, también podría contener otros menús. Se trata cómo se definen los submenús, tal como se muestra en el ejemplo siguiente.  
  
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
 Un comando que se proporciona el IDE se define como un [elemento Button](../../extensibility/button-element.md) o un [elemento combinado](../../extensibility/combo-element.md). Para que aparezca en un menú o una barra de herramientas, el comando debe tener un grupo como su elemento primario.  
  
##### <a name="buttons"></a>Botones  
 Botones se definen en la `Buttons` sección. Cualquier elemento de menú, botón u otro elemento que un usuario hace clic para ejecutar un único comando se considera un botón. Algunos tipos de botones también pueden incluir la funcionalidad de la lista. Los botones tienen la misma que se necesita y los atributos opcionales que dispone de menús, y también puede tener un [Icon (elemento)](../../extensibility/icon-element.md) que especifica el GUID y el identificador del mapa de bits que representa el botón en el IDE. Para obtener más información sobre los botones y sus atributos, vea la [botones elemento](../../extensibility/buttons-element.md) documentación.  
  
 El botón en el ejemplo siguiente es un elemento secundario del grupo en el ejemplo anterior y aparecería en el IDE como un elemento de menú en el menú principal de ese grupo.  
  
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
 Cuadro combinado se define en la `Combos` sección. Cada `Combo` elemento representa un cuadro de lista desplegable en el IDE. El cuadro de lista puede o no puede tener permisos de escritura a los usuarios, dependiendo del valor de la `type` atributo del cuadro combinado. Cuadro combinado tiene los mismos elementos y el comportamiento que botones tiene y también puede tener los siguientes atributos adicionales:  
  
-   Un `defaultWidth` atributo que especifica el ancho en píxeles.  
  
-   Un `idCommandList` atributo que especifica una lista que contiene los elementos que se muestran en el cuadro de lista. La lista de comandos debe declararse en la misma `GuidSymbol` nodo que contiene el cuadro combinado.  
  
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
 Los comandos que se mostrará junto con un icono deben incluir un `Icon` elemento que hace referencia a un mapa de bits utilizando su GUID y un identificador. Cada mapa de bits se define como un [elemento de mapa de bits](../../extensibility/bitmap-element.md) en la `Bitmaps` sección. Los únicos atributos obligatorios de una `Bitmap` definition son `guid` y `href`, que apunta al archivo de código fuente. Si el archivo de origen es una banda de recurso, un **usedList** atributo también es necesario, para enumerar las imágenes disponibles en la franja. Para obtener más información, consulte el [elemento de mapa de bits](../../extensibility/bitmap-element.md) documentación.  
  
### <a name="parenting"></a>Relaciones jerárquicas  
 Las reglas siguientes rigen cómo un elemento puede llamar a otro elemento como su elemento primario.  
  
|Elemento|Definidos en esta sección de la tabla de comandos|Puede incluirse (como un elemento primario, o mediante la posición en la `CommandPlacements` sección o ambos)|Puede contener (denominado un elemento primario)|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|Agrupar|[Elemento Groups](../../extensibility/groups-element.md), el IDE, otros VSPackages|Un menú, un grupo, el propio elemento|Los menús, los grupos y los comandos|  
|Menú|[Elemento menús](../../extensibility/menus-element.md), el IDE, otros VSPackages|1 a *n* grupos|0 para *n* grupos|  
|Barra de herramientas|[Elemento menús](../../extensibility/menus-element.md), el IDE, otros VSPackages|El elemento en Sí|0 para *n* grupos|  
|Elemento de menú|[Botones elemento](../../extensibility/buttons-element.md), el IDE, otros VSPackages|1 a *n* grupos, el propio elemento|-0 para *n* grupos|  
|Botón|[Botones elemento](../../extensibility/buttons-element.md), el IDE, otros VSPackages|1 a *n* grupos, el propio elemento||  
|combinado|[Elemento de cuadro combinado](../../extensibility/combos-element.md), el IDE, otros VSPackages|1 a *n* grupos, el propio elemento||  
  
### <a name="menu-command-and-group-placement"></a>Menús y comandos, selección de ubicación de grupo  
 Un menú, grupo o comando puede aparecer en más de una ubicación en el IDE. Un elemento que aparezca en varias ubicaciones, debe agregarse a la `CommandPlacements` sección como un [CommandPlacement elemento](../../extensibility/commandplacement-element.md). Cualquier menú, grupo o comando puede agregarse como una ubicación del comando. Sin embargo, no se puede colocar las barras de herramientas de esta manera porque no pueden aparecer en varias ubicaciones contextuales.  
  
 Ubicaciones de comando tienen `guid`, `id`, y `priority` atributos. El GUID y el identificador deben coincidir con los del elemento que se coloca. El `priority` atributo controla la posición del elemento con respecto a otros elementos. Cuando el IDE combina dos o más elementos que tienen la misma prioridad, sus ubicaciones son indefinidos porque el IDE no garantiza que se leen recursos del paquete en el mismo orden cada vez que se crea el paquete.  
  
 Si un menú o el grupo aparece en varias ubicaciones, todos los elementos secundarios de ese menú o grupo se mostrará en cada instancia.  
  
## <a name="command-visibility-and-context"></a>Visibilidad de comando y el contexto  
 Cuando se instalan varios VSPackages, una profusión de menús, elementos de menú y las barras de herramientas puede abarrotar el IDE. Para evitar este problema, puede controlar la visibilidad de los elementos de interfaz de usuario individuales mediante *las restricciones de visibilidad* y marcadores de comando.  
  
##### <a name="visibility-constraints"></a>Restricciones de visibilidad  
 Una restricción de visibilidad se establece como un [VisibilityItem elemento](../../extensibility/visibilityitem-element.md) en la `VisibilityConstraints` sección. Una restricción de visibilidad define contextos concretos de interfaz de usuario en el que está visible el elemento de destino. Un menú o un comando que se incluye en esta sección solo está visible cuando uno de los contextos definidos está activo. Si un menú o un comando no se hace referencia en esta sección, siempre es visible de forma predeterminada. En esta sección no se aplica a los grupos.  
  
 `VisibilityItem` los elementos deben tener tres atributos, como se indica a continuación: el `guid` y `id` del elemento de interfaz de usuario de destino, y `context`. El `context` atributo especifica si el elemento de destino será visible y toma cualquier contexto de interfaz de usuario válido como su valor. Las constantes de contexto de la interfaz de usuario de Visual Studio son miembros de la <xref:Microsoft.VisualStudio.VSConstants> clase. Cada `VisibilityItem` elemento acepta solo un contexto valor. Para aplicar un contexto de segundo, cree un segundo `VisibilityItem` elemento al que apunta al mismo elemento, tal como se muestra en el ejemplo siguiente.  
  
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
 Los siguientes indicadores de comando pueden afectar a la visibilidad de los menús y comandos que se aplican.  
  
 AlwaysCreate  
 Menú se crea aunque no tiene botones ni grupos.  
  
 Válido para: `Menu`  
  
 CommandWellOnly  
 Aplicar esta marca si el comando no aparece en el menú de nivel superior y desea que esté disponible para la personalización de shell adicionales, por ejemplo, enlace a una clave. Después de instala el paquete VSPackage, un usuario puede personalizar estos comandos abriendo el **opciones** cuadro de diálogo y, a continuación, editar la ubicación de comando en el **teclado entorno** categoría. No afecta a la ubicación en los menús contextuales, barras de herramientas, controladores de menús o submenús.  
  
 Válido para: `Button`, `Combo`  
  
 DefaultDisabled  
 De forma predeterminada, el comando se deshabilita si el VSPackage que implemente el comando no está cargado o no se ha llamado al método QueryStatus.  
  
 Válido para: `Button`, `Combo`  
  
 DefaultInvisible  
 De forma predeterminada, el comando es invisible si el VSPackage que implemente el comando no está cargado o no se ha llamado al método QueryStatus.  
  
 Debe combinarse con la `DynamicVisibility` marca.  
  
 Válido para: `Button`, `Combo`, `Menu`  
  
 DynamicVisibility  
 Se puede cambiar la visibilidad del comando mediante el método QueryStatus o un contexto de GUID que se incluye en la `VisibilityConstraints` sección.  
  
 Se aplica a los comandos que aparecen en los menús, no en las barras de herramientas. Elementos de nivel superior de la barra de herramientas pueden deshabilitados, pero no ocultos, cuando se devuelve la marca OLECMDF_INVISIBLE desde el método QueryStatus.  
  
 En un menú, esta marca indica también que debería automáticamente ocultarse cuando sus miembros están ocultos. Esta marca se asigna normalmente a submenús ya menús de nivel superior ya cuentan con este comportamiento.  
  
 Debe combinarse con la `DefaultInvisible` marca.  
  
 Válido para: `Button`, `Combo`, `Menu`  
  
 NoShowOnMenuController  
 Si un comando que tiene este indicador se coloca en un controlador de menú, el comando no aparece en la lista desplegable.  
  
 Válido para: `Button`  
  
 Para obtener más información acerca de las marcas de comando, consulte el [comando marca elemento](../../extensibility/command-flag-element.md) documentación.  
  
##### <a name="general-requirements"></a>Requisitos generales  
 El comando debe pasar la siguiente serie de pruebas antes de que pueden mostrarse y habilitado:  
  
-   El comando se coloca correctamente.  
  
-   El `DefaultInvisible` no se estableció el marcador.  
  
-   El menú primario o la barra de herramientas está visible.  
  
-   El comando no es invisible debido a una entrada de contexto en el [VisibilityConstraints elemento](../../extensibility/visibilityconstraints-element.md) sección.  
  
-   Código de VSPackage que implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz muestra y permite el comando. Ningún código de interfaz interceptado y ha actuado sobre él.  
  
-   Cuando un usuario hace clic en el comando, se convierte en sujetos al procedimiento que se describe en [algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="calling-pre-defined-commands"></a>Comandos predefinido que realiza la llamada  
 El [UsedCommands elemento](../../extensibility/usedcommands-element.md) permite VSPackages para tener acceso a los comandos que se proporcionan mediante otros VSPackages o por el IDE. Para ello, cree un [UsedCommand elemento](../../extensibility/usedcommand-element.md) que tiene el GUID y el identificador del comando que se va a usar. Esto garantiza que el comando se cargarán para Visual Studio, incluso si no es parte de la configuración actual de Visual Studio. Para obtener más información, consulte [UsedCommand elemento](../../extensibility/usedcommand-element.md).  
  
## <a name="interface-element-appearance"></a>Apariencia del elemento de interfaz  
 Consideraciones para seleccionar y colocar elementos de comando son los siguientes:  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ofrece muchos elementos de interfaz de usuario que aparecen de manera diferente dependiendo de la selección de ubicación.  
  
-   Un elemento de interfaz de usuario que se define utilizando la `DefaultInvisible` marca no se mostrará en el IDE a menos que se muestran por su implementación de VSPackage de la <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> método, o asociado a un determinado contexto de interfaz de usuario en el `VisibilityConstraints` sección.  
  
-   No puede mostrarse incluso un comando colocado correctamente. Esto es porque el IDE automáticamente oculta o muestra algunos comandos, dependiendo de las interfaces que el VSPackage tiene (o no) implementa. Por ejemplo, implementación de un VSPackage de algunas crear interfaces de elementos de menú relacionadas con la compilación de las causas que se mostrará automáticamente.  
  
-   Aplicar el `CommandWellOnly` marca en la definición del elemento de interfaz de usuario significa que se puede agregar el comando solo por personalización.  
  
-   Comandos pueden estar disponibles solo en ciertos contextos de interfaz de usuario, por ejemplo, solo cuando un cuadro de diálogo se muestra cuando el IDE está en la vista Diseño.  
  
-   Para hacer que algunos elementos de interfaz de usuario que se mostrará en el IDE, debe implementar una o más interfaces o escribir parte del código.  
  
## <a name="see-also"></a>Vea también  
 [Ampliación de menús y comandos](../../extensibility/extending-menus-and-commands.md)