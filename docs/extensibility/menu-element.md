---
title: Elemento de menú ???????? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dc4731f95e31781f6b10704d7cb14dc83e96d7a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702596"
---
# <a name="menu-element"></a>Elemento de menú
Define un elemento de menú. Estos son los seis tipos de menús: Contexto, Menu, MenuController, MenuControllerLatched, Toolbar y ToolWindowToolbar.

## <a name="syntax"></a>Sintaxis

```xml
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">
  <Parent>... </Parent>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Menu>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Necesario. GUID del identificador de comando GUID/ID.|
|id|Necesario. ID del identificador de comando GUID/ID.|
|priority|Opcional. Valor numérico que especifica la posición relativa de un menú en un grupo de menús.|
|ToolbarPriorityInband|Opcional. Valor numérico que especifica la posición relativa de una barra de herramientas en una banda cuando se acopla la ventana.|
|type|Opcional. Un valor enumerado que especifica el tipo de elemento.<br /><br /> Si no está presente, el tipo predeterminado es Menú.<br /><br /> Context<br /> Un menú contextual que se muestra cuando un usuario hace clic con el botón derecho en una ventana. Un menú contextual tiene las siguientes características:<br /><br /> - No utiliza los campos **Padre** y **Prioridad** cuando el menú se va a mostrar como un menú contextual.<br />- Se puede utilizar como un submenú y también como un menú contextual. En este caso, se respetan los campos ID de **grupo** y **Prioridad.**<br />- No siempre está disponible.<br /><br /> Solo se muestra un menú contextual cuando se cumplen las siguientes condiciones:<br /><br /> - Se muestra la ventana que lo aloja.<br />- Un controlador de mouse en el VSPackage detecta un clic derecho en la ventana y, a continuación, llama a un método que controla el comando.<br />- El menú contextual se <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> muestra llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> (el enfoque recomendado) o al método.<br /><br /> Menú<br /> Proporciona un menú desplegable. Un menú desplegable tiene las siguientes características:<br /><br /> - Respeta al Padre en su definición.<br />- Debe tener un grupo Padre o un CommandPlacement en un grupo.<br />- Puede ser un submenú en cualquier otro tipo de menú.<br />- Se muestra automáticamente cada vez que se muestra su menú principal.<br />- No requiere la implementación de ningún código VSPackage para que se muestre.<br /><br /> MenuController<br /> Proporciona un menú desplegable de botones divididos, que normalmente se utiliza en las barras de herramientas. Un menú MenuController tiene las siguientes características:<br /><br /> - Debe estar contenido en otro menú a través de Parent o CommandPlacement.<br />- Respeta al Padre en su definición.<br />- Puede tener cualquier tipo de menú como su padre.<br />- Se hace automáticamente disponible cada vez que se muestra su menú principal.<br />- No requiere soporte programático para que se muestre el menú.<br /><br /> En el botón de menú se muestra un comando del menú de botones divididos. El comando mostrado tiene una de las siguientes características:<br /><br /> - Es el último comando que se utilizó si el comando todavía se muestra y se habilita.<br />- Es el primer comando mostrado.<br /><br /> MenuControllerLatched<br /> Proporciona un menú desplegable de botones divididos para el que se puede especificar un comando como la selección predeterminada marcando el comando como bloqueado.<br /><br /> Un comando bloqueado es un comando que se marca en el menú como seleccionado, normalmente mostrando una marca de verificación. Un comando se puede marcar como bloqueado si tiene el indicador `QueryStatus` OLECMDF_LATCHED establecido <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> en él en una implementación del método de la interfaz. Un menú MenuControllerLatched tiene las siguientes características:<br /><br /> - Debe estar contenido en otro menú a través de un grupo Padre o CommandPlacement.<br />- Respeta al Padre en su definición.<br />- Puede tener cualquier tipo de menú como su padre.<br />- Se hace disponible cada vez que se muestra su menú principal.<br />- No requiere soporte programático para que se muestre el menú.<br /><br /> En el botón de menú se muestra un comando del menú de botones divididos. El comando mostrado tiene una de las siguientes características:<br /><br /> - Es el primer comando mostrado que está bloqueado.<br />- Es el primer comando mostrado.<br /><br /> Barra de herramientas<br /> Proporciona una barra de herramientas. Una barra de herramientas tiene las siguientes características:<br /><br /> - Ignora al padre en su definición.<br />- No se puede hacer un submenú de ningún grupo, ni siquiera mediante CommandPlacement.<br />- Siempre se puede mostrar haciendo clic en Barras de **herramientas** en el menú **Ver.**<br />- Se puede mostrar mediante un [VisibilityItem](../extensibility/visibilityitem-element.md).<br />- No requiere ningún código para crearlo. Para obtener un ejemplo sobre cómo crear una barra de herramientas, consulte [Agregar una barra](../extensibility/adding-a-toolbar.md)de herramientas .<br /><br /> ToolWindowToolbar<br /> Proporciona una barra de herramientas que se adjunta a una ventana de herramientas específica, al igual que una barra de herramientas se adjunta al entorno de desarrollo.<br /><br /> - Ignora al padre en su definición.<br />- No se puede hacer un submenú de ningún grupo, ni siquiera mediante CommandPlacement.<br />- Se muestra solo cuando se muestra la ventana de herramientas que hospeda la barra de herramientas y el VSPackage agrega explícitamente la barra de herramientas a la ventana de herramientas. Esto se realiza normalmente cuando se crea la ventana de herramientas obteniendo la propiedad host de la barra de herramientas (representada por la <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> interfaz) desde el marco de la ventana de herramientas y, a continuación, llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> método.|
|Condición|Opcional. Consulte [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Parent|Opcional. El elemento primario del elemento de menú.|
|CommandFlag|Necesario. Consulte [Elemento de indicador de comando](../extensibility/command-flag-element.md). Los valores commandFlag válidos para un menú son los siguientes:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible:** esta marca no afecta a la visualización de las barras de herramientas.<br />-   **DontCache**<br />-   **DynamicVisibility:** esta marca no afecta a la visualización de barras de herramientas.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|
|Cadenas|Necesario. Consulte [Elemento Cadenas](../extensibility/strings-element.md). El `ButtonText` elemento secundario debe definirse.|
|Anotación|Comentario opcional.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Menús](../extensibility/menus-element.md)|Define todos los menús que implementa un VSPackage.|

## <a name="example"></a>Ejemplo

```
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"
  priority="0x0002" type="Menu">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <CommandFlag>AlwaysCreate</CommandFlag>
    <Strings>
      <ButtonText>Edit Widget</ButtonText>
    </Strings>
    </Parent>
</Menu>
```

## <a name="see-also"></a>Consulte también
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
