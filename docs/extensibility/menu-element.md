---
title: Elemento menu | Microsoft Docs
description: El elemento de menú define un elemento de menú. Los tipos de menú son contexto, menú, MenuController, MenuControllerLatched, barra de herramientas y ToolWindowToolbar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7427b826249bd29c73c928630eed0941c57b997d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064051"
---
# <a name="menu-element"></a>Elemento menu
Define un elemento de menú. Estos son los seis tipos de menús: context, MENU, MenuController, MenuControllerLatched, Toolbar y ToolWindowToolbar.

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
|guid|Necesario. GUID del identificador del comando GUID/ID.|
|id|Necesario. IDENTIFICADOR del identificador del comando GUID/ID.|
|priority|Opcional. Valor numérico que especifica la posición relativa de un menú en un grupo de menús.|
|ToolbarPriorityInBand|Opcional. Valor numérico que especifica la posición relativa de una barra de herramientas en una banda cuando la ventana está acoplada.|
|type|Opcional. Valor enumerado que especifica el tipo de elemento.<br /><br /> Si no está presente, el tipo predeterminado es menú.<br /><br /> Context<br /> Un menú contextual que se muestra cuando un usuario hace clic con el botón secundario en una ventana. Un menú contextual tiene las siguientes características:<br /><br /> : No usa los campos **primario** y de **prioridad** cuando el menú se va a mostrar como menú contextual.<br />-Se puede usar como un submenú y también como un menú contextual. En este caso, se respetan los campos ID. de **Grupo** y **prioridad** .<br />-No siempre está disponible.<br /><br /> Solo se muestra un menú contextual cuando se cumplen las condiciones siguientes:<br /><br /> -Se muestra la ventana que la hospeda.<br />-Un controlador de mouse en el VSPackage detecta un clic con el botón secundario en la ventana y, a continuación, llama a un método que controla el comando.<br />: El menú contextual se muestra mediante una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> método (el enfoque recomendado) o el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> método.<br /><br /> Menú<br /> Proporciona un menú desplegable. Un menú desplegable tiene las siguientes características:<br /><br /> : Respeta el elemento primario en su definición.<br />-Debe tener un grupo primario o un CommandPlacement a un grupo.<br />: Puede ser un submenú de cualquier otro tipo de menú.<br />-Se muestra automáticamente cuando se muestra el menú primario.<br />: No requiere la implementación de ningún código VSPackage para que se muestre.<br /><br /> MenuController<br /> Proporciona un menú desplegable de botón de expansión, que se utiliza normalmente en las barras de herramientas. Un menú MenuController tiene las siguientes características:<br /><br /> : Debe estar incluido en otro menú a través de los elementos primarios o CommandPlacement.<br />: Respeta el elemento primario en su definición.<br />: Puede tener cualquier tipo de menú como elemento primario.<br />-Está disponible automáticamente cada vez que se muestra el menú primario.<br />: No requiere compatibilidad mediante programación para que se muestre el menú.<br /><br /> Un comando del menú de botón de expansión se muestra en el botón de menú. El comando que se muestra tiene una de las siguientes características:<br /><br /> -Es el último comando que se usó si el comando sigue mostrándose y habilitado.<br />-Es el primer comando que se muestra.<br /><br /> MenuControllerLatched<br /> Proporciona un menú desplegable de botón de expansión para el que se puede especificar un comando como selección predeterminada marcando el comando como bloqueado.<br /><br /> Un comando bloqueado es un comando que se marca en el menú como seleccionado, normalmente mostrando una marca de verificación. Un comando se puede marcar como bloqueado si tiene la marca OLECMDF_LATCHED establecida en él en una implementación del `QueryStatus` método de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Un menú MenuControllerLatched tiene las siguientes características:<br /><br /> -Debe estar incluido en otro menú a través de un grupo primario o CommandPlacement.<br />: Respeta el elemento primario en su definición.<br />: Puede tener cualquier tipo de menú como elemento primario.<br />-Está disponible cada vez que se muestra el menú primario.<br />: No requiere compatibilidad mediante programación para que se muestre el menú.<br /><br /> Un comando del menú de botón de expansión se muestra en el botón de menú. El comando que se muestra tiene una de las siguientes características:<br /><br /> -Es el primer comando que se muestra que está bloqueado.<br />-Es el primer comando que se muestra.<br /><br /> Barra de herramientas<br /> Proporciona una barra de herramientas. Una barra de herramientas tiene las siguientes características:<br /><br /> -Omite el elemento primario en su definición.<br />-No se puede convertir en un submenú de ningún grupo, ni siquiera mediante CommandPlacement.<br />-Siempre se puede mostrar haciendo clic en **barras de herramientas** en el menú **Ver** .<br />-Se puede mostrar mediante un [VisibilityItem](../extensibility/visibilityitem-element.md).<br />-No requiere código para crearlo. Para obtener un ejemplo sobre cómo crear una barra de herramientas, vea [Agregar una barra de herramientas](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Proporciona una barra de herramientas que se adjunta a una ventana de herramientas específica, al igual que una barra de herramientas se adjunta al entorno de desarrollo.<br /><br /> -Omite el elemento primario en su definición.<br />-No se puede convertir en un submenú de ningún grupo, ni siquiera mediante CommandPlacement.<br />-Solo se muestra cuando se muestra la ventana de herramientas que hospeda la barra de herramientas y el VSPackage agrega explícitamente la barra de herramientas a la ventana de herramientas. Normalmente, esto se hace cuando se crea la ventana de herramientas mediante la obtención de la propiedad de host de barra de herramientas (tal y como se representa en la <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> interfaz) desde el marco de la ventana de herramientas y, después, llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> método.|
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Parent|Opcional. Elemento primario del elemento de menú.|
|CommandFlag|Necesario. Vea [elemento de marca de comando](../extensibility/command-flag-element.md). Los valores válidos de CommandFlag para un menú son los siguientes:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** : esta marca no afecta a la presentación de barras de herramientas.<br />-   **DontCache**<br />-   **DynamicVisibility** : esta marca no afecta a la presentación de barras de herramientas.<br />-   **IconAndText**<br />-   **Nocustomizate**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **Textchanges al**<br />-   **TextIsAnchorCommand**|
|Cadenas|Necesario. Vea el [elemento Strings](../extensibility/strings-element.md). `ButtonText`Se debe definir el elemento secundario.|
|Anotación|Comentario opcional.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Menus (elemento)](../extensibility/menus-element.md)|Define todos los menús que implementa un VSPackage.|

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
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
