---
title: "C&#243;mo: proporcionar un servicio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servicios, que ofrece"
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# C&#243;mo: proporcionar un servicio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un VSPackage puede proporcionar servicios que pueden usar otros VSPackages. Para proporcionar un servicio, un VSPackage debe registrar el servicio con Visual Studio y agregue el servicio.  
  
 La <xref:Microsoft.VisualStudio.Shell.Package> clase implementa los <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> y <xref:System.ComponentModel.Design.IServiceContainer>.<xref:System.ComponentModel.Design.IServiceContainer> contiene métodos de devolución de llamada que proporcionan servicios a petición.  
  
 Para obtener más información acerca de los servicios, consulte [Fundamentos del servicio](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Cuando un paquete VSPackage está a punto de descargarse, Visual Studio espera hasta que todas las solicitudes de servicios que proporciona un paquete VSPackage que se han entregado. No permite nuevas solicitudes de estos servicios. No debería llamar explícitamente el <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> método revocar un servicio de descarga.  
  
#### Implementación de un servicio  
  
1.  Cree un proyecto VSIX \(**archivo \/ nuevo \/ proyecto \/ Visual C\# \/ Extensiblity \/ proyecto VSIX**\).  
  
2.  Agregar un paquete VSPackage al proyecto. Seleccione el nodo de proyecto en el **el Explorador de soluciones** y haga clic en **Agregar \/ nuevo elemento o elementos de Visual C\# \/ extensibilidad \/ paquete de Visual Studio**.  
  
3.  Para implementar un servicio, debe crear tres tipos:  
  
    -   Interfaz que describe el servicio. Muchas de estas interfaces están vacíos, es decir, no tienen ningún método.  
  
    -   Interfaz que describe la interfaz de servicio. Esta interfaz incluye los métodos para implementarse.  
  
    -   Una clase que implementa el servicio y la interfaz de servicio.  
  
     En el ejemplo siguiente se muestra una implementación muy básica de los tres tipos. El constructor de la clase de servicio debe establecer el proveedor de servicios.  
  
    ```c#  
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
  
### Registrar un servicio  
  
1.  Para registrar un servicio, agregue el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> a VSPackage que proporciona el servicio. Este es un ejemplo:  
  
    ```c#  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Este atributo se registra `SMyService` con Visual Studio.  
  
    > [!NOTE]
    >  Para registrar un servicio que reemplaza otro servicio con el mismo nombre, use la <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Tenga en cuenta que la invalidación de un servicio solo se permite.  
  
### Agregar un servicio  
  
1.  1.	En el inicializador de VSPackage, agregue el servicio y agregar un método de devolución de llamada para crear los servicios. Este es el cambio a la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método:  
  
    ```c#  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Implemente el método de devolución de llamada, que se debe crear y devolver el servicio o null si no se puede crear.  
  
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
  
3.  Ahora puede obtener el servicio y utilizar sus métodos. Le mostraremos en el inicializador, pero puede obtener el servicio en cualquier lugar que desea utilizar el servicio.  
  
    ```c#  
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
  
     El valor de `helloString` debe ser "Hello".  
  
## Vea también  
 [Cómo: obtener un servicio](../extensibility/how-to-get-a-service.md)   
 [Utilizar y proporcionar servicios](../extensibility/using-and-providing-services.md)   
 [Fundamentos del servicio](../extensibility/internals/service-essentials.md)