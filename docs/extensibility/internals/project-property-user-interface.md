---
title: Interfaz de usuario de propiedades del proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: b344731061053abb208225a0480408ebbe682050
ms.lasthandoff: 02/22/2017

---
# <a name="project-property-user-interface"></a>Interfaz de usuario de propiedades de proyecto
Un subtipo de proyecto puede usar los elementos en el proyecto **páginas de propiedades** cuadro de diálogo tal como se proporcionan por el proyecto base, ocultar o realizar controles de solo lectura y páginas enteras como se proporciona o agregar páginas específicos del subtipo de proyecto para la **páginas de propiedades** cuadro de diálogo.  
  
## <a name="extending-the-project-property-dialog-box"></a>Ampliar el cuadro de diálogo de propiedades de proyecto  
 Un subtipo de proyecto implementa extensores de automatización y examinar objetos de configuración de proyecto. Implementan los extensores la <xref:EnvDTE.IFilterProperties>interfaz para realizar determinadas propiedades oculto o de sólo lectura.</xref:EnvDTE.IFilterProperties> El **páginas de propiedades** cuadro de diálogo del proyecto de base, implementado por el proyecto de base respeta el filtrado realizadas por los extensores de automatización.  
  
 El proceso de ampliación de un **propiedad del proyecto** cuadro de diálogo se describe a continuación:  
  
-   El proyecto base recupera los extensores de subtipo de proyecto mediante la implementación de la <xref:EnvDTE80.IInternalExtenderProvider>interfaz.</xref:EnvDTE80.IInternalExtenderProvider> La exploración, automatización de proyectos y examinar objetos de configuración de proyecto del proyecto base todos los implementan esta interfaz.  
  
-   La implementación de <xref:EnvDTE80.IInternalExtenderProvider>para el objeto de búsqueda de proyecto y el objeto de automatización de proyecto delegación en el <xref:EnvDTE80.IInternalExtenderProvider>implementación del agregador de subtipo de proyecto (es decir, que `QueryInterface` para <xref:EnvDTE80.IInternalExtenderProvider>en la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>objeto project).</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider>  
  
-   También implementa el objeto de búsqueda de configuración de proyecto base <xref:EnvDTE80.IInternalExtenderProvider>Conectar directamente al extensor de automatización del objeto de configuración de proyecto subtipo.</xref:EnvDTE80.IInternalExtenderProvider> Su implementación delega en el <xref:EnvDTE80.IInternalExtenderProvider>interfaz implementada por el agregador del subtipo de proyecto.</xref:EnvDTE80.IInternalExtenderProvider>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementado por el objeto de búsqueda de configuración de proyecto, devuelve el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>objeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, también se implementa por el objeto de búsqueda de configuración de proyecto, devuelve el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>objeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>  
  
-   Un subtipo de proyecto puede determinar el CATID correspondiente de los objetos extensibles del proyecto base en tiempo de ejecución mediante la recuperación de los siguientes <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>valores:</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
 Para determinar el CATID para el ámbito del proyecto, el subtipo de proyecto recupera las propiedades anteriores para <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>desde la `VSITEMID``typedef`.</xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT> Un subtipo de proyecto también puede controlar qué **páginas de propiedades** páginas del cuadro de diálogo se muestran para el proyecto, dependientes de la configuración y la configuración independiente. Algunos subtipos de proyecto que necesite quitar páginas integradas y agregar páginas específicas del subtipo de proyecto. Para habilitar esto, el proyecto de cliente administrado llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>método para las propiedades siguientes:</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>  
  
-   `VSHPROPID_PropertyPagesCLSIDList`: una lista delimitada por punto y coma de CLSID de páginas de propiedades independientes de la configuración.  
  
-   `VSHPROPID_CfgPropertyPagesCLSIDList —`una lista delimitada por punto y coma de CLSID de páginas de propiedades dependientes de la configuración.  
  
 Dado que el proyecto de subtipo agregados el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>de objeto, puede reemplazar la definición de estas propiedades para controlar qué **páginas de propiedades** se muestran cuadros de diálogo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> El subtipo de proyecto puede recuperar estas propiedades del proyecto de base interna y, a continuación, agregar o quitar CLSID según sea necesario.  
  
 Agregada un subtipo de proyecto nuevas páginas de propiedades se entregan a un objeto de examen de configuración de proyecto de la implementación del proyecto base. Este objeto de exploración de configuración de proyecto admite extensores de automatización. Para obtener más información sobre AutomationExtenders, consulte [implementar y utilizar extensores de automatización](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Las páginas de propiedades implementadas por la llamada del subtipo de proyecto <xref:EnvDTE.Project.Extender%2A>para recuperar su propio objeto de examinar de configuración de subtipo de proyecto que extiende el objeto de búsqueda de la configuración del proyecto de base.</xref:EnvDTE.Project.Extender%2A>  
  
## <a name="see-also"></a>Vea también  
 <xref:EnvDTE.IFilterProperties></xref:EnvDTE.IFilterProperties>   
 [Cuadro de diálogo páginas de propiedades](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
