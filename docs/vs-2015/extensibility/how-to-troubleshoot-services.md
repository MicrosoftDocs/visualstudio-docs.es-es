---
title: 'Cómo: solucionar problemas de servicios | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5311aa3ff390611942aa91cb1f2a53ca5a76258d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204069"
---
# <a name="how-to-troubleshoot-services"></a>Servicios de solución de problemas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hay varios problemas comunes que pueden producirse al intentar obtener un servicio:  
  
- El servicio no está registrado con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- El servicio se solicita por el tipo de interfaz y no por el tipo de servicio.  
  
- No se ha puesto en sitio el VSPackage que solicita el servicio.  
  
- Se utiliza el proveedor de servicios equivocado.  
  
  Si no se puede obtener el servicio solicitado, la llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> devuelve NULL. Siempre debe comprobar si el valor es NULL después de solicitar un servicio:  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>Para solucionar problemas de un servicio  
  
1. Examine el registro del sistema para ver si el servicio se ha registrado correctamente. Para obtener más información, vea [registrar servicios](../misc/registering-services.md).  
  
     En el siguiente fragmento de archivo. reg se muestra cómo se puede registrar el servicio SVsTextManager:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     En el ejemplo anterior, el número de versión es la versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , como 12,0 o 14,0, la clave {F5E7E71D-1401-11D1-883B-0000F87579D2} es el identificador de servicio (SID) del servicio, SVsTextManager, y el valor predeterminado {F5E7E720-1401-11D1-883B-0000F87579D2} es el GUID del paquete del VSPackage del administrador de texto, que proporciona el servicio.  
  
2. Use el tipo de servicio y no el tipo de interfaz cuando llame a GetService. Al solicitar un servicio de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , <xref:Microsoft.VisualStudio.Shell.Package> extrae el GUID del tipo. No se encontrará un servicio si se dan las condiciones siguientes:  
  
    1. Un tipo de interfaz se pasa a GetService en lugar de al tipo de servicio.  
  
    2. No se asigna ningún GUID explícitamente a la interfaz. Por lo tanto, el sistema crea un GUID predeterminado para un objeto según sea necesario.  
  
3. Asegúrese de que el VSPackage que solicita el servicio se ha puesto en el sitio. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] localiza un VSPackage después de construirlo y antes de llamar a <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .  
  
     Si tiene código en un constructor VSPackage que necesita un servicio, muévalo al método Initialize.  
  
4. Asegúrese de que está usando el proveedor de servicios correcto.  
  
     No todos los proveedores de servicios son iguales. El proveedor de servicios que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pasa a una ventana de herramientas difiere de la que pasa a un VSPackage. El proveedor de servicios de la ventana de herramientas conoce <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> , pero no conoce <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Puede llamar <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> a para obtener un proveedor de servicios de VSPackage desde una ventana de herramientas.  
  
     Si una ventana de herramientas hospeda un control de usuario o cualquier otro contenedor de control, el contenedor se colocará en el modelo de componentes de Windows y no tendrá acceso a ningún [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] servicio. Puede llamar <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> a para obtener un proveedor de servicios de VSPackage desde un contenedor de control.  
  
## <a name="see-also"></a>Consulte también  
 [Lista de servicios disponibles](../extensibility/internals/list-of-available-services.md)   
 [Uso y suministro de servicios](../extensibility/using-and-providing-services.md)   
 [Conceptos básicos del servicio](../extensibility/internals/service-essentials.md)
