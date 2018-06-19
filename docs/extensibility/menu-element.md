---
title: Elemento de menú | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5c44ca8a78a331d66d099b8d141c4b66c1144949
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143457"
---
# <a name="menu-element"></a>Elemento de menú
Define un elemento de menú. Se trata de los seis tipos de menús: contexto, un menú, MenuController, MenuControllerLatched, barra de herramientas y ToolWindowToolbar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
|guid|Requerido. GUID del identificador de comando/identificador GUID.|  
|id|Requerido. Id. del identificador de comando/identificador GUID.|  
|priority|Opcional. Un valor numérico que especifica la posición relativa de un menú en un grupo de menús.|  
|ToolbarPriorityInBand|Opcional. Un valor numérico que especifica la posición relativa de una barra de herramientas en una banda cuando la ventana se acopla.|  
|type|Opcional. Un valor enumerado que especifica el tipo de elemento.<br /><br /> Si no está presente, el tipo predeterminado es el menú.<br /><br /> Contexto<br /> Un menú contextual que se muestra cuando un usuario hace clic con botón de una ventana. Un menú contextual tiene las siguientes características:<br /><br /> -No utiliza los campos de elemento primario y la prioridad cuando se en el menú que se mostrará como un menú contextual.<br />-Puede utilizarse como un submenú y también como un menú contextual. En este caso, se respetan los campos Id. de grupo y prioridad.<br />: Es no siempre está disponible.<br /><br /> Un menú contextual se muestra sólo cuando se cumplan las condiciones siguientes:<br /><br /> : Se muestra la ventana que lo hospeda.<br />-Un controlador de mouse (ratón) en el VSPackage detecta un menú contextual en la ventana y, a continuación, llama a un método que controla el comando.<br />-El menú contextual se muestra mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> método (el enfoque recomendado) o la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> método.<br /><br /> Menú<br /> Proporciona un menú desplegable. Un menú desplegable tiene las siguientes características:<br /><br /> -Respeta al elemento primario en su definición.<br />-Debe tener un grupo primario o un CommandPlacement a un grupo.<br />-Puede ser un submenú en cualquier otro tipo de menú.<br />-Se muestra automáticamente cada vez que se muestra el menú primario.<br />-No requiere la implementación de cualquier código de VSPackage para que se muestren.<br /><br /> MenuController<br /> Proporciona un menú de lista desplegable del botón de expansión, que se utiliza normalmente en las barras de herramientas. Un menú MenuController tiene las siguientes características:<br /><br /> -Debe estar incluido en otro menú a través de primario o CommandPlacement.<br />-Respeta al elemento primario en su definición.<br />-Puede tener cualquier tipo de menú como su elemento primario.<br />-Se realiza automáticamente disponible cada vez que se muestra el menú primario.<br />-No requiere soporte técnico mediante programación para realizar el menú que se muestra.<br /><br /> Un comando en el menú del botón de expansión se muestra en el botón de menú. El comando muestra no tiene una de las siguientes características:<br /><br /> -Es el último comando que se usa si el comando es todavía aparece y está activado.<br />-Es el primer comando mostrado.<br /><br /> MenuControllerLatched<br /> Proporciona un menú de lista desplegable del botón de expansión para el que se puede especificar un comando como la selección predeterminada marcando el comando tal y como se establece.<br /><br /> Un comando bloqueado es un comando que está marcado en el menú de la forma seleccionada, por lo general, mostrando una marca de verificación. Un comando se puede marcar como establece si tiene la OLECMDF_LATCHED marcador establecido en él en una implementación de la `QueryStatus` método de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Un menú MenuControllerLatched tiene las siguientes características:<br /><br /> -Debe estar incluido en otro menú a través de un grupo primario o CommandPlacement.<br />-Respeta al elemento primario en su definición.<br />-Puede tener cualquier tipo de menú como su elemento primario.<br />-Debe ponerse a disposición cada vez que se muestra el menú primario.<br />-No requiere soporte técnico mediante programación para realizar el menú que se muestra.<br /><br /> Un comando en el menú del botón de expansión se muestra en el botón de menú. El comando muestra no tiene una de las siguientes características:<br /><br /> -Es el primer comando muestra que se establece.<br />-Es el primer comando mostrado.<br /><br /> Barra de herramientas<br /> Proporciona una barra de herramientas. Una barra de herramientas tiene las siguientes características:<br /><br /> -Omite al elemento primario en su definición.<br />-No puede hacerse un submenú de un grupo, ni siquiera mediante CommandPlacement.<br />-Puede siempre se muestra al hacer clic **las barras de herramientas** en el **vista** menú.<br />-Puede mostrarse mediante un [VisibilityItem](../extensibility/visibilityitem-element.md).<br />-No requiere ningún código para crearla. Para obtener un ejemplo sobre cómo crear una barra de herramientas, consulte [agregar una barra de herramientas](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Proporciona una barra de herramientas que se adjunta a una ventana de herramientas específica, como una barra de herramientas está conectado al entorno de desarrollo.<br /><br /> -Omite al elemento primario en su definición.<br />-No puede hacerse un submenú de un grupo, ni siquiera mediante CommandPlacement.<br />-Se muestra solo cuando se muestra la ventana de herramientas que hospeda la barra de herramientas y el VSPackage agrega explícitamente la barra de herramientas a la ventana de herramientas. Esto se hace normalmente cuando la ventana de herramientas se crea mediante la obtención de la propiedad de host de la barra de herramientas (representado por la <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> interfaz) del marco de ventana de herramientas y, a continuación, llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> método.|  
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Elemento primario|Opcional. El elemento primario del elemento de menú.|  
|CommandFlag|Requerido. Vea [comando marca elemento](../extensibility/command-flag-element.md). Los valores de CommandFlag válidos para un menú son como sigue:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -esta marca no afecta a la presentación de las barras de herramientas.<br />-   **DontCache**<br />-   **DynamicVisibility** -esta marca no afecta a la presentación de las barras de herramientas.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextoCambia**<br />-   **TextIsAnchorCommand**|  
|Cadenas|Requerido. Vea [cadenas elemento](../extensibility/strings-element.md). El elemento secundario `ButtonText` debe definirse el elemento.|  
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