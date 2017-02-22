---
title: "Fundamentos del servicio | Microsoft Docs"
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
  - "Servicios de essentials"
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Fundamentos del servicio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un servicio es un contrato entre dos VSPackages. Un VSPackage proporciona un conjunto específico de interfaces para otro VSPackage consumir.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es una colección de VSPackages que proporciona servicios a otros VSPackages.  
  
 Por ejemplo, puede utilizar el servicio SVsActivityLog para obtener una interfaz IVsActivityLog, que puede utilizar para escribir en el registro de actividad. Para obtener más información, consulta [Cómo: utilizar el registro de actividad](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] También proporciona algunos servicios integrados que no están registrados. VSPackages puede reemplazar integrados u otros servicios proporcionando una invalidación de servicio. Se permite reemplazar un único servicio para cualquier servicio.  
  
 Los servicios no tienen ningún detectabilidad. Por lo tanto, debe conocer el identificador de servicio \(SID\) de un servicio que desea utilizar, y debe saber qué interfaces proporciona. La documentación de referencia para el servicio proporciona esta información.  
  
-   VSPackages que proporcionan servicios se denominan proveedores de servicios.  
  
-   Servicios que se proporcionan a otros VSPackages se denominan servicios globales.  
  
-   Servicios que solo están disponibles para el paquete VSPackage que implementa o a cualquier objeto que se crea, se denominan servicios locales.  
  
-   Servicios que reemplazan servicios integrados o servicios proporcionados por otros paquetes se denominan invalidaciones de servicio.  
  
-   Servicios o las invalidaciones de servicio, se cargan a petición, es decir, el proveedor de servicios se carga cuando se solicita el servicio que proporciona por otro VSPackage.  
  
-   Para admitir la carga a petición, un proveedor de servicios registra sus servicios globales con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulta [Registrar servicios](../../misc/registering-services.md).  
  
-   Después de obtener un servicio, utilice [QueryInterface](/visual-cpp/atl/queryinterface) \(código no administrado\) o conversión \(código administrado\) para obtener la interfaz deseada, por ejemplo:  
  
    ```vb#  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```c#  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Código administrado hace referencia a un servicio por su tipo, mientras que el código no administrado hace referencia a un servicio por su GUID.  
  
-   Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cargar un paquete VSPackage, pasa un proveedor de servicios para el VSPackage para permitir el acceso de VSPackage a servicios globales. Esto se conoce como "situación" VSPackage.  
  
-   VSPackages puede ser proveedores de servicios para los objetos que creen. Por ejemplo, un formulario puede enviar una solicitud para un servicio de color con el marco, que puede pasar la solicitud a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Los objetos administrados que están profundamente anidados o no está ubicados en absoluto, pueden llamar a <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> para el acceso directo a los servicios globales. Para obtener más información, consulta [Cómo: Usar GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## Vea también  
 [Lista de servicios disponibles](../../extensibility/internals/list-of-available-services.md)   
 [Utilizar y proporcionar servicios](../../extensibility/using-and-providing-services.md)   
 [Conversiones de tipos](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [Convertir](/visual-cpp/cpp/casting)