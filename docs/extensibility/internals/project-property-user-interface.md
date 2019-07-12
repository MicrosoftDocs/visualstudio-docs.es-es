---
title: Interfaz de usuario de propiedades del proyecto | Microsoft Docs
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
ms.openlocfilehash: 9f701c1a2e31a52c05f0a7514c9d403522579e45
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825840"
---
# <a name="project-property-user-interface"></a>Interfaz de usuario de propiedades de proyecto

Un subtipo de proyecto puede usar los elementos en el proyecto **páginas de propiedades** cuadro de diálogo como se proporcionan por el proyecto de base, ocultar o hacer controles de solo lectura y páginas completas tal como lo suministró o agregar páginas específicas del subtipo de proyecto a la **Páginas de propiedades** cuadro de diálogo.

## <a name="extending-the-project-property-dialog-box"></a>Ampliar el cuadro de diálogo de propiedades de proyecto

Un subtipo de proyecto implementa los extensores de automatización y examinar objetos de configuración de proyecto. Implementan estos extensores la <xref:EnvDTE.IFilterProperties> interfaz para realizar determinadas propiedades oculto o de solo lectura. El **páginas de propiedades** cuadro de diálogo del proyecto base, implementado el proyecto de base, respeta el filtrado realizado por los extensores de automatización.

El proceso de extender un **propiedad del proyecto** cuadro de diálogo se describe a continuación:

- El proyecto base recupera los extensores del subtipo de proyecto mediante la implementación de la <xref:EnvDTE80.IInternalExtenderProvider> interfaz. La exploración, automatización de proyectos y examinar objetos de configuración de proyecto del proyecto base todas implementan esta interfaz.

- La implementación de <xref:EnvDTE80.IInternalExtenderProvider> para delegación el objeto de examen de proyecto y el objeto de automatización de proyecto en el <xref:EnvDTE80.IInternalExtenderProvider> implementación del agregador de subtipo de proyecto (es decir, `QueryInterface` para <xref:EnvDTE80.IInternalExtenderProvider> en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto de proyecto).

- También implementa el objeto de exploración de la configuración de proyecto base <xref:EnvDTE80.IInternalExtenderProvider> para conectar directamente en el extensor de automatización desde el objeto de configuración del subtipo de proyecto. Su implementación se delega en el <xref:EnvDTE80.IInternalExtenderProvider> interfaz implementada por el agregador de subtipo de proyecto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementado por el objeto de exploración de configuración de proyecto, devuelve el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, también se implementa por el objeto de exploración de configuración de proyecto, devuelve el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objeto.

- Un subtipo de proyecto puede determinar el CATID correspondiente para los distintos objetos extensibles del proyecto base en tiempo de ejecución mediante la recuperación de los siguientes <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> valores:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Para determinar el CATID para el ámbito del proyecto, el subtipo de proyecto recupera las propiedades anteriores para [VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) desde el `VSITEMID typedef`. Un subtipo de proyecto también puede controlar qué **páginas de propiedades** se muestran las páginas del cuadro de diálogo para el proyecto, dependientes de la configuración y configuración independiente. Algunos subtipos de proyecto que deba quitar páginas integradas y agregar páginas específicas de subtipo de proyecto. Para habilitar esto, el proyecto de cliente administrado llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> método para las propiedades siguientes:

- `VSHPROPID_PropertyPagesCLSIDList` : una lista delimitada por punto y coma de CLSID de páginas de propiedades independientes de la configuración.

- `VSHPROPID_CfgPropertyPagesCLSIDList —` una lista delimitada por punto y coma de CLSID de páginas de propiedades dependientes de la configuración.

Dado que el proyecto de subtipo agregados el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto, puede reemplazar la definición de estas propiedades para controlar qué **páginas de propiedades** se muestran cuadros de diálogo. El subtipo de proyecto puede recuperar estas propiedades del proyecto base interno y, a continuación, agregar o quitar CLSID según sea necesario.

Nuevas páginas de propiedades que se agrega un subtipo de proyecto se va a pasar un objeto de exploración de configuración de proyecto de la implementación del proyecto de base. Este objeto de exploración de configuración de proyecto es compatible con los extensores de automatización. Para obtener más información sobre AutomationExtenders, consulte [implementación y utilizar extensores de automatización](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Las páginas de propiedades que se implementa mediante la llamada de subtipo de proyecto <xref:EnvDTE.Project.Extender%2A> para recuperar su propio objeto de exploración de configuración subtipo del proyecto que extiende el objeto de exploración de la configuración del proyecto base.

## <a name="see-also"></a>Vea también

- <xref:EnvDTE.IFilterProperties>
- [Cuadro de diálogo páginas de propiedades](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
