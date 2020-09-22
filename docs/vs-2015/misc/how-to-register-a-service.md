---
title: Cómo registrar un servicio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: f41578f2522487f746a469933a2269a621390f3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842439"
---
# <a name="how-to-register-a-service"></a>Procedimiento: registrar un servicio
El marco de trabajo de paquetes administrados (MPF) ofrece atributos para controlar el registro de servicios administrados. La utilidad RegPkg usa estos atributos para registrar un servicio con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Ejemplo  
 El código que sigue es de [ejemplos de VSSDK](../misc/vssdk-samples.md).  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> registra el servicio SMyGlobalService con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obtener más información sobre <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> y <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> , vea [registrar y anular el registro de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Para registrar un servicio que reemplace otro con el mismo nombre, utilice <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> en lugar de <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>.  
  
## <a name="robust-programming"></a>Programación sólida  
 Para que sea más fácil volver a compilar un proveedor de servicios sin cambiar el cliente del servicio, o viceversa, puede definir el servicio y sus interfaces en un módulo de ensamblado independiente. El código siguiente procede del archivo IMyGlobalService.cs del ejemplo Reference.Services (C#).  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> es necesario para obtener la interfaz desde código no administrado.  
  
> [!NOTE]
> Aunque podría utilizar el mismo tipo o GUID para el servicio y la interfaz, se recomienda separar los dos porque un servicio puede exponer interfaces diferentes.  
  
## <a name="see-also"></a>Consulte también  
 [Registrar VSPackages](../extensibility/internals/registering-vspackages.md)   
 [Conceptos básicos del servicio](../extensibility/internals/service-essentials.md)