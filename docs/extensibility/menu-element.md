---
title: "Elemento de men&#250; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elementos de esquema XML VSCT, menús"
  - "Elemento de menús (esquema VSCT XML)"
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento de men&#250;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Define un elemento de menú. Estos son los seis tipos de menús: contexto, menú, MenuController, MenuControllerLatched, barra de herramientas y ToolWindowToolbar.  
  
## Sintaxis  
  
```  
<Menu guid=”guidMyCommandSet” id=”MyCommand” priority=”0x100” type=”button”>  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|GUID|Obligatorio. GUID del identificador de comando\/identificador GUID.|  
|id|Obligatorio. Id. del identificador de comando\/identificador GUID.|  
|priority|Opcional. Un valor numérico que especifica la posición relativa de un menú en un grupo de menús.|  
|ToolbarPriorityInBand|Opcional. Un valor numérico que especifica la posición relativa de una barra de herramientas en una banda de cuando la ventana está acoplada.|  
|tipo|Opcional. Un valor enumerado que especifica el tipo de elemento.<br /><br /> Si no está presente, el tipo predeterminado es el menú.<br /><br /> Contexto<br /> Menú contextual que aparece cuando un usuario hace clic con botón de una ventana. Un menú contextual tiene las siguientes características:<br /><br /> -   Utilice los campos de elemento primario y la prioridad cuando el menú se mostrarán como un menú contextual.<br />-   Puede utilizarse como un submenú y también como un menú contextual. En este caso, se respetan los campos Id. de grupo y prioridad.<br />-   No siempre está disponible.<br /><br /> Se mostrará un menú contextual sólo cuando se cumplan las condiciones siguientes:<br /><br /> -   Se muestra la ventana que lo hospeda.<br />-   Un controlador de mouse \(ratón\) en el paquete VSPackage detecta un con el botón secundario en la ventana y, a continuación, llama a un método que controla el comando.<br />-   Se muestra el menú contextual llamando el <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> método \(el enfoque recomendado\) o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> \(método\).<br /><br /> Menú<br /> Proporciona un menú desplegable. Un menú desplegable tiene las siguientes características:<br /><br /> -   Respeta al elemento primario en su definición.<br />-   Debe tener un grupo primario o un CommandPlacement a un grupo.<br />-   Puede ser un submenú en cualquier otro tipo de menú.<br />-   Se muestra automáticamente cada vez que se muestre el menú primario.<br />-   No requiere la implementación de cualquier código de VSPackage para hacer que se muestre.<br /><br /> MenuController<br /> Proporciona un menú desplegable de botón de división, que se utiliza normalmente en las barras de herramientas. Un menú MenuController tiene las siguientes características:<br /><br /> -   Debe estar incluido en otro menú a través de CommandPlacement o primario.<br />-   Respeta al elemento primario en su definición.<br />-   Puede tener cualquier tipo de menú como su elemento primario.<br />-   Se convierte automáticamente en disponible cuando se muestra el menú primario.<br />-   No requiere compatibilidad mediante programación para que el menú que aparece.<br /><br /> Un comando en el menú del botón de división se muestra en el botón de menú. El comando mostrado tiene una de las siguientes características:<br /><br /> -   Es el último comando que se utiliza si el comando sigue muestra y habilitado.<br />-   Es el primer comando mostrado.<br /><br /> MenuControllerLatched<br /> Proporciona un menú desplegable de botón de división para el que se puede especificar un comando como la selección predeterminada marcando el comando como bloqueado.<br /><br /> Un comando de cierre es un comando que está marcado como en el menú seleccionados, normalmente al mostrar una marca de verificación. Un comando se puede marcar como bloqueado si tiene la OLECMDF\_LATCHED marcador establecido en él en una implementación de la `QueryStatus` método de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Un menú MenuControllerLatched tiene las siguientes características:<br /><br /> -   Debe estar incluido en otro menú a través de un grupo primario o CommandPlacement.<br />-   Respeta al elemento primario en su definición.<br />-   Puede tener cualquier tipo de menú como su elemento primario.<br />-   Estará disponible cuando se muestra el menú primario.<br />-   No requiere compatibilidad mediante programación para que el menú que aparece.<br /><br /> Un comando en el menú del botón de división se muestra en el botón de menú. El comando mostrado tiene una de las siguientes características:<br /><br /> -   Es el primer comando muestra que está bloqueado.<br />-   Es el primer comando mostrado.<br /><br /> Barra de herramientas<br /> Proporciona una barra de herramientas. Una barra de herramientas tiene las siguientes características:<br /><br /> -   Omite al elemento primario en su definición.<br />-   No puede realizarse un submenú de grupo, ni siquiera con CommandPlacement.<br />-   Siempre puede mostrarse haciendo clic en **las barras de herramientas** en el **vista** menú.<br />-   Puede mostrarse mediante un [VisibilityItem](0932f551-972d-4194-84bb-426e3e4375e4Vis).<br />-   No se requiere ningún código para crearla. Para obtener un ejemplo sobre cómo crear una barra de herramientas, consulte [Agregar una barra de herramientas](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Proporciona una barra de herramientas que se adjunta a una ventana de herramienta específica, como una barra de herramientas está conectado al entorno de desarrollo.<br /><br /> -   Omite al elemento primario en su definición.<br />-   No puede realizarse un submenú de grupo, ni siquiera con CommandPlacement.<br />-   Sólo se muestra cuando se muestra la ventana de herramientas que hospeda la barra de herramientas y el VSPackage agrega explícitamente la barra de herramientas a la ventana de herramientas. Esto se hace normalmente cuando la ventana de herramientas se crea mediante la obtención de la propiedad de host de la barra de herramientas \(representado por la <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> interfaz\) del marco de ventana de herramientas y, a continuación, llamar al método el <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> método.|  
|Condición|Opcional. Vea [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|Elemento primario|Opcional. El elemento primario del elemento de menú.|  
|CommandFlag|Obligatorio. Vea [Elemento de indicador de comando](../extensibility/command-flag-element.md). Los valores válidos de CommandFlag para un menú son:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** \-esta marca no afecta a la presentación de las barras de herramientas.<br />-   **DontCache**<br />-   **DynamicVisibility** \-esta marca no afecta a la presentación de las barras de herramientas.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextoCambia**<br />-   **TextIsAnchorCommand**|  
|Cadenas|Obligatorio. Vea [Elemento de cadenas](../extensibility/strings-element.md). El elemento secundario `ButtonText` se debe definir el elemento.|  
|Anotación|Comentario opcional.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento de menús](../extensibility/menus-element.md)|Define todos los menús que implementa un VSPackage.|  
  
## Ejemplo  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget" priority="0x0002" type="Menu"> <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>Edit Widget</ButtonText> </Strings> </Parent> </Menu>  
```  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)