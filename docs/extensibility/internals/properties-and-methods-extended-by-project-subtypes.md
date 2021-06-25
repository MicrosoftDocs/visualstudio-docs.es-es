---
title: Propiedades y métodos extendidos por subtipos de proyecto | Microsoft Docs
description: Obtenga información sobre las características que los subtipos de proyecto pueden mejorar o modificar, lo que le permite personalizar el comportamiento de los sistemas de proyecto de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ddcf020cf0b3e3e4f0f4a7c61ff1f15ce9ded5e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903546"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Propiedades y métodos ampliados por subtipos de proyecto
Un subtipo de proyecto tiene mucha capacidad para influir en el comportamiento del proyecto porque se construye como agregador de un proyecto base. En esta sección se resumen algunas de las características que los subtipos de proyecto pueden mejorar o modificar.

## <a name="features-gained-by-aggregation"></a>Características adquiridas por agregación
 En la tabla siguiente se resumen muchos de los métodos que la agregación permite invalidar los subtipos de proyecto en los proyectos base.

|Métodos reemplazados por agregación|Subtipo de proyecto|
|---------------------------------------|---------------------|
|Desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Habilita un subtipo de proyecto para<br /><br /> - Cambiar el título y el icono del nodo del proyecto.<br />- Invalidar completamente el objeto de `Browse` proyecto.<br />: controla si se puede cambiar el nombre del proyecto.<br />: controle el criterio de ordenación.<br />: controle el contexto del usuario para obtener ayuda dinámica.|
|Desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Permite que un subtipo de proyecto controle qué servicios contextuales se proporcionan a los diseñadores y editores.|
|Desde <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Habilita un subtipo de proyecto para<br /><br /> - Participar en el enrutamiento de comandos para los comandos del proyecto.<br />- Agregue, quite o deshabilite tanto los comandos ambiente del proyecto como Explorador de soluciones comandos activos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Permite que el subtipo de proyecto filtre lo que el usuario ve en el **cuadro de diálogo Agregar** nuevo elemento.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Habilita un subtipo de proyecto para<br /><br /> - Determine el generador predeterminado dada una extensión de archivo.<br />: asigne un nombre de generador legible a un objeto COM.|

## <a name="properties-used-by-project-subtypes"></a>Propiedades usadas por subtipos de proyecto
 El entorno y el sistema de proyectos base pueden usar las propiedades de y enumeraciones detalladas en la tabla siguiente para permitir que un subtipo de proyecto controle varias características <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> del sistema de proyectos.

|Propiedad VSHPROPID|Subtipo de proyecto|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Permite que un subtipo de proyecto controle el contenido del **cuadro de diálogo Agregar** elemento . El subtipo de proyecto puede proporcionar una nueva especificación de directorios de plantilla, agregar nuevos tipos de elementos, quitar elementos existentes y reorganizar un subconjunto de los elementos del cuadro de diálogo Agregar **elemento** del proyecto base.|
|`PropertyPagesCLSIDList`|Permite que un subtipo de proyecto agregue o quite páginas de propiedades independientes de la configuración.|
|`CfgPropertyPagesCLSIDList`|Permite que un subtipo de proyecto agregue o quite páginas de propiedades dependientes de la configuración.|
|`ExtObjectCATID`|Permite que un subtipo de proyecto proporcione un extensor de Automation para los objetos de proyecto o elemento de proyecto conociendo el CATID extensor. Por ejemplo, un subtipo de proyecto puede proporcionar un objeto `Project.Extender("<subtype>")` personalizado.|
|`BrowseObjectCATID`|Permite que un subtipo de proyecto proporcione un extensor de Automatización para el `Browse` objeto conociendo el CATID extensor. Por ejemplo, un subtipo de proyecto puede agregar propiedades adicionales a la <xref:EnvDTE.Project.Properties%2A> colección.|
|`CfgBrowseObjectCATID`|Permite que un subtipo de proyecto proporcione un extensor de Automation para el objeto de exploración de configuración del proyecto. Por ejemplo, un subtipo de proyecto puede agregar propiedades adicionales a la <xref:EnvDTE.Configuration.Properties%2A> colección.|
|`CfgExtObjectCATID`|Permite que un subtipo de proyecto proporcione un extensor de Automation para el objeto de configuración.|
|`DefaultPlatformName`|Permite que un subtipo de proyecto determine el nombre de la plataforma para los objetos de configuración del proyecto.|

 El proyecto base proporciona una implementación predeterminada de las propiedades anteriores. El proyecto base obtiene estos mediante una llamada a para en el subtipo de proyecto más externo, lo que permite que el subtipo de proyecto invalide la `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> implementación de las propiedades.

## <a name="see-also"></a>Consulta también
- [Diseño de subtipos de proyecto](../../extensibility/internals/project-subtypes-design.md)
