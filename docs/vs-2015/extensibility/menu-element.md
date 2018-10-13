---
title: Elemento de menú | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9326364e6182441fc3da095cd1cd36a7cb2ed207
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242275"
---
# <a name="menu-element"></a>Menu (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Define un elemento de menú. Estos son los seis tipos de menús: contexto, un menú, MenuController, MenuControllerLatched, barra de herramientas y ToolWindowToolbar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Menu guid=”guidMyCommandSet” id=”MyCommand” priority=”0x100” type=”button”>  
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
|guid|Requerido. GUID del identificador de comando/identificador de GUID.|  
|id|Requerido. Id. del identificador de comando/identificador de GUID.|  
|priority|Opcional. Un valor numérico que especifica la posición relativa de un menú en un grupo de menús.|  
|ToolbarPriorityInBand|Opcional. Un valor numérico que especifica la posición relativa de una barra de herramientas en una banda cuando la ventana está acoplada.|  
|type|Opcional. Un valor enumerado que especifica el tipo de elemento.<br /><br /> Si no está presente, el tipo predeterminado es el menú.<br /><br /> Contexto<br /> Un menú contextual que se muestra cuando un usuario hace clic con botón de una ventana. Un menú contextual tiene las siguientes características:<br /><br /> -No utiliza los campos de elemento primario y la prioridad cuando el menú se mostrarán como un menú contextual.<br />-Puede utilizarse como un submenú y también como un menú contextual. En este caso, se respetan los campos de Id. de grupo y prioridad.<br />: Es no siempre está disponible.<br /><br /> Se muestra un menú contextual sólo cuando se cumplan las condiciones siguientes:<br /><br /> : Se muestra la ventana que lo hospeda.<br />-Un controlador del mouse en el VSPackage detecta un botón secundario en la ventana y, a continuación, llama a un método que controla el comando.<br />-En el menú contextual se muestra mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> método (el enfoque recomendado) o el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> método.<br /><br /> Menú<br /> Proporciona un menú desplegable. Un menú desplegable tiene las siguientes características:<br /><br /> -Respeta al elemento primario en su definición.<br />-Debe tener un grupo primario o un CommandPlacement a un grupo.<br />-Puede ser un submenú en cualquier otro tipo de menú.<br />-Se muestra automáticamente cada vez que se muestra el menú primario.<br />-No requiere la implementación de cualquier código VSPackage para que se muestren.<br /><br /> MenuController<br /> Proporciona un menú desplegable de botón de expansión, que se utiliza normalmente en las barras de herramientas. Un menú MenuController tiene las siguientes características:<br /><br /> -Debe estar incluido en otro menú a través de primario o CommandPlacement.<br />-Respeta al elemento primario en su definición.<br />-Puede tener cualquier tipo de menú como su elemento primario.<br />-Está automáticamente disponible cada vez que se muestra el menú primario.<br />-No requiere soporte técnico de programación para que el menú que aparece.<br /><br /> Un comando en el menú del botón de expansión se muestra en el botón de menú. El comando muestra tiene una de las siguientes características:<br /><br /> -Es el último comando que se usa si el comando todavía se muestra y habilitado.<br />-Es el primer comando mostrado.<br /><br /> MenuControllerLatched<br /> Proporciona un menú desplegable de botón de expansión para el que se puede especificar un comando como la selección predeterminada marcando el comando como activado.<br /><br /> Un comando bloqueado temporalmente es un comando que está marcado como en el menú seleccionados, normalmente al mostrar una marca de verificación. Un comando se puede marcar como activado si tiene la OLECMDF_LATCHED establecido en él en la implementación de la `QueryStatus` método de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Un menú MenuControllerLatched tiene las siguientes características:<br /><br /> -Debe estar incluido en otro menú a través de un grupo primario o CommandPlacement.<br />-Respeta al elemento primario en su definición.<br />-Puede tener cualquier tipo de menú como su elemento primario.<br />-Está disponible cada vez que se muestra el menú primario.<br />-No requiere soporte técnico de programación para que el menú que aparece.<br /><br /> Un comando en el menú del botón de expansión se muestra en el botón de menú. El comando muestra tiene una de las siguientes características:<br /><br /> -Es el primer comando muestra que está bloqueado.<br />-Es el primer comando mostrado.<br /><br /> Barra de herramientas<br /> Proporciona una barra de herramientas. Una barra de herramientas tiene las siguientes características:<br /><br /> -Omite al elemento primario en su definición.<br />-No se puede realizar un submenú de grupo, ni siquiera mediante el uso de CommandPlacement.<br />-Puede siempre se muestra al hacer clic **las barras de herramientas** en el **vista** menú.<br />-Puede mostrarse mediante un [VisibilityItem](../extensibility/visibilityitem-element.md).<br />-No requiere ningún código para crearla. Para obtener un ejemplo sobre cómo crear una barra de herramientas, consulte [agregar una barra de herramientas](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Proporciona una barra de herramientas que se adjunta a una ventana de herramientas específica, tal como una barra de herramientas está asociado al entorno de desarrollo.<br /><br /> -Omite al elemento primario en su definición.<br />-No se puede realizar un submenú de grupo, ni siquiera mediante el uso de CommandPlacement.<br />-Solo se muestra cuando se muestra la ventana de herramientas que hospeda la barra de herramientas y el VSPackage agrega explícitamente la barra de herramientas a la ventana de herramientas. Esto se hace normalmente cuando se crea la ventana de herramientas mediante la obtención de la propiedad de host de la barra de herramientas (tal como está representada por la <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> interfaz) en el marco de ventana de herramientas y, a continuación, que realiza la llamada la <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> método.|  
|Condición|Opcional. Consulte [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Elemento primario|Opcional. El elemento primario del elemento de menú.|  
|CommandFlag|Requerido. Consulte [Command Flag (elemento)](../extensibility/command-flag-element.md). Los valores válidos de CommandFlag para un menú son como sigue:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -esta marca no afecta a la presentación de las barras de herramientas.<br />-   **DontCache**<br />-   **DynamicVisibility** -esta marca no afecta a la presentación de las barras de herramientas.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextoCambia**<br />-   **TextIsAnchorCommand**|  
|Cadenas|Requerido. Consulte [cadenas elemento](../extensibility/strings-element.md). El elemento secundario `ButtonText` debe definirse el elemento.|  
|Anotación|Comentario opcional.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Menus (Elemento)](../extensibility/menus-element.md)|Define todos los menús que implementa un paquete VSPackage.|  
  
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
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)