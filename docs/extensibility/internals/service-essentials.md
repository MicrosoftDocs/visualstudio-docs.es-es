---
title: Aspectos básicos del servicio | Microsoft Docs
description: Obtenga información sobre los servicios, que son interfaces para que los consuma otro VSPackage. Los servicios de un VSPackage pueden invalidar los servicios integrados u otros servicios.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 54d785d665122fd5c5fa1709aa9348777e3c730b
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875809"
---
# <a name="service-essentials"></a>Conceptos básicos del servicio
Un servicio es un contrato entre dos VSPackages. Un VSPackage proporciona un conjunto específico de interfaces para que lo consuma otro VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es en sí misma una colección de VSPackages que proporciona servicios a otros VSPackages.

 Por ejemplo, puede usar el servicio SVsActivityLog para obtener una interfaz IVsActivityLog, que puede usar para escribir en el registro de actividad. Para obtener más información, vea [Cómo: usar el registro de actividad](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] también proporciona algunos servicios integrados que no están registrados. Los paquetes VSPackage pueden reemplazar los servicios integrados u otros servicios proporcionando una invalidación de servicio. Solo se permite una invalidación de servicio para cualquier servicio.

 Los servicios no tienen ninguna capacidad de detección. Por lo tanto, debe conocer el identificador de servicio (SID) de un servicio que desea consumir y debe saber qué interfaces proporciona. La documentación de referencia del servicio proporciona esta información.

- Los VSPackages que proporcionan servicios se denominan proveedores de servicios.

- Los servicios que se proporcionan a otros VSPackages se denominan servicios globales.

- Los servicios que solo están disponibles para el VSPackage que los implementa, o para cualquier objeto que crea, se denominan servicios locales.

- Los servicios que reemplazan servicios integrados o servicios proporcionados por otros paquetes se denominan invalidaciones de servicio.

- Los servicios, o las invalidaciones de servicio, se cargan a petición, es decir, el proveedor de servicios se carga cuando otro VSPackage solicita el servicio que proporciona.

- Para admitir la carga a petición, un proveedor de servicios registra sus servicios globales con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Para obtener más información, consulte [Cómo: proporcionar un servicio](../../extensibility/how-to-provide-a-service.md).

- Después de obtener un servicio, use [QueryInterface](/cpp/atl/queryinterface) (código no administrado) o la conversión (código administrado) para obtener la interfaz deseada, por ejemplo:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- El código administrado hace referencia a un servicio por su tipo, mientras que el código no administrado hace referencia a un servicio por su GUID.

- Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga un VSPackage, pasa un proveedor de servicios al VSPackage para proporcionar al VSPackage acceso a servicios globales. Esto se conoce como "emplazamiento" el VSPackage.

- Los VSPackages pueden ser proveedores de servicios para los objetos que crean. Por ejemplo, un formulario podría enviar una solicitud de un servicio de color a su fotograma, lo que podría pasar la solicitud a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- Los objetos administrados profundamente anidados, o que no se encuentran en el sitio, pueden llamar a <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> para obtener acceso directo a los servicios globales.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Usar GetGlobalService

En ocasiones, es posible que necesite obtener un servicio desde una ventana de herramientas o un contenedor de controles que no se haya puesto en el sitio, o bien que se haya puesto en un proveedor de servicios que no conozca el servicio que desea. Por ejemplo, puede que desee escribir en el registro de actividad desde un control. Para obtener más información sobre estos y otros escenarios, consulte [Cómo: solucionar problemas](../../extensibility/how-to-troubleshoot-services.md)de los servicios.

Puede obtener la mayoría de los servicios de Visual Studio llamando al <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método estático.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> se basa en un proveedor de servicios en caché que se inicializa la primera vez que se encuentra en el sitio un VSPackage derivado del paquete. Debe garantizar que se cumpla esta condición, o bien estar preparado para un servicio nulo.

Afortunadamente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funciona correctamente la mayor parte del tiempo.

- Si un VSPackage proporciona un servicio conocido solo para otro VSPackage, el VSPackage que solicita el servicio se encuentra en el sitio antes de que se cargue el VSPackage que proporciona el servicio.

- Si un VSPackage crea una ventana de herramientas, el VSPackage se encuentra en el sitio antes de crear la ventana de herramientas.

- Si un contenedor de control está hospedado en una ventana de herramientas creada por un VSPackage, el VSPackage se encuentra en el sitio antes de que se cree el contenedor de control.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Para obtener un servicio desde una ventana de herramientas o un contenedor de controles

- Inserte este código en el constructor, la ventana de herramientas o el contenedor de controles:

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

    Este código obtiene un servicio SVsActivityLog y lo convierte en una interfaz IVsActivityLog, que se puede usar para escribir en el registro de actividad. Para obtener un ejemplo, consulte [Cómo: usar el registro de actividad](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Consulte también

- [Lista de servicios disponibles](../../extensibility/internals/list-of-available-services.md)
- [Uso y prestación de servicios](../../extensibility/using-and-providing-services.md)
- [Conversiones de tipos](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Conversión](/cpp/cpp/casting)
