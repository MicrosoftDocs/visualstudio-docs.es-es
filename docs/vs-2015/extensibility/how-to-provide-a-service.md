---
title: 'Cómo: proporcionar un servicio | Microsoft Docs'
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
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0b9dc7d2ef8aabab628f13ce9648e0fa5dc1f3b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845100"
---
# <a name="how-to-provide-a-service"></a>Cómo: proporcionar un servicio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un VSPackage puede proporcionar servicios que pueden usar otros VSPackages. Para proporcionar un servicio, un VSPackage debe registrar el servicio con Visual Studio y agregue el servicio.  
  
 El <xref:Microsoft.VisualStudio.Shell.Package> clase implementa tanto <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> y <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer> contiene métodos de devolución de llamada que proporcionan servicios a petición.  
  
 Para obtener más información acerca de los servicios, consulte [información esencial del servicio](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Cuando un paquete VSPackage está a punto de descargarse, Visual Studio espera hasta que se han entregado todas las solicitudes de servicios que proporciona un paquete VSPackage. No permite las nuevas solicitudes para estos servicios. No se debe llamar explícitamente la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> método revocar un servicio cuando se descarga.  
  
#### <a name="implementing-a-service"></a>Implementación de un servicio  
  
1. Cree un proyecto VSIX (**archivo / nuevo / proyecto / Visual C# / usaría / proyecto VSIX**).  
  
2. Agregar un paquete VSPackage al proyecto. Seleccione el nodo del proyecto en el **el Explorador de soluciones** y haga clic en **Agregar / nuevo elemento o elementos de Visual C# / extensibilidad / paquete de Visual Studio**.  
  
3. Para implementar un servicio, deberá crear tres tipos:  
  
   - Interfaz que describe el servicio. Muchas de estas interfaces están vacíos, es decir, no tienen ningún método.  
  
   - Interfaz que describe la interfaz de servicio. Esta interfaz incluye los métodos para implementarse.  
  
   - Una clase que implementa el servicio y la interfaz de servicio.  
  
     El ejemplo siguiente muestra una implementación muy básica de los tres tipos. El constructor de la clase de servicio debe establecer el proveedor de servicios.  
  
   ```csharp  
   public class MyService : SMyService, IMyService  
   {  
       private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;  
       private string myString;  
       public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)  
       {  
           Trace.WriteLine(  
                  "Constructing a new instance of MyService");  
           serviceProvider = sp;  
       }  
       public void Hello()  
       {  
           myString = "hello";  
       }  
       public string Goodbye()  
       {  
          return "goodbye";  
       }  
   }  
   public interface SMyService  
   {  
   }  
   public interface IMyService  
   {  
       void Hello();  
       string Goodbye();  
   }  
  
   ```  
  
### <a name="registering-a-service"></a>Registrar un servicio  
  
1.  Para registrar un servicio, agregue el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> al VSPackage que proporciona el servicio. A continuación, se muestra un ejemplo:  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Este atributo registra `SMyService` con Visual Studio.  
  
    > [!NOTE]
    >  Para registrar un servicio que reemplace otro con el mismo nombre, use la <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Tenga en cuenta que la invalidación de un servicio solo se permite.  
  
### <a name="adding-a-service"></a>Agregar un servicio  
  
1.  1.  En el inicializador de VSPackage, agregue el servicio y agregue un método de devolución de llamada para crear los servicios. Este es el cambio a la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Implemente el método de devolución de llamada, que debe crear y devolver el servicio o null si no se pueden crear.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio puede rechazar una solicitud para proporcionar un servicio. Esto produce si otro VSPackage ya proporciona el servicio.  
  
3.  Ahora puede obtener el servicio y usar sus métodos. Le mostraremos en el inicializador, pero puede obtener el servicio en cualquier lugar que desea usar el servicio.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.myString;  
  
        base.Initialize();  
    }  
    ```  
  
     El valor de `helloString` debe ser "Hola".  
  
## <a name="see-also"></a>Vea también  
 [Cómo: obtener un servicio](../extensibility/how-to-get-a-service.md)   
 [Uso y provisión de servicios](../extensibility/using-and-providing-services.md)   
 [Conceptos básicos del servicio](../extensibility/internals/service-essentials.md)

