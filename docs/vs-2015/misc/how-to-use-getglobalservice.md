---
title: Filtrar Usar GetGlobalService | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 0161b3e44b44567166a337d94101778074561e80
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "58995187"
---
# <a name="how-to-use-getglobalservice"></a>Filtrar Usar GetGlobalService
A veces es posible que necesita obtener un servicio de una ventana de herramientas o control contenedor que no se ha ubicado, o bien que se ha ubicado con un proveedor de servicios que no conoce el servicio que desee. Por ejemplo, puede escribir en el registro de actividad desde dentro de un control. Para obtener más información sobre estos y otros escenarios, consulte [Cómo: Solucionar problemas de servicios](../extensibility/how-to-troubleshoot-services.md).  
  
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
  
     Este código obtiene un servicio SVsActivityLog y lo convierte a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz, que puede usarse para escribir en el registro de actividad. Como ejemplo, vea [Cómo: Usar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Solucionar problemas de servicios](../extensibility/how-to-troubleshoot-services.md)   
 [Uso y provisión de servicios](../extensibility/using-and-providing-services.md)   
 [Conceptos básicos del servicio](../extensibility/internals/service-essentials.md)