---
title: 'Cómo: usar GetGlobalService | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: douge
ms.openlocfilehash: bd0a82281d2271f9badfbda9a7b32d20edf0c12c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576586"
---
# <a name="how-to-use-getglobalservice"></a>Cómo: Usar GetGlobalService
A veces es posible que necesita obtener un servicio de una ventana de herramientas o control contenedor que no se ha ubicado, o bien que se ha ubicado con un proveedor de servicios que no conoce el servicio que desee. Por ejemplo, puede escribir en el registro de actividad desde dentro de un control. Para obtener más información sobre estos y otros escenarios, consulte [Cómo: solucionar problemas de servicios](../extensibility/how-to-troubleshoot-services.md).  
  
 Puede obtener la mayoría [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] servicios mediante una llamada a estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> se basa en un proveedor de servicios en caché que se inicializa la primera vez que se deriva de cualquier VSPackage <xref:Microsoft.VisualStudio.Shell.Package> está situado. Debe garantizar que esta condición se cumple o bien estar preparada para un servicio nulo.  
  
 Afortunadamente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funciona correctamente la mayoría del tiempo.  
  
-   Si un paquete VSPackage proporciona un servicio conocido solo a otro VSPackage, se basa en un VSPackage que solicita el servicio antes de VSPackage que proporciona que el servicio está cargado.  
  
-   Si una ventana de herramientas se crea un VSPackage, el VSPackage está situado antes de crea la ventana de herramientas.  
  
-   Si un contenedor de control se hospeda en una ventana de herramienta creada por un VSPackage, el VSPackage está situado antes de crea el contenedor del control.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Para obtener un servicio desde dentro de un contenedor de control o ventana de herramienta  
  
-   Inserte este código en el constructor, la ventana de herramientas o el contenedor de controles:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Este código obtiene un servicio SVsActivityLog y lo convierte a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz, que puede usarse para escribir en el registro de actividad. Para obtener un ejemplo, vea [Cómo: usar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: solucionar problemas de servicios](../extensibility/how-to-troubleshoot-services.md)   
 [Uso y provisión de servicios](../extensibility/using-and-providing-services.md)   
 [Conceptos básicos del servicio](../extensibility/internals/service-essentials.md)