---
title: Servicio Essentials | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 8ff357d7ed3542a01cf8d98e36b9d0e99a122864
ms.lasthandoff: 04/05/2017

---
# <a name="service-essentials"></a>Fundamentos de servicio
Un servicio es un contrato entre dos VSPackages. Un VSPackage proporciona un conjunto específico de interfaces para otro VSPackage consumir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]es una colección de VSPackages que proporciona servicios a otros VSPackages.  
  
 Por ejemplo, puede usar el servicio SVsActivityLog para obtener una interfaz IVsActivityLog, que puede usar para escribir en el registro de actividad. Para obtener más información, consulte [Cómo: usar el registro de actividad](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]También proporciona algunos servicios integrados que no están registrados. VSPackages puede reemplazar integrados u otros servicios proporcionando una invalidación de servicio. Se permite el reemplazo de un único servicio para cualquier servicio.  
  
 Los servicios no tienen ningún detectabilidad. Por lo tanto, debe conocer el identificador de servicio (SID) de un servicio que desea utilizar, y debe saber qué interfaces proporciona. La documentación de referencia para el servicio proporciona esta información.  
  
-   VSPackages que proporcionan los servicios se denominan proveedores de servicios.  
  
-   Los servicios que se proporcionan a otros VSPackages se llaman servicios globales.  
  
-   Servicios que solo están disponibles para el VSPackage que implemente en ellos, o a cualquier objeto que se crea, se denominan servicios locales.  
  
-   Servicios que reemplazan a los servicios integrados o servicios proporcionados por otros paquetes, se denominan invalidaciones de servicio.  
  
-   Servicios, o las invalidaciones de servicio, se cargan a petición, es decir, el proveedor de servicios se carga cuando se solicite el servicio que proporciona por otro VSPackage.  
  
-   Para admitir la carga a petición, un proveedor de servicios registra sus servicios globales con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulte [registrar servicios](../../misc/registering-services.md).  
  
-   Después de obtener un servicio, utilice [QueryInterface](/cpp/atl/queryinterface) (código no administrado) o conversión (código administrado) para obtener la interfaz deseada, por ejemplo:  
  
    ```vb#  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```c#  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Código administrado se refiere a un servicio por su tipo, mientras que el código no administrado hace referencia a un servicio por su GUID.  
  
-   Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cargar un paquete VSPackage, pasa un proveedor de servicios para el VSPackage para permitir el acceso de VSPackage a servicios globales. Esto se conoce como "situación" el VSPackage.  
  
-   VSPackages puede ser proveedores de servicios para los objetos que creen. Por ejemplo, un formulario puede enviar una solicitud para un servicio de color para su marco, lo que podría pasar la solicitud a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Los objetos administrados que están profundamente anidados o no se sitúa en absoluto, pueden llamar a <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>para el acceso directo a los servicios globales.</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Para obtener más información, consulte [Cómo: usar GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Vea también  
 [Lista de servicios disponibles](../../extensibility/internals/list-of-available-services.md)   
 [Uso y proporciona servicios](../../extensibility/using-and-providing-services.md)   
 [Casting and Type Conversions](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)  (Conversiones de tipos [Guía de programación de C#])  
 [Conversión](/cpp/cpp/casting)
