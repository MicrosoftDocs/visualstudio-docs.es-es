---
title: Interfaz de usuario de la propiedad del proyecto ( Project Property User Interface) Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4634eb5edaab16752bc5df82d70371a580845d28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706397"
---
# <a name="project-property-user-interface"></a>Interfaz de usuario de propiedades de proyecto

Un subtipo de proyecto puede usar los elementos del cuadro de diálogo **Páginas** de propiedades del proyecto tal como los proporciona el proyecto base, ocultar o crear controles de solo lectura y páginas enteras según lo proporcionado, o agregar páginas específicas del subtipo de proyecto al cuadro de diálogo **Páginas** de propiedades.

## <a name="extending-the-project-property-dialog-box"></a>Ampliación del cuadro de diálogo Propiedad del proyecto

Un subtipo de proyecto implementa extensores de automatización y objetos de exploración de configuración de proyecto. Estos extensores <xref:EnvDTE.IFilterProperties> implementan la interfaz para que determinadas propiedades estén ocultas o de solo lectura. El cuadro de diálogo **Páginas** de propiedades del proyecto base, implementado por el proyecto base, respeta el filtrado realizado por los extensores de automatización.

El proceso de ampliación de un cuadro de diálogo Propiedad de **proyecto** se describe a continuación:

- El proyecto base recupera los extensores del <xref:EnvDTE80.IInternalExtenderProvider> subtipo de proyecto mediante la implementación de la interfaz. Los objetos examinar, la automatización del proyecto y la configuración del proyecto implementan esta interfaz.

- La implementación del <xref:EnvDTE80.IInternalExtenderProvider> objeto de exploración del <xref:EnvDTE80.IInternalExtenderProvider> proyecto y el delegado de objeto de automatización del proyecto para la implementación del agregador de subtipo de proyecto (es decir, `QueryInterface` para <xref:EnvDTE80.IInternalExtenderProvider> el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto de proyecto).

- El objeto de exploración <xref:EnvDTE80.IInternalExtenderProvider> de configuración del proyecto base también implementa para conectar directamente en el extensor de automatización desde el objeto de configuración de subtipo de proyecto. Su implementación se <xref:EnvDTE80.IInternalExtenderProvider> delega en la interfaz implementada por el agregador de subtipos de proyecto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementado por el objeto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> exploración de configuración del proyecto, devuelve el objeto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, también implementado por el objeto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> exploración de configuración del proyecto, devuelve el objeto.

- Un subtipo de proyecto puede determinar los CATID adecuados para los distintos objetos extensibles del proyecto base en tiempo de ejecución recuperando los valores siguientes: <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Para determinar los CATID para el ámbito del proyecto, el subtipo de proyecto recupera las propiedades anteriores para [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) de `VSITEMID typedef`la . Un subtipo de proyecto también puede controlar qué páginas de cuadro de diálogo **Páginas** de propiedades se muestran para el proyecto, tanto dependientede de la configuración como independiente de la configuración. Es posible que algunos subtipos de proyecto necesiten quitar páginas integradas y agregar páginas específicas de subtipo de proyecto. Para habilitar esto, el proyecto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> cliente administrado llama al método para las siguientes propiedades:

- `VSHPROPID_PropertyPagesCLSIDList`— una lista delimitada por punto y coma de CLSID de páginas de propiedades independientes de la configuración.

- `VSHPROPID_CfgPropertyPagesCLSIDList —`una lista delimitada por punto y coma de CLSID de páginas de propiedades dependientes de la configuración.

Dado que el subtipo <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> de proyecto agrega el objeto, puede invalidar la definición de estas propiedades para controlar qué cuadros de diálogo **Páginas** de propiedades se muestran. El subtipo de proyecto puede recuperar estas propiedades del proyecto base interno y, a continuación, agregar o quitar CLSDI según sea necesario.

Las nuevas páginas de propiedades agregadas por un subtipo de proyecto se entregan un objeto de exploración de configuración de proyecto de la implementación del proyecto base. Este objeto de exploración de configuración de proyecto admite extensores de automatización. Para obtener más información sobre AutomationExtenders, consulte Implementación y uso de [extensores](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356)de automatización . Las páginas de propiedades implementadas <xref:EnvDTE.Project.Extender%2A> por la llamada al subtipo de proyecto para recuperar su propio objeto de exploración de configuración de subtipo de proyecto que extiende el objeto de exploración de configuración del proyecto base.

## <a name="see-also"></a>Vea también

- <xref:EnvDTE.IFilterProperties>
- [Cuadro de diálogo Páginas de propiedades](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
