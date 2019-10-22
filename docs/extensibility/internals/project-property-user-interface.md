---
title: Interfaz de usuario de propiedad de proyecto | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a83e5c9fb633322da536e62f1ba03484b965b162
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252363"
---
# <a name="project-property-user-interface"></a>Interfaz de usuario de propiedades de proyecto

Un subtipo de proyecto puede usar los elementos del cuadro de diálogo **páginas de propiedades** del proyecto tal como los proporciona el proyecto base, ocultar o hacer que los controles de solo lectura y las páginas completas se proporcionen, o agregar páginas específicas del subtipo de proyecto en el cuadro de diálogo **páginas de propiedades** . cuadro.

## <a name="extending-the-project-property-dialog-box"></a>Extender el cuadro de diálogo propiedad del proyecto

Un subtipo de proyecto implementa extensores de automatización y objetos de exploración de configuración del proyecto. Estos extensores implementan <xref:EnvDTE.IFilterProperties> la interfaz para que las propiedades concretas estén ocultas o sean de solo lectura. El cuadro de diálogo **páginas de propiedades** del proyecto base, implementado por el proyecto base, respeta el filtrado realizado por los extensores de automatización.

El proceso de extensión de un cuadro de diálogo de **propiedades de proyecto** se describe a continuación:

- El proyecto base recupera los objetos extender del subtipo de proyecto implementando la <xref:EnvDTE80.IInternalExtenderProvider> interfaz. Los objetos examinar, automatización del proyecto y examinar la configuración del proyecto del proyecto base implementan esta interfaz.

- La implementación de <xref:EnvDTE80.IInternalExtenderProvider> para el objeto examinar del proyecto y el delegado del objeto de automatización <xref:EnvDTE80.IInternalExtenderProvider> del proyecto para la implementación del agregador de subtipos de `QueryInterface` proyecto <xref:EnvDTE80.IInternalExtenderProvider> (es <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> decir, para en el objeto de proyecto).

- El objeto de exploración de configuración del proyecto base <xref:EnvDTE80.IInternalExtenderProvider> también implementa directamente en el extensor de automatización del objeto de configuración del subtipo de proyecto. Su implementación delega en la <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada por el agregador de subtipos de proyecto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementado por el objeto de exploración de configuración del <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> proyecto, devuelve el objeto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, también implementado por el objeto de exploración de configuración del <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> proyecto, devuelve el objeto.

- Un subtipo de proyecto puede determinar los CATID adecuados para los distintos objetos ampliables del proyecto base en tiempo de ejecución mediante la recuperación <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> de los valores siguientes:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Para determinar los CATID del ámbito del proyecto, el subtipo de proyecto recupera las propiedades anteriores para [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) de la `VSITEMID typedef`. Un subtipo de proyecto también puede querer controlar qué páginas de cuadro de diálogo de **las páginas de propiedades** se muestran para el proyecto, tanto dependiente de la configuración como independiente de la configuración. Es posible que algunos subtipos de proyecto deban quitar páginas integradas y agregar páginas específicas de subtipos de proyecto. Para habilitar esto, el proyecto de cliente administrado llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> método para las siguientes propiedades:

- `VSHPROPID_PropertyPagesCLSIDList`: una lista delimitada por signos de punto y coma de CLSID de páginas de propiedades independientes de la configuración.

- `VSHPROPID_CfgPropertyPagesCLSIDList —`una lista delimitada por signos de punto y coma de CLSID de páginas de propiedades dependientes de la configuración.

Dado que el subtipo de proyecto agrega <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> el objeto, puede invalidar la definición de estas propiedades para controlar qué cuadros de diálogo de **páginas de propiedades** se muestran. El subtipo de proyecto puede recuperar estas propiedades del proyecto base interno y, a continuación, agregar o quitar CLSID según sea necesario.

Las nuevas páginas de propiedades agregadas por un subtipo de proyecto se entregan a un objeto de exploración de configuración del proyecto desde la implementación del proyecto base. Este objeto de examen de configuración de proyecto es compatible con los extensores de automatización. Para obtener más información sobre AutomationExtenders, consulte [implementación y uso de extensores de automatización](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Las páginas de propiedades implementadas por la llamada <xref:EnvDTE.Project.Extender%2A> de subtipo de proyecto para recuperar su propio objeto de examen de configuración de subtipo de proyecto que extiende el objeto de exploración de configuración del proyecto base.

## <a name="see-also"></a>Vea también

- <xref:EnvDTE.IFilterProperties>
- [Cuadro de diálogo páginas de propiedades](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
