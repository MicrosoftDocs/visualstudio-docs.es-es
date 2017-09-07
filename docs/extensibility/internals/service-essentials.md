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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 0b78b5f9bf1fb6d9c92657b99e6d21b58cab2728
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

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
  
-   Para admitir la carga a petición, un proveedor de servicios registra sus servicios globales con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulte [Cómo: proporcionar un servicio](../../extensibility/how-to-provide-a-service.md).  
  
-   Después de obtener un servicio, utilice [QueryInterface](/cpp/atl/queryinterface) (código no administrado) o conversión (código administrado) para obtener la interfaz deseada, por ejemplo:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    ```  
  
-   Código administrado se refiere a un servicio por su tipo, mientras que el código no administrado hace referencia a un servicio por su GUID.  
  
-   Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cargar un paquete VSPackage, pasa un proveedor de servicios para el VSPackage para permitir el acceso de VSPackage a servicios globales. Esto se conoce como "situación" el VSPackage.  
  
-   VSPackages puede ser proveedores de servicios para los objetos que creen. Por ejemplo, un formulario puede enviar una solicitud para un servicio de color para su marco, lo que podría pasar la solicitud a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Los objetos administrados que están profundamente anidados o no se sitúa en absoluto, pueden llamar a <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> para el acceso directo a los servicios globales.   
  
<a name="how-to-use-getglobalservice"></a>  
  
## <a name="use-getglobalservice"></a>Usar GetGlobalService  
  
A veces, debe obtener un servicio desde una ventana de herramientas o control contenedor que no se ha ubicado, o bien se ha ubicado en un sitio con un proveedor de servicios que no conozca el servicio que desee. Por ejemplo, puede escribir en el registro de actividad desde dentro de un control. Para obtener más información sobre estos y otros escenarios, consulte [Cómo: solucionar problemas de servicios](../../extensibility/how-to-troubleshoot-services.md).  
  
Puede obtener la mayoría de los servicios de Visual Studio mediante una llamada a estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método.  
  
<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>se basa en un servicio almacenado en caché se basa en un proveedor que se inicializa la primera vez cualquier VSPackage derivado de paquete. Debe garantizar que esta condición se cumple, o, de lo contrario estar preparada para un servicio null.  
  
Afortunadamente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funciona correctamente la mayoría de los casos.  
  
-   Si un paquete VSPackage proporciona un servicio que solo conocido otro VSPackage, sitúa el VSPackage que solicitan el servicio antes de VSPackage proporciona que el servicio está cargado.  
  
-   Si se crea una ventana de herramientas por un paquete VSPackage, sitúa el VSPackage antes de crea la ventana de herramientas.  
  
-   Si un contenedor de control está hospedado en una ventana de herramienta creada por un paquete VSPackage, sitúa el VSPackage antes de crea el contenedor del control.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Para obtener un servicio desde dentro de un contenedor de control o la ventana de herramienta  
  
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
    
    Este código obtiene un servicio SVsActivityLog y lo convierte a una interfaz IVsActivityLog, que se puede usar para escribir en el registro de actividad. Para obtener un ejemplo, vea [Cómo: usar el registro de actividad](../../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Vea también  
 [Lista de servicios disponibles](../../extensibility/internals/list-of-available-services.md)   
 [Uso y proporciona servicios](../../extensibility/using-and-providing-services.md)   
 [Casting and Type Conversions](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)  (Conversiones de tipos [Guía de programación de C#])  
 [Conversión](/cpp/cpp/casting)
