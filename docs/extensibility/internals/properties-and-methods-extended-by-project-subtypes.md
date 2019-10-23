---
title: Propiedades y métodos extendidos por subtipos de proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f5f67ac70b7ca6d5151a9115f20be88f6984d52
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725345"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Propiedades y métodos ampliados por subtipos de proyecto
Un subtipo de proyecto tiene una gran capacidad para influir en el comportamiento del proyecto porque se construye como un agregador de un proyecto base. En esta sección se resumen algunas de las características que se pueden mejorar o modificar mediante subtipos de proyecto.

## <a name="features-gained-by-aggregation"></a>Características obtenidas por la agregación
 En la tabla siguiente se resumen muchos de los métodos que la agregación permite a los subtipos de proyecto invalidar en proyectos base.

|Métodos invalidados por la agregación|Subtipo de proyecto|
|---------------------------------------|---------------------|
|Desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Habilita un subtipo de proyecto para<br /><br /> -Cambiar el título y el icono del nodo del proyecto.<br />-Invalidar completamente el objeto de `Browse` de proyecto.<br />: Controla si se puede cambiar el nombre del proyecto.<br />-Control: criterio de ordenación.<br />-Controle el contexto de usuario para la ayuda dinámica.|
|Desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Habilita un subtipo de proyecto para controlar qué servicios contextuales se proporcionan a los diseñadores y editores.|
|Desde <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Habilita un subtipo de proyecto para<br /><br /> -Participar en el enrutamiento de comandos para los comandos del proyecto.<br />-Agregar, quitar o deshabilitar los comandos de ambiente del proyecto y Explorador de soluciones comandos activos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Habilita el subtipo de proyecto para filtrar lo que el usuario ve en el cuadro de diálogo **Agregar nuevo elemento** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Habilita un subtipo de proyecto para<br /><br /> -Determinar el generador predeterminado dada una extensión de archivo.<br />-Asignar un nombre de generador legible a un objeto COM.|

## <a name="properties-used-by-project-subtypes"></a>Propiedades utilizadas por los subtipos de proyecto
 El entorno y el sistema del proyecto base pueden utilizar las propiedades de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> y <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> enumeraciones que se detallan en la tabla siguiente para habilitar un subtipo de proyecto con el fin de controlar las distintas características del sistema del proyecto.

|Propiedad VSHPROPID|Subtipo de proyecto|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Permite que un subtipo de proyecto controle el contenido del cuadro de diálogo **Agregar elemento** . El subtipo de proyecto puede proporcionar una nueva especificación de directorios de plantilla, agregar nuevos tipos de elementos, quitar elementos existentes y reorganizar un subconjunto de los elementos del cuadro de diálogo **Agregar elemento** del proyecto base.|
|`PropertyPagesCLSIDList`|Permite que un subtipo de proyecto agregue o quite páginas de propiedades independientes de la configuración.|
|`CfgPropertyPagesCLSIDList`|Permite que un subtipo de proyecto agregue o quite páginas de propiedades dependientes de la configuración.|
|`ExtObjectCATID`|Permite que un subtipo de proyecto proporcione un extensor de automatización para los objetos de proyecto o de elemento de proyecto conociendo el CATId del objeto extender. Por ejemplo, un subtipo de proyecto puede proporcionar un objeto de `Project.Extender("<subtype>")` personalizado.|
|`BrowseObjectCATID`|Permite que un subtipo de proyecto proporcione un extensor de automatización para el objeto `Browse` conociendo el CATId del extensor. Por ejemplo, un subtipo de proyecto puede Agregar propiedades adicionales a la colección de <xref:EnvDTE.Project.Properties%2A>.|
|`CfgBrowseObjectCATID`|Permite que un subtipo de proyecto proporcione un extensor de automatización para el objeto de exploración de configuración del proyecto. Por ejemplo, un subtipo de proyecto puede Agregar propiedades adicionales a la colección de <xref:EnvDTE.Configuration.Properties%2A>.|
|`CfgExtObjectCATID`|Permite que un subtipo de proyecto proporcione un extensor de automatización para el objeto de configuración.|
|`DefaultPlatformName`|Permite que un subtipo de proyecto determine el nombre de la plataforma para los objetos de configuración del proyecto.|

 El proyecto base proporciona una implementación predeterminada de las propiedades anteriores. El proyecto base los obtiene llamando a `QueryInterface` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> en el subtipo de proyecto más externo, lo que permite que el subtipo de proyecto invalide la implementación de las propiedades.

## <a name="see-also"></a>Vea también
- [Diseño de subtipos de proyecto](../../extensibility/internals/project-subtypes-design.md)