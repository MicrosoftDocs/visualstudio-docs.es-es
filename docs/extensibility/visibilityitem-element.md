---
title: Elemento VisibilityItem | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85cc2a3d65d5a4763aeca231175201cf55a74b3e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="visibilityitem-element"></a>Elemento VisibilityItem
El `VisibilityItem` elemento determina la visibilidad estática de comandos y las barras de herramientas. Cada entrada identifica un comando o menú y también un contexto de la interfaz de usuario de comando asociado. Visual Studio detecta comandos, menús y barras de herramientas y su visibilidad, sin necesidad de cargar los VSPackages que definirlos. El IDE usa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> método para determinar si un contexto de la interfaz de usuario de comando está activo.  
  
 Después de carga el VSPackage, Visual Studio espera visibilidad de comando quedará determinado por el VSPackage en lugar de la `VisibilityItem`. Para determinar la visibilidad del comando, puede implementar la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> controlador de eventos o la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método, dependiendo de cómo haya implementado el comando.  
  
 Un comando o un menú con un `VisibilityItem` elemento aparece solo cuando el contexto asociado está activo. Puede asociar un único comando, el menú o la barra de herramientas con uno o varios contextos de interfaz de usuario de comandos mediante la inclusión de una entrada para cada combinación de contexto de los comandos. Si un comando o un menú está asociado a varios contextos de interfaz de usuario de comando, a continuación, el comando o el menú es visible cuando cualquiera de los contextos de la interfaz de usuario de comando asociado está activo.  
  
 El `VisibilityItem` elemento solo se aplica a comandos, menús y barras de herramientas, no a grupos. Un elemento que no tiene un relacionados `VisibilityItem` elemento está visible cuando está activo el menú primario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|guid|Requerido. El GUID del identificador de comando/identificador GUID.|  
|id|Requerido. El Id. del identificador de comando/identificador GUID.|  
|contexto|Requerido. El contexto de la interfaz de usuario en el que el comando es visible.|  
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguna  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[VisibilityConstraints (Elemento)](../extensibility/visibilityconstraints-element.md)|El `VisibilityConstraints` elemento determina la visibilidad de los grupos de comandos y las barras de herramientas estática.|  
  
## <a name="remarks"></a>Comentarios  
 Los contextos de interfaz de usuario de Visual Studio estándares se definen en el *ruta de instalación del SDK de Visual Studio*\VisualStudioIntegration\Common\Inc\vsshlids.h archivo así como en la <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> y <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> clases. Se define un conjunto más completo de contextos de la interfaz de usuario en el <xref:Microsoft.VisualStudio.VSConstants> clase.  
  
## <a name="example"></a>Ejemplo  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)   
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)