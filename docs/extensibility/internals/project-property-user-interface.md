---
title: Interfaz de usuario de propiedad de proyecto | Microsoft Docs
description: Obtenga información sobre cómo los subtipos de proyecto pueden modificar el cuadro de diálogo páginas de propiedades del proyecto según lo proporcionado por el proyecto base.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: da60258f41665bbbb5510eb73b4fbca0a88809ac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970184"
---
# <a name="project-property-user-interface"></a>Interfaz de usuario de propiedades de proyecto

Un subtipo de proyecto puede usar los elementos del cuadro de diálogo **páginas de propiedades** del proyecto, tal como los proporciona el proyecto base, ocultar o hacer los controles de solo lectura y las páginas completas tal como se proporcionan, o agregar páginas específicas del subtipo de proyecto en el cuadro de diálogo **páginas de propiedades** .

## <a name="extending-the-project-property-dialog-box"></a>Extender el cuadro de diálogo propiedad del proyecto

Un subtipo de proyecto implementa extensores de automatización y objetos de exploración de configuración del proyecto. Estos extensores implementan la <xref:EnvDTE.IFilterProperties> interfaz para que las propiedades concretas estén ocultas o sean de solo lectura. El cuadro de diálogo **páginas de propiedades** del proyecto base, implementado por el proyecto base, respeta el filtrado realizado por los extensores de automatización.

El proceso de extensión de un cuadro de diálogo de **propiedades de proyecto** se describe a continuación:

- El proyecto base recupera los objetos extender del subtipo de proyecto implementando la <xref:EnvDTE80.IInternalExtenderProvider> interfaz. Los objetos examinar, automatización del proyecto y examinar la configuración del proyecto del proyecto base implementan esta interfaz.

- La implementación de <xref:EnvDTE80.IInternalExtenderProvider> para el objeto examinar del proyecto y el delegado del objeto de automatización del proyecto para la <xref:EnvDTE80.IInternalExtenderProvider> implementación del agregador de subtipos de proyecto (es decir, `QueryInterface` para <xref:EnvDTE80.IInternalExtenderProvider> en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto de proyecto).

- El objeto de exploración de configuración del proyecto base también implementa <xref:EnvDTE80.IInternalExtenderProvider> directamente en el extensor de automatización del objeto de configuración del subtipo de proyecto. Su implementación delega en la <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada por el agregador de subtipos de proyecto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementado por el objeto de exploración de configuración del proyecto, devuelve el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, también implementado por el objeto de exploración de configuración del proyecto, devuelve el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objeto.

- Un subtipo de proyecto puede determinar los CATID adecuados para los distintos objetos ampliables del proyecto base en tiempo de ejecución mediante la recuperación de los <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> valores siguientes:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Para determinar los CATID del ámbito del proyecto, el subtipo de proyecto recupera las propiedades anteriores para [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) de la `VSITEMID typedef` . Un subtipo de proyecto también puede querer controlar qué páginas de cuadro de diálogo de **las páginas de propiedades** se muestran para el proyecto, tanto dependiente de la configuración como independiente de la configuración. Es posible que algunos subtipos de proyecto deban quitar páginas integradas y agregar páginas específicas de subtipos de proyecto. Para habilitar esto, el proyecto de cliente administrado llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> método para las siguientes propiedades:

- `VSHPROPID_PropertyPagesCLSIDList` : una lista delimitada por signos de punto y coma de CLSID de páginas de propiedades independientes de la configuración.

- `VSHPROPID_CfgPropertyPagesCLSIDList —` una lista delimitada por signos de punto y coma de CLSID de páginas de propiedades dependientes de la configuración.

Dado que el subtipo de proyecto agrega el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto, puede invalidar la definición de estas propiedades para controlar qué cuadros de diálogo de **páginas de propiedades** se muestran. El subtipo de proyecto puede recuperar estas propiedades del proyecto base interno y, a continuación, agregar o quitar CLSID según sea necesario.

Las nuevas páginas de propiedades agregadas por un subtipo de proyecto se entregan a un objeto de exploración de configuración del proyecto desde la implementación del proyecto base. Este objeto de examen de configuración de proyecto es compatible con los extensores de automatización. Para obtener más información sobre AutomationExtenders, consulte [implementación y uso de extensores de automatización](/previous-versions/0y92k2w2(v=vs.140)). Las páginas de propiedades implementadas por la llamada de subtipo de proyecto <xref:EnvDTE.Project.Extender%2A> para recuperar su propio objeto de examen de configuración de subtipo de proyecto que extiende el objeto de exploración de configuración del proyecto base.

## <a name="see-also"></a>Vea también

- <xref:EnvDTE.IFilterProperties>
- [Cuadro de diálogo páginas de propiedades](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))