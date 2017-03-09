---
title: "C&#243;mo: Usar GetGlobalService | Microsoft Docs"
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
  - "servicios, GetGlobalService"
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# C&#243;mo: Usar GetGlobalService
A veces puede ser necesario obtener un servicio de un contenedor de ventana de herramientas o control que no se ha encontrado, o bien se ha encontrado con un proveedor de servicios que no sabe sobre el servicio que desea.  Por ejemplo, puede escribir en el registro de actividad dentro de un control.  Para obtener más información sobre éstos y otros escenarios, vea [Cómo: solucionar problemas de servicios](../extensibility/how-to-troubleshoot-services.md).  
  
 Puede obtener la mayoría de los servicios de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] llamando al método estático de <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> .  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> se basa en un proveedor de servicios almacenado en caché se busque que inicializa la primera vez cualquier VSPackage derivado de <xref:Microsoft.VisualStudio.Shell.Package> .  Debe garantizar que esta condición se cumple, o bien estar preparado para un servicio null.  
  
 Afortunadamente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funciona correctamente la mayoría de los casos.  
  
-   Si un VSPackage proporciona un servicio conocido sólo a otro paquete VSPackage, se localiza el Paquete que solicita el servicio antes de que el Paquete que proporciona el servicio se carga.  
  
-   Si una ventana de herramientas crea un VSPackage, se encuentra el Paquete antes de que se cree la ventana de herramientas.  
  
-   Si un contenedor de control se hospeda en una ventana de herramientas creada por un VSPackage, se encuentra el Paquete antes de que se cree el contenedor del control.  
  
### Para obtener un servicio dentro de un contenedor de ventana de herramientas o control  
  
-   Inserte este código en el constructor, la ventana de herramientas, o el contenedor del control:  
  
     [!code-vb[UseGetGlobalService#1](../misc/codesnippet/VisualBasic/how-to-use-getglobalservice_1.vb)]
     [!code-cs[UseGetGlobalService#1](../misc/codesnippet/CSharp/how-to-use-getglobalservice_1.cs)]  
  
     Este código obtiene un servicio y las conversiones de SVsActivityLog a una interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> , que se puede utilizar para escribir en el registro de actividades.  Para obtener un ejemplo, vea [Cómo: utilizar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).  
  
## Vea también  
 [Cómo: solucionar problemas de servicios](../extensibility/how-to-troubleshoot-services.md)   
 [Utilizar y proporcionar servicios](../extensibility/using-and-providing-services.md)   
 [Fundamentos del servicio](../extensibility/internals/service-essentials.md)