---
title: 'Cómo: registrar un servicio | Microsoft Docs'
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
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: douge
ms.openlocfilehash: a242a13893c7cd303adfe266c9609b7a71d251ba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575526"
---
# <a name="how-to-register-a-service"></a>Procedimiento: registrar un servicio
El marco de trabajo de paquetes administrados (MPF) ofrece atributos para controlar el registro de servicios administrados. La utilidad RegPkg usa estos atributos para registrar un servicio con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Ejemplo  
 El código siguiente procede [muestras de VSSDK](../misc/vssdk-samples.md).  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 El <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> registra el servicio SMyGlobalService con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obtener más información acerca de <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> y <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, consulte [registrar y anular el registro de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Para registrar un servicio que reemplace otro con el mismo nombre, use la <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> en lugar de la <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>.  
  
## <a name="robust-programming"></a>Programación sólida  
 Para que sea más fácil volver a compilar un proveedor de servicios sin cambiar el cliente del servicio, o viceversa, puede definir el servicio y sus interfaces en un módulo de ensamblado independiente. El código siguiente procede del archivo IMyGlobalService.cs del ejemplo Reference.Services (C#).  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 El <xref:System.Runtime.InteropServices.ComVisibleAttribute> es necesaria para obtener la interfaz desde código no administrado.  
  
> [!NOTE]
>  Aunque podría utilizar el mismo tipo o GUID para el servicio y la interfaz, se recomienda separar los dos porque un servicio puede exponer interfaces diferentes.  
  
## <a name="see-also"></a>Vea también  
 [Registro de VSPackages](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [Conceptos básicos del servicio](../extensibility/internals/service-essentials.md)