---
title: "Elemento VisibilityItem | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elemento VisibilityItem (esquema VSCT XML)"
  - "Elementos de esquema XML VSCT, VisibilityItem"
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Elemento VisibilityItem
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El `VisibilityItem` elemento determina la visibilidad estática de los comandos y las barras de herramientas. Cada entrada identifica un comando o menú y también un contexto de interfaz de usuario de comando asociado. Visual Studio detecta comandos, menús y barras de herramientas y su visibilidad, sin necesidad de cargar los VSPackages que los definen. El IDE utiliza la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> método para determinar si un contexto de la interfaz de usuario de comando está activo.  
  
 Una vez cargado el VSPackage, Visual Studio espera visibilidad de comando que determinará el VSPackage en lugar de `VisibilityItem`. Para determinar la visibilidad de los comandos, puede implementar la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> controlador de eventos o la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> \(método\), dependiendo de cómo haya implementado el comando.  
  
 Un comando o un menú que tiene un `VisibilityItem` elemento aparece sólo cuando está activo el contexto asociado. Puede asociar un único comando, el menú o la barra de herramientas con uno o más contextos de la interfaz de usuario de comando mediante la inclusión de una entrada para cada combinación de contexto de los comandos. Si un comando o un menú está asociado a varios contextos de interfaz de usuario de comando, a continuación, el comando o el menú es visible cuando se active cualquiera de los contextos de la interfaz de usuario de comando asociado.  
  
 El `VisibilityItem` elemento solo se aplica a comandos, menús y barras de herramientas, no a grupos. Un elemento que no tiene un relacionados `VisibilityItem` elemento está visible cuando está activo el menú primario.  
  
## Sintaxis  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|GUID|Obligatorio. El GUID del identificador de comando\/identificador GUID.|  
|id|Obligatorio. Id. del identificador de comando\/identificador GUID.|  
|contexto|Obligatorio. El contexto de la interfaz de usuario en el que el comando está visible.|  
|Condición|Opcional. Vea [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementos secundarios  
 Ninguno  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|El `VisibilityConstraints` elemento determina la visibilidad de los grupos de barras de herramientas y comandos estática.|  
  
## Comentarios  
 Los contextos de la interfaz de usuario de Visual Studio estándares se definen en el *ruta de instalación del SDK de Visual Studio*\\VisualStudioIntegration\\Common\\Inc\\vsshlids.h archivo así como en la <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> y <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> clases. Se define un conjunto más completo de contextos de la interfaz de usuario en el <xref:Microsoft.VisualStudio.VSConstants> clase.  
  
## Ejemplo  
  
```  
<VisibilityConstraints> <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget" context="guidNotViewSourceMode"/> </VisibilityConstraints>  
```  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)   
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)