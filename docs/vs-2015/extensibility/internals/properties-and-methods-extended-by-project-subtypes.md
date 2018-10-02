---
title: Propiedades y métodos extienden por subtipos de proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 143c15cd757912aa79e7e9d92d7c138def16db7c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577023"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Propiedades y métodos ampliados por subtipos de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [propiedades y métodos extendidos por subtipos de proyecto](https://docs.microsoft.com/visualstudio/extensibility/internals/properties-and-methods-extended-by-project-subtypes).  
  
Un subtipo de proyecto tiene una gran cantidad de energía para influir en el comportamiento del proyecto porque se construye como un agregador de un proyecto de base. En esta sección se resume algunas de las características que pueden ser mejoradas o modificar mediante subtipos de proyecto.  
  
## <a name="features-gained-by-aggregation"></a>Características obtenidas a través de agregación  
 En la tabla siguiente se resume a muchos de los métodos de agregación permite subtipos de proyecto reemplazar en proyectos de bases.  
  
|Métodos que se reemplaza por la agregación|Subtipo de proyecto|  
|---------------------------------------|---------------------|  
|Desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Permite a un subtipo de proyecto<br /><br /> -Cambiar el título y el icono del nodo del proyecto.<br />-Invalidar completamente proyecto `Browse` objeto.<br />-Controlar si se puede cambiar el nombre de proyecto.<br />-Criterio de ordenación control.<br />-Contexto de usuario control para obtener Ayuda dinámica.|  
|Desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Permite un subtipo de proyecto controlar qué servicios contextuales se proporcionan a los diseñadores y editores.|  
|Desde <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Permite a un subtipo de proyecto<br /><br /> -Participar en el enrutamiento de comandos para comandos del proyecto.<br />-Agregar, quitar o deshabilitar los comandos de ambiente del proyecto y los comandos activos del explorador de soluciones.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Permite que el subtipo de proyecto filtrar lo que ve el usuario en el **Agregar nuevo elemento** cuadro de diálogo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Permite a un subtipo de proyecto<br /><br /> -Determine el generador predeterminado tiene una extensión de archivo.<br />-Asignar un nombre de generador legible humano a un objeto COM.|  
  
## <a name="properties-used-by-project-subtypes"></a>Propiedades utilizadas por subtipos de proyecto  
 El sistema de proyectos base y el entorno puede usar las propiedades de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> y <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> enumeraciones que se detallan en la tabla siguiente para habilitar un subtipo de proyecto controlar diversas características del sistema del proyecto.  
  
|Propiedad VSHPROPID|Subtipo de proyecto|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Permite un subtipo de proyecto controlar el contenido de la **Agregar elemento** cuadro de diálogo. Puede proporcionar una nueva especificación de directorios de plantillas, agregar nuevos tipos de elementos, quitar los elementos existentes y reorganizar un subconjunto de los elementos en el proyecto de base del subtipo de proyecto **Agregar elemento** cuadro de diálogo.|  
|`PropertyPagesCLSIDList`|Permite un subtipo de proyecto Agregar o quitar páginas de propiedades independientes de la configuración.|  
|`CfgPropertyPagesCLSIDList`|Permite un subtipo de proyecto Agregar o quitar páginas de propiedades dependientes de la configuración.|  
|`ExtObjectCATID`|Permite un subtipo de proyecto proporcionar un extensor de automatización para el proyecto o el proyecto de objetos de elemento conociendo el CATID del objeto Extender. Por ejemplo, un subtipo de proyecto puede proporcionar una personalizada `Project.Extender("<subtype>")` objeto.|  
|`BrowseObjectCATID`|Permite un subtipo de proyecto proporcionar un extensor de automatización para la `Browse` objeto conociendo el CATID del objeto Extender. Por ejemplo, un subtipo de proyecto puede agregar propiedades adicionales a la <xref:EnvDTE.Project.Properties%2A> colección.|  
|`CfgBrowseObjectCATID`|Permite un subtipo de proyecto proporcionar un extensor de automatización para el objeto de exploración de la configuración de proyecto. Por ejemplo, un subtipo de proyecto puede agregar propiedades adicionales a la <xref:EnvDTE.Configuration.Properties%2A> colección.|  
|`CfgExtObjectCATID`|Permite un subtipo de proyecto proporcionar un extensor de automatización para el objeto de configuración.|  
|`DefaultPlatformName`|Permite un subtipo de proyecto determinar el nombre de la plataforma para los objetos de configuración del proyecto.|  
  
 El proyecto base proporciona una implementación predeterminada de las propiedades anteriores. Obtiene el proyecto base llamando a `QueryInterface` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> en el subtipo de proyecto más externo, lo que permite invalidar la implementación de las propiedades del subtipo de proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Diseño de subtipos de proyecto](../../extensibility/internals/project-subtypes-design.md)

