---
title: Interfaz de usuario de propiedades del proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 36d8f6afebf09d4efd176ba204dcc6f485a56124
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="project-property-user-interface"></a>Interfaz de usuario de propiedades de proyecto
Un subtipo de proyecto puede utilizar los elementos en el proyecto **páginas de propiedades** cuadro de diálogo tal y como se proporcionan por el proyecto de base, ocultar o realizar controles de solo lectura y páginas completas tal como lo suministró o agregar páginas específicas de subtipo del proyecto a la **Páginas de propiedades** cuadro de diálogo.  
  
## <a name="extending-the-project-property-dialog-box"></a>Ampliar el cuadro de diálogo de propiedades de proyecto  
 Un subtipo de proyecto implementa extensores de automatización y examinar objetos de configuración de proyecto. Implementa estos extender la <xref:EnvDTE.IFilterProperties> interfaz para realizar determinadas propiedades oculto o de solo lectura. El **páginas de propiedades** cuadro de diálogo del proyecto de base, implementado por el proyecto de base, respeta el filtrado realizado por los extensores de automatización.  
  
 El proceso de extender un **propiedad del proyecto** cuadro de diálogo se indica a continuación:  
  
-   El proyecto de base recupera los extensores desde el subtipo de proyecto mediante la implementación de la <xref:EnvDTE80.IInternalExtenderProvider> interfaz. La exploración, automatización de proyecto y examinar objetos de configuración de proyecto del proyecto base todas las implementan esta interfaz.  
  
-   La implementación de <xref:EnvDTE80.IInternalExtenderProvider> para el objeto de búsqueda de proyecto y el objeto de automatización de proyecto delegar a la <xref:EnvDTE80.IInternalExtenderProvider> implementación del agregador de subtipo de proyecto (es decir, que `QueryInterface` para <xref:EnvDTE80.IInternalExtenderProvider> en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto de proyecto).  
  
-   También implementa el objeto de búsqueda de configuración de proyecto base <xref:EnvDTE80.IInternalExtenderProvider> para conectarlo directamente en el extensor de automatización del objeto de configuración del subtipo de proyecto. Su implementación se delega en el <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada por el agregador de subtipo de proyecto.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementado por el objeto de búsqueda de configuración de proyecto, devuelve el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, también se implementa por el objeto de búsqueda de configuración de proyecto, devuelve el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objeto.  
  
-   Un subtipo de proyecto puede determinar el CATID adecuado para los distintos objetos extensibles del objeto base en tiempo de ejecución mediante la recuperación de los siguientes <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> valores:  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
 Para determinar el CATID para el ámbito del proyecto, el subtipo de proyecto recupera las propiedades anteriores para <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT> desde el `VSITEMID``typedef`. Un subtipo de proyecto que también desee controlar qué **páginas de propiedades** páginas del cuadro de diálogo se muestran para el proyecto, dependientes de la configuración y la configuración independiente. Algunos subtipos de proyecto que necesite quitar páginas integradas y agregue páginas específicas de subtipo de proyecto. Para habilitar esto, el proyecto de cliente administrado llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> método para las propiedades siguientes:  
  
-   `VSHPROPID_PropertyPagesCLSIDList`: una lista delimitada por punto y coma de CLSID de páginas de propiedades independientes de la configuración.  
  
-   `VSHPROPID_CfgPropertyPagesCLSIDList —`una lista delimitada por punto y coma de CLSID de páginas de propiedades dependientes de la configuración.  
  
 Dado que el proyecto subtipo agregados la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> de objeto, puede reemplazar la definición de estas propiedades para controlar qué **páginas de propiedades** se muestran cuadros de diálogo. El subtipo de proyecto puede recuperar estas propiedades desde el proyecto de base interno y, a continuación, agregar o quitar CLSID según sea necesario.  
  
 Nuevas páginas de propiedades agregadas por un subtipo de proyecto se va a pasar un objeto de exploración de configuración de proyecto de la implementación de proyecto base. Este objeto de búsqueda de configuración de proyecto admite extensores de automatización. Para obtener más información sobre AutomationExtenders, consulte [implementar y utilizar extensores de automatización](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Las páginas de propiedades implementadas por la llamada del subtipo de proyecto <xref:EnvDTE.Project.Extender%2A> para recuperar su propio objeto de búsqueda de configuración de subtipo de proyecto que extiende el objeto de exploración de la configuración del proyecto de base de.  
  
## <a name="see-also"></a>Vea también  
 <xref:EnvDTE.IFilterProperties>   
 [Cuadro de diálogo páginas de propiedades](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)