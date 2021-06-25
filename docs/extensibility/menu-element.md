---
title: Elemento Menu | Microsoft Docs
description: El elemento Menu define un elemento de menú. Los tipos de menú son Context, Menu, MenuController, MenuControllerLatched, Toolbar y ToolWindowToolbar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a2ffa029dd05e7fe3d32a9df4a1d06c90c8b9c6b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901544"
---
# <a name="menu-element"></a>Elemento Menu
Define un elemento de menú. Estos son los seis tipos de menús: Context, Menu, MenuController, MenuControllerLatched, Toolbar y ToolWindowToolbar.

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
|id|Necesario. Identificador del identificador de comando GUID/ID.|
|priority|Opcional. Valor numérico que especifica la posición relativa de un menú en un grupo de menús.|
|ToolbarPriorityInBand|Opcional. Valor numérico que especifica la posición relativa de una barra de herramientas en una banda cuando la ventana está acoplada.|
|type|Opcional. Valor enumerado que especifica el tipo de elemento.<br /><br /> Si no está presente, el tipo predeterminado es Menu.<br /><br /> Contexto<br /> Menú contextual que se muestra cuando un usuario hace clic con el botón derecho en una ventana. Un menú contextual tiene las siguientes características:<br /><br /> - No usa los campos **Primario** y **Prioridad** cuando el menú se va a mostrar como un menú contextual.<br />: se puede usar como submenú y también como menú contextual. En este caso, se **respetan los campos** **Id.** de grupo y Prioridad.<br />- No siempre está disponible.<br /><br /> Solo se muestra un menú contextual cuando se cumplen las condiciones siguientes:<br /><br /> : se muestra la ventana que la hospeda.<br />- Un controlador del mouse del VSPackage detecta un clic con el botón derecho en la ventana y, a continuación, llama a un método que controla el comando.<br />- El menú contextual se muestra llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> método (el enfoque recomendado) o al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> método .<br /><br /> Menú<br /> Proporciona un menú desplegable. Un menú desplegable tiene las siguientes características:<br /><br /> : respeta el elemento primario en su definición.<br />- Debe tener un grupo primario o commandPlacement en un grupo.<br />- Puede ser un submenú en cualquier otro tipo de menú.<br />: se muestra automáticamente cada vez que se muestra su menú primario.<br />- No requiere la implementación de ningún código VSPackage para que se muestre.<br /><br /> MenuController<br /> Proporciona un menú desplegable de botón de división, que normalmente se usa en las barras de herramientas. Un menú MenuController tiene las siguientes características:<br /><br /> - Debe estar contenido en otro menú a través de Parent o CommandPlacement.<br />: respeta el elemento primario en su definición.<br />: puede tener cualquier tipo de menú como elemento primario.<br />: está disponible automáticamente cada vez que se muestra su menú primario.<br />- No requiere compatibilidad mediante programación para que se muestre el menú.<br /><br /> En el botón de menú se muestra un comando del menú de botón de división. El comando mostrado tiene una de las siguientes características:<br /><br /> - Es el último comando que se usó si el comando todavía se muestra y se habilita.<br />: es el primer comando que se muestra.<br /><br /> MenuControllerLatched<br /> Proporciona un menú desplegable de botón de división para el que se puede especificar un comando como selección predeterminada marcando el comando como bloqueos de bloqueos.<br /><br /> Un comando con bloqueos latched es un comando que se marca en el menú como seleccionado, normalmente mostrando una marca de verificación. Un comando se puede marcar como con bloqueos OLECMDF_LATCHED marca establecida en él en una implementación del `QueryStatus` método de la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . Un menú MenuControllerLatched tiene las siguientes características:<br /><br /> - Debe estar contenido en otro menú a través de un grupo primario o CommandPlacement.<br />: respeta el elemento primario en su definición.<br />: puede tener cualquier tipo de menú como elemento primario.<br />: está disponible cada vez que se muestra su menú primario.<br />- No requiere compatibilidad mediante programación para que se muestre el menú.<br /><br /> En el botón de menú se muestra un comando del menú de botón de división. El comando mostrado tiene una de las siguientes características:<br /><br /> - Es el primer comando que se muestra con bloqueos de bloqueos.<br />: es el primer comando que se muestra.<br /><br /> Barra de herramientas<br /> Proporciona una barra de herramientas. Una barra de herramientas tiene las siguientes características:<br /><br /> : omite el elemento primario en su definición.<br />- No se puede convertir en un submenú de ningún grupo, ni siquiera mediante CommandPlacement.<br />- Siempre se puede mostrar haciendo clic en **Barras de herramientas** en el **menú** Ver.<br />: se puede mostrar mediante [visibilityItem](../extensibility/visibilityitem-element.md).<br />: no requiere ningún código para crearlo. Para obtener un ejemplo sobre cómo crear una barra de herramientas, vea [Agregar una barra de herramientas](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Proporciona una barra de herramientas que está asociada a una ventana de herramientas específica, igual que una barra de herramientas está asociada al entorno de desarrollo.<br /><br /> : omite el elemento primario en su definición.<br />- No se puede convertir en un submenú de ningún grupo, ni siquiera mediante CommandPlacement.<br />- Solo se muestra cuando se muestra la ventana de herramientas que hospeda la barra de herramientas y el VSPackage agrega explícitamente la barra de herramientas a la ventana de herramientas. Esto suele hacerse cuando se crea la ventana de herramientas mediante la obtención de la propiedad host de la barra de herramientas (representada por la interfaz) del marco de la ventana de herramientas y, a continuación, llamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> al <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> método .|
|Condición|Opcional. Vea [Atributos condicionales.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Parent|Opcional. Elemento primario del elemento de menú.|
|CommandFlag|Necesario. Vea [Elemento de marca command](../extensibility/command-flag-element.md). Los valores de CommandFlag válidos para un menú son los siguientes:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible:** esta marca no afecta a la presentación de las barras de herramientas.<br />-   **DontCache**<br />-   **DynamicVisibility:** esta marca no afecta a la presentación de las barras de herramientas.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|
|Cadenas|Necesario. Vea [Elemento Strings](../extensibility/strings-element.md). Se debe `ButtonText` definir el elemento secundario.|
|Anotación|Comentario opcional.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Menus](../extensibility/menus-element.md)|Define todos los menús que implementa un VSPackage.|

## <a name="example"></a>Ejemplo

```
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"
  priority="0x0002" type="Menu">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"/>
  <CommandFlag>AlwaysCreate</CommandFlag>
  <Strings>
    <ButtonText>Edit Widget</ButtonText>
  </Strings>
</Menu>
```

## <a name="see-also"></a>Consulte también
- [Visual Studio archivos de tabla de comandos (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
