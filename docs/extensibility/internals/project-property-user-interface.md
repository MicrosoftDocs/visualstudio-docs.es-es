---
title: Propiedades del proyecto Interfaz de usuario | Microsoft Docs
description: Obtenga información sobre cómo los subtipos de proyecto pueden modificar el cuadro de diálogo Páginas de propiedades del proyecto tal como lo proporciona el proyecto base.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77e3554f2a3fd3b0dc1d608bb7d0a1198116a4e3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903594"
---
# <a name="project-property-user-interface"></a>Interfaz de usuario de propiedades de proyecto

Un subtipo de proyecto puede  usar los elementos del cuadro de diálogo Páginas de propiedades del proyecto a medida que los proporciona el proyecto  base, ocultar o crear controles de solo lectura y páginas enteras según lo proporcionado, o agregar páginas específicas del subtipo de proyecto al cuadro de diálogo Páginas de propiedades .

## <a name="extending-the-project-property-dialog-box"></a>Extensión del cuadro de diálogo Propiedad del proyecto

Un subtipo de proyecto implementa extensores de automatización y objetos de exploración de configuración de proyecto. Estos extensores implementan la <xref:EnvDTE.IFilterProperties> interfaz para que determinadas propiedades se ocultan o son de solo lectura. El **cuadro de diálogo** Páginas de propiedades del proyecto base, implementado por el proyecto base, respeta el filtrado realizado por los extensores de Automation.

A continuación se describe el **proceso** de extensión de un cuadro de diálogo Propiedad del proyecto:

- El proyecto base recupera los extensores del subtipo de proyecto implementando la <xref:EnvDTE80.IInternalExtenderProvider> interfaz . Los objetos browse, project automation y project configuration browse del proyecto base implementan esta interfaz.

- La implementación de para el objeto de exploración del proyecto y el delegado de objeto de automatización del proyecto en la implementación del agregador de subtipos de proyecto <xref:EnvDTE80.IInternalExtenderProvider> <xref:EnvDTE80.IInternalExtenderProvider> (es decir, para en el objeto de `QueryInterface` <xref:EnvDTE80.IInternalExtenderProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> proyecto).

- El objeto de exploración de configuración de proyecto base también implementa para conectar directamente en el <xref:EnvDTE80.IInternalExtenderProvider> extensor de Automation desde el objeto de configuración de subtipo del proyecto. Su implementación delega a la <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada por el agregador de subtipos de proyecto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementado por el objeto de exploración de configuración del proyecto, devuelve el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, también implementado por el objeto de exploración de configuración del proyecto, devuelve el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objeto .

- Un subtipo de proyecto puede determinar los CATID adecuados para los distintos objetos extensibles del proyecto base en tiempo de ejecución mediante la recuperación de los valores <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> siguientes:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Para determinar los CATID del ámbito del proyecto, el subtipo de proyecto recupera las propiedades anteriores para [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) de `VSITEMID typedef` . Un subtipo de proyecto también  puede querer controlar qué páginas de propiedades se muestran para el proyecto, tanto dependientes de la configuración como independientes de la configuración. Es posible que algunos subtipos de proyecto necesiten quitar páginas integradas y agregar páginas específicas del subtipo de proyecto. Para habilitar esto, el proyecto de cliente administrado llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> método para las propiedades siguientes:

- `VSHPROPID_PropertyPagesCLSIDList` : una lista delimitada por punto y coma de CLID de páginas de propiedades independientes de la configuración.

- `VSHPROPID_CfgPropertyPagesCLSIDList —` una lista delimitada por punto y coma de CLID de páginas de propiedades dependientes de la configuración.

Dado que el subtipo de proyecto agrega el objeto , puede invalidar la definición de estas propiedades para controlar qué cuadros de diálogo Páginas de propiedades <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> se muestran.  El subtipo de proyecto puede recuperar estas propiedades del proyecto base interno y, a continuación, agregar o quitar CLID según sea necesario.

Las nuevas páginas de propiedades agregadas por un subtipo de proyecto se entregan a un objeto de exploración de configuración de proyecto desde la implementación del proyecto base. Este objeto de exploración de configuración de proyecto admite extensores de Automation. Para obtener más información sobre AutomationE automatismos, vea [Implementing and Using Automation Extenders](/previous-versions/0y92k2w2(v=vs.140)). Las páginas de propiedades implementadas por la llamada de subtipo de proyecto para recuperar su propio objeto de exploración de configuración de subtipo de proyecto que extiende el objeto de exploración de configuración <xref:EnvDTE.Project.Extender%2A> del proyecto base.

## <a name="see-also"></a>Consulta también

- <xref:EnvDTE.IFilterProperties>
- [Páginas de propiedades (cuadro de diálogo)](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))