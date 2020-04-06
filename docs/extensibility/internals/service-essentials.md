---
title: Fundamentos del servicio ? Microsoft Docs
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
ms.openlocfilehash: 0e2947cb4cd6a347d8e010340f8689eb1907a28a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705501"
---
# <a name="service-essentials"></a>Conceptos básicos del servicio
Un servicio es un contrato entre dos VSPackages. Un VSPackage proporciona un conjunto específico de interfaces para otro VSPackage para consumir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]es en sí misma una colección de VSPackages que proporciona servicios a otros VSPackages.

 Por ejemplo, puede usar el servicio SVsActivityLog para obtener una interfaz IVsActivityLog, que puede usar para escribir en el registro de actividad. Para obtener más información, consulte [Cómo: Usar el registro](../../extensibility/how-to-use-the-activity-log.md)de actividad .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]también proporciona algunos servicios integrados que no están registrados. VSPackages puede reemplazar los servicios integrados u otros proporcionando una invalidación de servicio. Solo se permite una invalidación de servicio para cualquier servicio.

 Los servicios no tienen capacidad de detección. Por lo tanto, debe conocer el identificador de servicio (SID) de un servicio que desea consumir y debe saber qué interfaces proporciona. La documentación de referencia para el servicio proporciona esta información.

- VSPackages que proporcionan servicios se denominan proveedores de servicios.

- Los servicios que se proporcionan a otros VSPackages se denominan servicios globales.

- Los servicios que solo están disponibles para el VSPackage que los implementa, o para cualquier objeto que crea, se denominan servicios locales.

- Los servicios que reemplazan los servicios integrados o los servicios proporcionados por otros paquetes se denominan invalidaciones de servicio.

- Los servicios, o invalidaciones de servicio, se cargan a petición, es decir, el proveedor de servicios se carga cuando otro VSPackage solicita el servicio que proporciona.

- Para admitir la carga bajo demanda, un proveedor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de servicios registra sus servicios globales con . Para obtener más información, consulte [Cómo: proporcionar un servicio](../../extensibility/how-to-provide-a-service.md).

- Después de obtener un servicio, utilice [QueryInterface](/cpp/atl/queryinterface) (código no administrado) o conversión (código administrado) para obtener la interfaz deseada, por ejemplo:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- El código administrado hace referencia a un servicio por su tipo, mientras que el código no administrado hace referencia a un servicio por su GUID.

- Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga un VSPackage, pasa un proveedor de servicios al VSPackage para dar el VSPackage acceso a los servicios globales. Esto se conoce como "sentar" el VSPackage.

- VSPackages pueden ser proveedores de servicios para los objetos que crean. Por ejemplo, un formulario puede enviar una solicitud de un servicio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de color a su marco, que podría pasar la solicitud a .

- Los objetos administrados que están profundamente anidados, o que no están sitios en absoluto, pueden requerir <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> acceso directo a los servicios globales.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Usar GetGlobalService

A veces es posible que necesite obtener un servicio desde una ventana de herramientas o un contenedor de control que no se ha ubicado, o bien se ha ubicado con un proveedor de servicios que no conoce el servicio que desea. Por ejemplo, es posible que desee escribir en el registro de actividad desde dentro de un control. Para obtener más información acerca de estos y otros escenarios, vea [Cómo: Solucionar problemas de servicios](../../extensibility/how-to-troubleshoot-services.md).

Puede obtener la mayoría de los <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> servicios de Visual Studio llamando al método estático.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>se basa en un proveedor de servicios en caché que se inicializa la primera vez que se encuentra cualquier VSPackage derivado de Package. Debe garantizar que se cumple esta condición o, de lo contrario, estar preparado para un servicio nulo.

Afortunadamente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funciona correctamente la mayor parte del tiempo.

- Si un VSPackage proporciona un servicio conocido sólo para otro VSPackage, el VSPackage que solicita el servicio se encuentra antes de que se cargue el VSPackage que proporciona el servicio.

- Si un VSPackage crea una ventana de herramientas, el VSPackage se encuentra antes de crear la ventana de herramientas.

- Si un contenedor de controles está hospedado por una ventana de herramientas creada por un VSPackage, el VSPackage se encuentra antes de crear el contenedor de control.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Para obtener un servicio desde una ventana de herramientas o un contenedor de control

- Inserte este código en el constructor, la ventana de herramientas o el contenedor de control:

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

    Este código obtiene un servicio SVsActivityLog y lo convierte en una interfaz IVsActivityLog, que se puede usar para escribir en el registro de actividad. Para obtener un ejemplo, vea [Cómo: Usar el registro](../../extensibility/how-to-use-the-activity-log.md)de actividad .

## <a name="see-also"></a>Vea también

- [Lista de servicios disponibles](../../extensibility/internals/list-of-available-services.md)
- [Uso y prestación de servicios](../../extensibility/using-and-providing-services.md)
- [Conversiones de tipos](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Conversión](/cpp/cpp/casting)
