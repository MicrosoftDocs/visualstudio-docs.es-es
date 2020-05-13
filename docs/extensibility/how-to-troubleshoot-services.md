---
title: 'Cómo: Solucionar problemas de servicios ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49560acdf57f5dad2c57f2a8e4649f194d6d8298
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710748"
---
# <a name="how-to-troubleshoot-services"></a>Cómo: Solucionar problemas de servicios
Hay varios problemas comunes que pueden ocurrir cuando intenta obtener un servicio:

- El servicio no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]está registrado con .

- El servicio se solicita por tipo de interfaz y no por tipo de servicio.

- El VSPackage que solicita el servicio no se ha sitio.

- Se utiliza el proveedor de servicios incorrecto.

  Si no se puede obtener el <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> servicio solicitado, la llamada a devuelve null. Siempre debe probar si es null después de solicitar un servicio:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Para solucionar problemas de un servicio

1. Examine el registro del sistema para ver si el servicio se ha registrado correctamente. Para obtener más información, consulte [Cómo: proporcionar un servicio](../extensibility/how-to-provide-a-service.md).

    El siguiente fragmento de archivo *.reg* muestra cómo se puede registrar el servicio SVsTextManager:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    En el ejemplo anterior, el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]número de versión es la versión de , como 12.0 o 14.0, la clave .F5E7E71D-1401-11d1-883B-0000F87579D2 es el identificador de servicio (SID) del servicio, SVsTextManager, y el valor predeterminado de f5E7E720-1401-11d1-883B-0000F87579D2 es el GUID de paquete del administrador de texto VSPackage, que proporciona el servicio.

2. Utilice el tipo de servicio y no el tipo de interfaz cuando llame a GetService. Al solicitar un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]servicio <xref:Microsoft.VisualStudio.Shell.Package> de , extrae el GUID del tipo. No se encontrará un servicio si existen las siguientes condiciones:

   1. Un tipo de interfaz se pasa a GetService en lugar del tipo de servicio.

   2. No se asigna ningún GUID explícitamente a la interfaz. Por lo tanto, el sistema crea un GUID predeterminado para un objeto según sea necesario.

3. Asegúrese de que el VSPackage que solicita el servicio se ha sitio. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]sitios de un VSPackage después <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>de construirlo y antes de llamar a .

    Si tiene código en un constructor de VSPackage que `Initialize` necesita un servicio, muévalo al método.

4. Asegúrese de que está utilizando el proveedor de servicios correcto.

    No todos los proveedores de servicios son iguales. El proveedor [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de servicios que pasa a una ventana de herramientas difiere de la que pasa a un VSPackage. El proveedor de servicios <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>de ventana de <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>herramientas conoce , pero no conoce . Puede llamar <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> para obtener un proveedor de servicios VSPackage desde dentro de una ventana de herramientas.

    Si una ventana de herramientas hospeda un control de usuario o cualquier otro contenedor de control, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el modelo de componentes de Windows ubicará el contenedor y no tendrá acceso a ningún servicio. Puede llamar <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> para obtener un proveedor de servicios VSPackage desde dentro de un contenedor de control.

## <a name="see-also"></a>Vea también
- [Lista de servicios disponibles](../extensibility/internals/list-of-available-services.md)
- [Usar y proporcionar servicios](../extensibility/using-and-providing-services.md)
- [Elementos esenciales del servicio](../extensibility/internals/service-essentials.md)
