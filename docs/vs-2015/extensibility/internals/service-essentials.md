---
title: Aspectos básicos del servicio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 407dda2f203b7be20b19c0e296caa9ce1c95b32c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696080"
---
# <a name="service-essentials"></a>Conceptos básicos del servicio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un servicio es un contrato entre dos VSPackages. Un VSPackage proporciona un conjunto específico de interfaces para que lo consuma otro VSPackage. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] es en sí misma una colección de VSPackages que proporciona servicios a otros VSPackages.  
  
 Por ejemplo, puede usar el servicio SVsActivityLog para obtener una interfaz IVsActivityLog, que puede usar para escribir en el registro de actividad. Para obtener más información, vea [Cómo: usar el registro de actividad](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] también proporciona algunos servicios integrados que no están registrados. Los paquetes VSPackage pueden reemplazar los servicios integrados u otros servicios proporcionando una invalidación de servicio. Solo se permite una invalidación de servicio para cualquier servicio.  
  
 Los servicios no tienen ninguna capacidad de detección. Por lo tanto, debe conocer el identificador de servicio (SID) de un servicio que desea consumir y debe saber qué interfaces proporciona. La documentación de referencia del servicio proporciona esta información.  
  
- Los VSPackages que proporcionan servicios se denominan proveedores de servicios.  
  
- Los servicios que se proporcionan a otros VSPackages se denominan servicios globales.  
  
- Los servicios que solo están disponibles para el VSPackage que los implementa, o para cualquier objeto que crea, se denominan servicios locales.  
  
- Los servicios que reemplazan servicios integrados o servicios proporcionados por otros paquetes se denominan invalidaciones de servicio.  
  
- Los servicios, o las invalidaciones de servicio, se cargan a petición, es decir, el proveedor de servicios se carga cuando otro VSPackage solicita el servicio que proporciona.  
  
- Para admitir la carga a petición, un proveedor de servicios registra sus servicios globales con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Para obtener más información, vea [registrar servicios](../../misc/registering-services.md).  
  
- Después de obtener un servicio, use [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (código no administrado) o la conversión (código administrado) para obtener la interfaz deseada, por ejemplo:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
- El código administrado hace referencia a un servicio por su tipo, mientras que el código no administrado hace referencia a un servicio por su GUID.  
  
- Cuando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] carga un VSPackage, pasa un proveedor de servicios al VSPackage para proporcionar al VSPackage acceso a servicios globales. Esto se conoce como "emplazamiento" el VSPackage.  
  
- Los VSPackages pueden ser proveedores de servicios para los objetos que crean. Por ejemplo, un formulario podría enviar una solicitud de un servicio de color a su fotograma, lo que podría pasar la solicitud a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- Los objetos administrados profundamente anidados, o que no se encuentran en el sitio, pueden llamar a <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> para obtener acceso directo a los servicios globales. Para obtener más información, consulte [Cómo: usar GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Consulte también  
 [Lista de servicios disponibles](../../extensibility/internals/list-of-available-services.md)   
 [Uso y suministro de servicios](../../extensibility/using-and-providing-services.md)   
 [Conversiones de tipos y conversión](https://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [Conversión](https://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)
