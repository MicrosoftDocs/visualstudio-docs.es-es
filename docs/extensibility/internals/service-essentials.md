---
title: Fundamentos de servicio | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72dfb519e35cb0bec94fb73d112e0bff27b0b14
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027963"
---
# <a name="service-essentials"></a>Conceptos básicos del servicio
Un servicio es un contrato entre dos VSPackages. Un VSPackage proporciona un conjunto específico de interfaces para otro paquete de VS consumir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es una colección de VSPackages que proporciona servicios a otros VSPackages.  
  
 Por ejemplo, puede usar el servicio SVsActivityLog para obtener una interfaz IVsActivityLog, que puede usar para escribir en el registro de actividad. Para obtener más información, vea [Cómo: Usar el registro de actividad](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] También proporciona algunos servicios integrados que no están registradas. Los paquetes VSPackage pueden reemplazar integrados u otros servicios al proporcionar un reemplazo de servicio. Se permite la invalidación de un único servicio para cualquier servicio.  
  
 Los servicios no tienen ningún detectabilidad. Por lo tanto, debe conocer el identificador de servicio (SID) de un servicio que desea consumir, y debe saber qué interfaces proporciona. La documentación de referencia para el servicio proporciona esta información.  
  
- Los VSPackages que proporcionan servicios se llama a los proveedores de servicios.  
  
- Servicios que se proporcionan a otros VSPackages se denominan servicios globales.  
  
- Servicios que están disponibles solo para el VSPackage que implemente en ellos, o a cualquier objeto que crea, se llama a los servicios locales.  
  
- Servicios que reemplazar servicios integrados o servicios proporcionados por otros paquetes, se denominan invalidaciones de servicio.  
  
- Servicios o las invalidaciones de servicio, se cargan a petición, es decir, se carga el proveedor de servicios cuando se solicite el servicio que proporciona otro VSPackage.  
  
- Para admitir la carga a petición, un proveedor de servicios registra sus servicios globales con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obtener más información, vea [Cómo: Proporcionar un servicio](../../extensibility/how-to-provide-a-service.md).  
  
- Después de obtener un servicio, utilice [QueryInterface](/cpp/atl/queryinterface) (código no administrado) o conversión (código administrado) para obtener la interfaz deseada, por ejemplo:  
  
  ```vb  
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
  ```  
  
  ```csharp  
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  ```  
  
- Código administrado se refiere a un servicio por su tipo, mientras que el código no administrado se refiere a un servicio por su GUID.  
  
- Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga un paquete VSPackage, pasa un proveedor de servicios a VSPackage para permitir el acceso de VSPackage a servicios globales. Esto se conoce como "situación" el VSPackage.  
  
- Los VSPackages pueden proveedores de servicios para los objetos que creen. Por ejemplo, un formulario puede enviar una solicitud para un servicio de color con el marco, que podría pasar la solicitud a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
- Pueden llamar objetos administrados que están profundamente anidados o no está ubicados en absoluto, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> para el acceso directo a los servicios globales.   
  
<a name="how-to-use-getglobalservice"></a>  
  
## <a name="use-getglobalservice"></a>Usar GetGlobalService  
  
A veces es posible que necesita obtener un servicio de una ventana de herramientas o control contenedor que no se ha ubicado, o bien que se ha ubicado con un proveedor de servicios que no conoce el servicio que desee. Por ejemplo, puede escribir en el registro de actividad desde dentro de un control. Para obtener más información sobre estos y otros escenarios, consulte [Cómo: Solucionar problemas de servicios](../../extensibility/how-to-troubleshoot-services.md).  
  
Puede obtener la mayoría de los servicios de Visual Studio mediante una llamada a estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método.  
  
<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> se basa en un servicio en caché se basa en un proveedor que se inicializa por primera vez cualquier VSPackage derivado de paquete. Debe garantizar que esta condición se cumple o bien estar preparada para un servicio nulo.  
  
Afortunadamente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funciona correctamente la mayoría del tiempo.  
  
-   Si un paquete VSPackage proporciona un servicio conocido solo a otro VSPackage, se basa en un VSPackage que solicita el servicio antes de VSPackage que proporciona que el servicio está cargado.  
  
-   Si una ventana de herramientas se crea un VSPackage, el VSPackage está situado antes de crea la ventana de herramientas.  
  
-   Si un contenedor de control se hospeda en una ventana de herramienta creada por un VSPackage, el VSPackage está situado antes de crea el contenedor del control.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Para obtener un servicio desde dentro de un contenedor de control o ventana de herramienta  
  
-   Inserte este código en el constructor, la ventana de herramientas o el contenedor de controles:  
  
    ```csharp  
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```  
    ```vb  
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```  
    
    Este código obtiene un servicio SVsActivityLog y lo convierte en una interfaz IVsActivityLog, que se puede utilizar para escribir en el registro de actividad. Como ejemplo, vea [Cómo: Usar el registro de actividad](../../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Vea también  
 [Lista de servicios disponibles](../../extensibility/internals/list-of-available-services.md)   
 [Uso y provisión de servicios](../../extensibility/using-and-providing-services.md)   
 [Casting and Type Conversions](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)  (Conversiones de tipos [Guía de programación de C#])  
 [Conversión](/cpp/cpp/casting)