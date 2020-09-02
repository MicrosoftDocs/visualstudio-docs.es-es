---
title: 'Cómo: usar GetGlobalService | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 1c1fb48e4bb354ef403b39b0f1320ead92f43967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62948187"
---
# <a name="how-to-use-getglobalservice"></a>Cómo: Usar GetGlobalService
En ocasiones, es posible que necesite obtener un servicio desde una ventana de herramientas o un contenedor de controles que no se haya puesto en el sitio, o bien que se haya puesto en un proveedor de servicios que no conozca el servicio que desea. Por ejemplo, puede que desee escribir en el registro de actividad desde un control. Para obtener más información sobre estos y otros escenarios, consulte [Cómo: solucionar problemas](../extensibility/how-to-troubleshoot-services.md)de los servicios.  
  
 Puede obtener la mayoría [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] de los servicios llamando al <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método estático.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> se basa en un proveedor de servicios en caché que se inicializa la primera vez que se sitúa en el sitio un VSPackage derivado de <xref:Microsoft.VisualStudio.Shell.Package> . Debe garantizar que se cumpla esta condición, o bien estar preparado para un servicio nulo.  
  
 Afortunadamente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funciona correctamente la mayor parte del tiempo.  
  
- Si un VSPackage proporciona un servicio conocido solo para otro VSPackage, el VSPackage que solicita el servicio se encuentra en el sitio antes de que se cargue el VSPackage que proporciona el servicio.  
  
- Si un VSPackage crea una ventana de herramientas, el VSPackage se encuentra en el sitio antes de crear la ventana de herramientas.  
  
- Si un contenedor de control está hospedado en una ventana de herramientas creada por un VSPackage, el VSPackage se encuentra en el sitio antes de que se cree el contenedor de control.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Para obtener un servicio desde una ventana de herramientas o un contenedor de controles  
  
- Inserte este código en el constructor, la ventana de herramientas o el contenedor de controles:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Este código obtiene un servicio SVsActivityLog y lo convierte en una <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz, que se puede utilizar para escribir en el registro de actividad. Para obtener un ejemplo, consulte [Cómo: usar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Consulte también  
 [Cómo: solucionar problemas de servicios](../extensibility/how-to-troubleshoot-services.md)   
 [Uso y suministro de servicios](../extensibility/using-and-providing-services.md)   
 [Conceptos básicos del servicio](../extensibility/internals/service-essentials.md)