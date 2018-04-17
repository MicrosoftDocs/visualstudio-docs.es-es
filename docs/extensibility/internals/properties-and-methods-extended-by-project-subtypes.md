---
title: Propiedades y métodos extendidos subtipos de proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23510ffbb42e0c0c37c07e0ee80ae15f99e5df00
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Propiedades y métodos extendidos subtipos de proyecto
Un subtipo de proyecto tiene una gran cantidad de energía para influir en el comportamiento del proyecto porque se construye como un agregador de un proyecto de base. En esta sección se resume algunas de las características que pueden ser mejoradas o modificar mediante subtipos de proyecto.  
  
## <a name="features-gained-by-aggregation"></a>Obtenido mediante la agregación de características  
 En la tabla siguiente se resume muchos de los métodos de agregación permite subtipos de proyecto invalidar en los proyectos de base.  
  
|Se reemplaza con la agregación de métodos|Subtipo de proyecto|  
|---------------------------------------|---------------------|  
|Desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Habilita a un subtipo de proyecto a<br /><br /> -Cambiar el título y el icono de nodo del proyecto.<br />-Completamente invalidar proyecto `Browse` objeto.<br />-Controlar si se puede cambiar el nombre de proyecto.<br />-Criterio de ordenación control.<br />: Contexto de usuario de control para obtener Ayuda dinámica.|  
|Desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Permite un subtipo de proyecto controlar qué servicios contextuales se proporcionan a los editores y diseñadores.|  
|Desde <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Habilita a un subtipo de proyecto a<br /><br /> -Participar en el enrutamiento de comandos para los comandos de proyecto.<br />-Agregar, quitar o deshabilitar comandos ambiente de proyecto y los comandos activos el Explorador de soluciones.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Habilita el subtipo de proyecto filtrar lo que ve el usuario en el **Agregar nuevo elemento** cuadro de diálogo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Habilita a un subtipo de proyecto a<br /><br /> -Determine el generador predeterminado tiene una extensión de archivo.<br />-Asignar un nombre de generador legible humano a un objeto COM.|  
  
## <a name="properties-used-by-project-subtypes"></a>Propiedades utilizadas por los subtipos de proyecto  
 Puede utilizar el sistema de proyecto de base y el entorno de las propiedades de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> y <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> enumeraciones detalladas en la tabla siguiente para habilitar un subtipo de proyecto controlar diversas características del sistema del proyecto.  
  
|Propiedad VSHPROPID|Subtipo de proyecto|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Permite un subtipo de proyecto controlar el contenido de la **Agregar elemento** cuadro de diálogo. Puede proporcionar una nueva especificación de directorios de la plantilla, agregar nuevos tipos de elementos, quitar los elementos existentes y reorganizar un subconjunto de los elementos en el proyecto de base del subtipo de proyecto **Agregar elemento** cuadro de diálogo.|  
|`PropertyPagesCLSIDList`|Permite un subtipo de proyecto Agregar o quitar páginas de propiedades independientes de la configuración.|  
|`CfgPropertyPagesCLSIDList`|Permite un subtipo de proyecto Agregar o quitar páginas de propiedades dependientes de la configuración.|  
|`ExtObjectCATID`|Permite un subtipo de proyecto proporcionar un extensor de automatización para el proyecto o el proyecto de objetos de elementos si se conoce el identificador de categoría del extensor. Por ejemplo, un subtipo de proyecto puede proporcionar un personalizado `Project.Extender("<subtype>")` objeto.|  
|`BrowseObjectCATID`|Permite un subtipo de proyecto proporcionar un extensor de automatización para la `Browse` objeto conociendo el CATID del objeto Extender. Por ejemplo, un subtipo de proyecto puede agregar propiedades adicionales a la <xref:EnvDTE.Project.Properties%2A> colección.|  
|`CfgBrowseObjectCATID`|Permite un subtipo de proyecto proporcionar un extensor de automatización para el objeto de búsqueda de la configuración de proyecto. Por ejemplo, un subtipo de proyecto puede agregar propiedades adicionales a la <xref:EnvDTE.Configuration.Properties%2A> colección.|  
|`CfgExtObjectCATID`|Permite un subtipo de proyecto proporcionar un extensor de automatización para el objeto de configuración.|  
|`DefaultPlatformName`|Permite un subtipo de proyecto determinar el nombre de la plataforma para los objetos de configuración del proyecto.|  
  
 El proyecto de base proporciona una implementación predeterminada de las propiedades anteriores. Obtiene el proyecto de base estos métodos, debe llamar a `QueryInterface` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> en el subtipo de proyecto más externo, lo que permite el subtipo de proyecto invalidar la implementación de las propiedades.  
  
## <a name="see-also"></a>Vea también  
 [Diseño de subtipos de proyecto](../../extensibility/internals/project-subtypes-design.md)