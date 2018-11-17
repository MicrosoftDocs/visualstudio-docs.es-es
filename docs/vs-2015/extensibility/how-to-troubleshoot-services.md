---
title: 'Cómo: solucionar problemas de servicios | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8df01dcc2c8e15144f6049148286012bda6ac3f5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798214"
---
# <a name="how-to-troubleshoot-services"></a>Cómo: solucionar problemas de servicios
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hay varios problemas comunes que pueden producirse al intentar obtener un servicio:  
  
- El servicio no está registrado con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Tipo de interfaz y no por tipo de servicio, se solicita el servicio.  
  
- El VSPackage que solicita el servicio no que se ha ubicado.  
  
- Se utiliza el proveedor de servicio incorrecto.  
  
  Si el servicio solicitado no se puede obtener la llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> devuelve null. Siempre debe probar null después de solicitar un servicio:  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>Para solucionar problemas de un servicio  
  
1.  Examine el registro del sistema para ver si el servicio se ha registrado correctamente. Para obtener más información, consulte [registrar servicios](../misc/registering-services.md).  
  
     El siguiente fragmento del archivo .reg muestra cómo se puede registrar el servicio SVsTextManager:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     En el ejemplo anterior, el número de versión es la versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], como 12.0 o 14.0, la clave {F5E7E71D-1401-11d1-883B-0000F87579D2} es el identificador de servicio (SID) del servicio, SVsTextManager y el valor de predeterminada {} F5E7E720-1401-11D1-883B-0000F87579D2} es el GUID del Administrador de texto VSPackage, que ofrece el servicio del paquete.  
  
2.  Utilice el tipo de servicio y no el tipo de interfaz al llamar a GetService. Cuando se solicita un servicio de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], <xref:Microsoft.VisualStudio.Shell.Package> extrae el GUID del tipo. No se encontrará un servicio si se cumplen las condiciones siguientes:  
  
    1.  Un tipo de interfaz se pasa a GetService en lugar del tipo de servicio.  
  
    2.  Ningún GUID se asigna explícitamente a la interfaz. Por lo tanto, el sistema crea una GUID de forma predeterminada para un objeto según sea necesario.  
  
3.  Asegúrese de que se ha ubicado el VSPackage que solicita el servicio. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Después de crear y antes de llamar a los sitios un VSPackage <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Si tiene código en un constructor de VSPackage que necesita un servicio, muévalo al método Initialize.  
  
4.  Asegúrese de que está usando el proveedor de servicio correcto.  
  
     No todos los proveedores de servicios son iguales. El proveedor de servicios que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pasa a una ventana de herramientas es diferente al pasa a un VSPackage. El proveedor de servicios de la ventana de herramienta conoce <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, pero no conoce <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Puede llamar a <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> para obtener un proveedor de servicios de VSPackage desde dentro de una ventana de herramientas.  
  
     Si una ventana de herramientas hospeda un control de usuario o cualquier otro contenedor de control, el contenedor se sitúa el modelo de componentes de Windows y no tendrá acceso a cualquier [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] servicios. Puede llamar a <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> para obtener un proveedor de servicios de VSPackage desde dentro de un contenedor de control.  
  
## <a name="see-also"></a>Vea también  
 [Lista de servicios disponibles](../extensibility/internals/list-of-available-services.md)   
 [Uso y provisión de servicios](../extensibility/using-and-providing-services.md)   
 [Conceptos básicos del servicio](../extensibility/internals/service-essentials.md)

