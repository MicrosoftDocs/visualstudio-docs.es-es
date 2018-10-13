---
title: Fundamentos de servicio | Documentos de Microsoft
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
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec9ccc92a8650c71336fc4a6916b797bd449dc7a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178144"
---
# <a name="service-essentials"></a>Conceptos básicos del servicio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un servicio es un contrato entre dos VSPackages. Un VSPackage proporciona un conjunto específico de interfaces para otro paquete de VS consumir. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] es una colección de VSPackages que proporciona servicios a otros VSPackages.  
  
 Por ejemplo, puede usar el servicio SVsActivityLog para obtener una interfaz IVsActivityLog, que puede usar para escribir en el registro de actividad. Para obtener más información, consulte [Cómo: usar el registro de actividad](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] También proporciona algunos servicios integrados que no están registradas. Los paquetes VSPackage pueden reemplazar integrados u otros servicios al proporcionar un reemplazo de servicio. Se permite la invalidación de un único servicio para cualquier servicio.  
  
 Los servicios no tienen ningún detectabilidad. Por lo tanto, debe conocer el identificador de servicio (SID) de un servicio que desea consumir, y debe saber qué interfaces proporciona. La documentación de referencia para el servicio proporciona esta información.  
  
-   Los VSPackages que proporcionan servicios se llama a los proveedores de servicios.  
  
-   Servicios que se proporcionan a otros VSPackages se denominan servicios globales.  
  
-   Servicios que están disponibles solo para el VSPackage que implemente en ellos, o a cualquier objeto que crea, se llama a los servicios locales.  
  
-   Servicios que reemplazar servicios integrados o servicios proporcionados por otros paquetes, se denominan invalidaciones de servicio.  
  
-   Servicios o las invalidaciones de servicio, se cargan a petición, es decir, se carga el proveedor de servicios cuando se solicite el servicio que proporciona otro VSPackage.  
  
-   Para admitir la carga a petición, un proveedor de servicios registra sus servicios globales con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Para obtener más información, consulte [registrar servicios](../../misc/registering-services.md).  
  
-   Después de obtener un servicio, utilice [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (código no administrado) o conversión (código administrado) para obtener la interfaz deseada, por ejemplo:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Código administrado se refiere a un servicio por su tipo, mientras que el código no administrado se refiere a un servicio por su GUID.  
  
-   Cuando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] carga un paquete VSPackage, pasa un proveedor de servicios a VSPackage para permitir el acceso de VSPackage a servicios globales. Esto se conoce como "situación" el VSPackage.  
  
-   Los VSPackages pueden proveedores de servicios para los objetos que creen. Por ejemplo, un formulario puede enviar una solicitud para un servicio de color con el marco, que podría pasar la solicitud a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
-   Pueden llamar objetos administrados que están profundamente anidados o no está ubicados en absoluto, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> para el acceso directo a los servicios globales. Para obtener más información, consulte [Cómo: usar GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Vea también  
 [Lista de servicios disponibles](../../extensibility/internals/list-of-available-services.md)   
 [Uso y provisión de servicios](../../extensibility/using-and-providing-services.md)   
 [Casting and Type Conversions](http://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)  (Conversiones de tipos [Guía de programación de C#])  
 [Conversión](http://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)

