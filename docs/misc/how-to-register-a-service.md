---
title: "Procedimiento: registrar un servicio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servicios, registrar"
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Procedimiento: registrar un servicio
El marco de trabajo de paquetes administrados \(MPF\) ofrece atributos para controlar el registro de servicios administrados. La utilidad RegPkg usa estos atributos para registrar un servicio con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Ejemplo  
 El código siguiente es de [Muestras de VSSDK](../misc/vssdk-samples.md).  
  
 [!code-vb[VSSDKRegisterService#1](../misc/codesnippet/VisualBasic/how-to-register-a-service_1.vb)]
 [!code-cs[VSSDKRegisterService#1](../misc/codesnippet/CSharp/how-to-register-a-service_1.cs)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> registra el servicio SMyGlobalService con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obtener más información acerca de <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> y <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, vea [Registrar y anular el registro VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Para registrar un servicio que reemplace otro con el mismo nombre, utilice <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> en lugar de <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>.  
  
## Programación eficaz  
 Para que sea más fácil volver a compilar un proveedor de servicios sin cambiar el cliente del servicio, o viceversa, puede definir el servicio y sus interfaces en un módulo de ensamblado independiente. El código siguiente procede del archivo IMyGlobalService.cs del ejemplo Reference.Services \(C\#\).  
  
 [!code-vb[VSSDKRegisterService#2](../misc/codesnippet/VisualBasic/how-to-register-a-service_2.vb)]
 [!code-cs[VSSDKRegisterService#2](../misc/codesnippet/CSharp/how-to-register-a-service_2.cs)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> es necesario para obtener la interfaz desde código no administrado.  
  
> [!NOTE]
>  Aunque podría utilizar el mismo tipo o GUID para el servicio y la interfaz, se recomienda separar los dos porque un servicio puede exponer interfaces diferentes.  
  
## Vea también  
 [Registering VSPackages](http://msdn.microsoft.com/es-es/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [Fundamentos del servicio](../extensibility/internals/service-essentials.md)