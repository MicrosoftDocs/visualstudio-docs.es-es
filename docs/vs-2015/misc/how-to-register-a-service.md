---
title: Filtrar Registrar un servicio | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: 0ec69fa123775cb477195d4022fb439fb990f415
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "59002820"
---
# <a name="how-to-register-a-service"></a>Filtrar Registrar un servicio
El marco de trabajo de paquetes administrados (MPF) ofrece atributos para controlar el registro de servicios administrados. La utilidad RegPkg usa estos atributos para registrar un servicio con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Ejemplo  
 El código siguiente procede [muestras de VSSDK](../misc/vssdk-samples.md).  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> registra el servicio SMyGlobalService con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obtener más información acerca de <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> y <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, consulte [registrar y anular el registro de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Para registrar un servicio que reemplace otro con el mismo nombre, utilice <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> en lugar de <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>.  
  
## <a name="robust-programming"></a>Programación sólida  
 Para que sea más fácil volver a compilar un proveedor de servicios sin cambiar el cliente del servicio, o viceversa, puede definir el servicio y sus interfaces en un módulo de ensamblado independiente. El código siguiente procede del archivo IMyGlobalService.cs del ejemplo Reference.Services (C#).  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> es necesario para obtener la interfaz desde código no administrado.  
  
> [!NOTE]
>  Aunque podría utilizar el mismo tipo o GUID para el servicio y la interfaz, se recomienda separar los dos porque un servicio puede exponer interfaces diferentes.  
  
## <a name="see-also"></a>Vea también  
 [Registro de VSPackages](../extensibility/internals/registering-vspackages.md)   
 [Conceptos básicos del servicio](../extensibility/internals/service-essentials.md)