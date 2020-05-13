---
title: Propiedades y métodos extendidos por subtipos de proyecto ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9963f779055fcf1ed0efd8c47abbe1cce35631a6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706195"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Propiedades y métodos ampliados por subtipos de proyecto
Un subtipo de proyecto tiene mucho poder para influir en el comportamiento del proyecto porque se construye como un agregador de un proyecto base. En esta sección se resumen algunas de las características que se pueden mejorar o modificar mediante subtipos de proyecto.

## <a name="features-gained-by-aggregation"></a>Características obtenidas por agregación
 En la tabla siguiente se resumen muchos de los métodos que la agregación permite que los subtipos de proyecto se invaliden en proyectos base.

|Métodos anulados por la agregación|Subtipo de proyecto|
|---------------------------------------|---------------------|
|Desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Permite que un subtipo de proyecto<br /><br /> - Cambiar el título y el icono del nodo del proyecto.<br />- Anular `Browse` completamente el objeto de proyecto.<br />- Controlar si se puede cambiar el nombre del proyecto.<br />- Ordenar el control.<br />- Controlar el contexto del usuario para la ayuda dinámica.|
|Desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Permite que un subtipo de proyecto controle qué servicios contextuales se proporcionan a diseñadores y editores.|
|Desde <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Permite que un subtipo de proyecto<br /><br /> - Participar en el enrutamiento de comandos para los comandos del proyecto.<br />- Agregar, quitar o deshabilitar los comandos ambientales del proyecto y los comandos activos del Explorador de soluciones.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Permite que el subtipo de proyecto filtre lo que el usuario ve en el cuadro de diálogo **Agregar nuevo elemento.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Permite que un subtipo de proyecto<br /><br /> - Determinar el generador predeterminado dada una extensión de archivo.<br />- Asignar un nombre de generador legible humano a un objeto COM.|

## <a name="properties-used-by-project-subtypes"></a>Propiedades utilizadas por los subtipos de proyecto
 El entorno y el sistema de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> proyecto base pueden utilizar las propiedades y enumeraciones detalladas en la tabla siguiente para permitir que un subtipo de proyecto controle varias características del sistema de proyecto.

|Propiedad VSHPROPID|Subtipo de proyecto|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Permite que un subtipo de proyecto controle el contenido del cuadro de diálogo **Agregar elemento.** El subtipo de proyecto puede proporcionar una nueva especificación de directorios de plantilla, agregar nuevos tipos de elementos, quitar elementos existentes y reorganizar un subconjunto de los elementos en el cuadro de diálogo **Agregar elemento** del proyecto base.|
|`PropertyPagesCLSIDList`|Permite que un subtipo de proyecto agregue o quite páginas de propiedades independientes de la configuración.|
|`CfgPropertyPagesCLSIDList`|Permite que un subtipo de proyecto agregue o quite páginas de propiedades dependientes de la configuración.|
|`ExtObjectCATID`|Permite que un subtipo de proyecto proporcione un extensor de automatización para los objetos de proyecto o elemento de proyecto conociendo el CATID de extensor. Por ejemplo, un subtipo de `Project.Extender("<subtype>")` proyecto puede proporcionar un objeto personalizado.|
|`BrowseObjectCATID`|Permite que un subtipo de proyecto `Browse` proporcione un extensor de automatización para el objeto conociendo el CATID de extensor. Por ejemplo, un subtipo de proyecto <xref:EnvDTE.Project.Properties%2A> puede agregar propiedades adicionales a la colección.|
|`CfgBrowseObjectCATID`|Permite que un subtipo de proyecto proporcione un extensor de automatización para el objeto de exploración de configuración del proyecto. Por ejemplo, un subtipo de proyecto <xref:EnvDTE.Configuration.Properties%2A> puede agregar propiedades adicionales a la colección.|
|`CfgExtObjectCATID`|Permite que un subtipo de proyecto proporcione un extensor de automatización para el objeto de configuración.|
|`DefaultPlatformName`|Permite que un subtipo de proyecto determine el nombre de la plataforma para los objetos de configuración del proyecto.|

 El proyecto base proporciona una implementación predeterminada de las propiedades anteriores. El proyecto base obtiene `QueryInterface` estos <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> llamando al subtipo de proyecto más externo, lo que permite que el subtipo de proyecto invalide la implementación de las propiedades.

## <a name="see-also"></a>Vea también
- [Diseño de subtipos de proyecto](../../extensibility/internals/project-subtypes-design.md)
