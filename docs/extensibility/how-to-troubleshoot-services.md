---
title: "C&#243;mo: solucionar problemas de servicios | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servicios, solución de problemas"
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: solucionar problemas de servicios
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Hay varios problemas comunes que pueden producirse cuando intenta obtener un servicio:  
  
-   El servicio no está registrado con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Tipo de interfaz y no por tipo de servicio, se solicita el servicio.  
  
-   No se ha ubicado el VSPackage que solicite el servicio.  
  
-   Se utiliza el proveedor de servicio incorrecta.  
  
 Si no se puede obtener el servicio solicitado, la llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> devuelve null. Siempre debe probar null después de solicitar un servicio:  
  
```c#  
IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog; if (log == null) return;  
```  
  
### Solucionar problemas de un servicio  
  
1.  Examine el registro del sistema para ver si el servicio se ha registrado correctamente. Para obtener más información, consulta [Registrar servicios](../misc/registering-services.md).  
  
     El siguiente fragmento del archivo .reg muestra cómo se puede registrar el servicio SVsTextManager:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}] @="{F5E7E720-1401-11d1-883B-0000F87579D2}" "Name"="SVsTextManager"  
    ```  
  
     En el ejemplo anterior, el número de versión es la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], como 12.0 o 14.0, la clave {F5E7E71D\-1401\-11d1\-883B\-0000F87579D2} es el identificador de servicio \(SID\) del servicio, SVsTextManager, y el valor predeterminado {F5E7E720\-1401\-11d1\-883B\-0000F87579D2} es el GUID del administrador VSPackage, que proporciona el servicio de texto del paquete.  
  
2.  Utilice el tipo de servicio y no el tipo de interfaz al llamar a GetService. Cuando se solicita un servicio de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> extrae el GUID del tipo. No se encuentre un servicio si se cumplen las condiciones siguientes:  
  
    1.  Un tipo de interfaz se pasa a GetService en lugar del tipo de servicio.  
  
    2.  Ningún GUID se asigna explícitamente a la interfaz. Por lo tanto, el sistema crea un GUID predeterminado de un objeto según sea necesario.  
  
3.  Asegúrese de que se sitúa el VSPackage que solicite el servicio.[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sitios un VSPackage después de crear y antes de llamar a <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Si tiene código en un constructor de VSPackage que necesita un servicio, muévalo al método Initialize.  
  
4.  Asegúrese de que está utilizando el proveedor de servicio correcta.  
  
     No todos los proveedores de servicios son iguales. El proveedor de servicios que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pasa a una ventana de herramientas difiere de la que se pasa a un VSPackage. El proveedor de servicios de la ventana de herramienta conoce <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, pero no conoce <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Puede llamar a <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> para obtener un proveedor de servicios de VSPackage desde dentro de una ventana de herramientas.  
  
     Si una ventana de herramientas hospeda un control de usuario o cualquier otro contenedor de control, el contenedor se sitúa el modelo de componentes de Windows y no tendrá acceso a cualquier [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] servicios. Puede llamar a <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> para obtener un proveedor de servicios de VSPackage desde dentro de un contenedor de control.  
  
## Vea también  
 [Lista de servicios disponibles](../extensibility/internals/list-of-available-services.md)   
 [Utilizar y proporcionar servicios](../extensibility/using-and-providing-services.md)   
 [Fundamentos del servicio](../extensibility/internals/service-essentials.md)