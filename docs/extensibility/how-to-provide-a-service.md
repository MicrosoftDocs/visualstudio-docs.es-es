---
title: "Cómo: proporcionar un servicio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3c37f4dc215027752da9c16fbdfba44b4e10c41c
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
# <a name="how-to-provide-a-service"></a>Cómo: proporcionar un servicio
Un VSPackage puede proporcionar servicios que pueden usar otros VSPackages. Para proporcionar un servicio, un VSPackage debe registrar el servicio con Visual Studio y agregue el servicio.  
  
 El <xref:Microsoft.VisualStudio.Shell.Package> clase implementa tanto <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> y <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer>contiene métodos de devolución de llamada que proporcionan servicios a petición.  
  
 Para obtener más información acerca de los servicios, vea [servicio Essentials](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Cuando un paquete VSPackage está a punto de descargarse, Visual Studio espera hasta que todas las solicitudes para los servicios que proporciona un paquete VSPackage se han entregado. No permiten nuevas solicitudes de estos servicios. No debería llamar explícitamente el <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> método revocar un servicio cuando se descarga.  
  
#### <a name="implementing-a-service"></a>Implementar un servicio  
  
1.  Cree un proyecto VSIX (**archivo > Nuevo > proyecto > Visual C# > Extensiblity > proyecto VSIX**).  
  
2.  Agregar un paquete VSPackage al proyecto. Seleccione el nodo de proyecto en el **el Explorador de soluciones** y haga clic en **Agregar > nuevo elemento > elementos de Visual C# > extensibilidad > paquete de Visual Studio**.  
  
3.  Para implementar un servicio, debe crear tres tipos:  
  
    -   Interfaz que describe el servicio. Muchas de estas interfaces están vacíos, es decir, no tienen ningún método.  
  
    -   Interfaz que describe la interfaz de servicio. Esta interfaz incluye los métodos para que se implementen.  
  
    -   Una clase que implementa el servicio y la interfaz de servicio.  
  
     En el ejemplo siguiente se muestra una implementación muy básica de los tres tipos. El constructor de la clase de servicio debe establecer el proveedor de servicios.  
  
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
  
1.  Para registrar un servicio, agregue el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> para el VSPackage que proporciona el servicio. A continuación se muestra un ejemplo:  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Este atributo registra `SMyService` con Visual Studio.  
  
    > [!NOTE]
    >  Para registrar un servicio que reemplaza otro servicio con el mismo nombre, utilice el <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Tenga en cuenta que solo la invalidación de un servicio se permite.  
  
### <a name="adding-a-service"></a>Agregar un servicio  
  
1.  En el inicializador de VSPackage, agregue el servicio y agregue un método de devolución de llamada para crear los servicios. Este es el cambio que realice en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Implemente el método de devolución de llamada, que debe crear y devolver el servicio o null si no se puede crear.  
  
    ```csharp  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio puede rechazar una solicitud para proporcionar un servicio. Lo hace si otro VSPackage ya proporciona el servicio.  
  
3.  Ahora puede hacer que el servicio y utilizar sus métodos. Le mostraremos en el inicializador, pero puede obtener el servicio en cualquier lugar que desea usar el servicio.  
  
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
 [Uso y proporciona servicios](../extensibility/using-and-providing-services.md)   
 [Conceptos básicos del servicio](../extensibility/internals/service-essentials.md)
