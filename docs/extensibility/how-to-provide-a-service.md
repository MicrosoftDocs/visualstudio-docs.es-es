---
title: 'Cómo: Proporcionar un Servicio ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60cae5e8048a0234114e1f9e7d97728e26ee40f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710770"
---
# <a name="how-to-provide-a-service"></a>Cómo: Proporcionar un servicio
Un VSPackage puede proporcionar servicios que otros VSPackages pueden usar. Para proporcionar un servicio, un VSPackage debe registrar el servicio con Visual Studio y agregar el servicio.

 La <xref:Microsoft.VisualStudio.Shell.Package> clase implementa <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:System.ComponentModel.Design.IServiceContainer>tanto y . <xref:System.ComponentModel.Design.IServiceContainer>contiene métodos de devolución de llamada que proporcionan servicios a petición.

 Para obtener más información acerca de los servicios, consulte [Elementos esenciales](../extensibility/internals/service-essentials.md) del servicio .

> [!NOTE]
> Cuando un VSPackage está a punto de descargarse, Visual Studio espera hasta que se hayan entregado todas las solicitudes de servicios que proporciona un VSPackage. No permite nuevas solicitudes para estos servicios. No debe llamar explícitamente al <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> método para revocar un servicio al descargar.

## <a name="implement-a-service"></a>Implementar un servicio

1. Crear un proyecto VSIX (**Archivo** > **Nuevo** > **proyecto** > **Proyecto** > de**extensibilidad** > **VSIX Project**).

2. Agregue un VSPackage al proyecto. Seleccione el nodo del proyecto en el **Explorador** de soluciones y haga clic en **Agregar** > **nuevo elemento** > Paquete de**extensibilidad** > de**elementos** > de**Visual Studio**.

3. Para implementar un servicio, debe crear tres tipos:

   - Interfaz que describe el servicio. Muchas de estas interfaces están vacías, es decir, no tienen métodos.

   - Interfaz que describe la interfaz de servicio. Esta interfaz incluye los métodos que se van a implementar.

   - Una clase que implementa el servicio y la interfaz de servicio.

     En el ejemplo siguiente se muestra una implementación básica de los tres tipos. El constructor de la clase de servicio debe establecer el proveedor de servicios.

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

### <a name="register-a-service"></a>Registrar un servicio

1. Para registrar un servicio, agregue el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> VSPackage que proporciona el servicio. Este es un ejemplo:

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     Este atributo `SMyService` se registra con Visual Studio.

    > [!NOTE]
    > Para registrar un servicio que reemplaza otro servicio <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>con el mismo nombre, utilice el archivo . Tenga en cuenta que solo se permite una invalidación de un servicio.

### <a name="add-a-service"></a>Agregar un servicio

1. En el inicializador de VSPackage, agregue el servicio y agregue un método de devolución de llamada para crear los servicios. Aquí está el cambio <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> a realizar en el método:

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. Implemente el método de devolución de llamada, que debe crear y devolver el servicio, o null si no se puede crear.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Visual Studio puede rechazar una solicitud para proporcionar un servicio. Lo hace si otro VSPackage ya proporciona el servicio.

3. Ahora puede obtener el servicio y utilizar sus métodos. En el ejemplo siguiente se muestra el uso del servicio en el inicializador, pero puede obtener el servicio en cualquier lugar donde desee usar el servicio.

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);

        MyService myService = (MyService) this.GetService(typeof(SMyService));
        myService.Hello();
        string helloString = myService.Goodbye();

        base.Initialize();
    }
    ```

     El valor `helloString` de debe ser "Hola".

## <a name="see-also"></a>Vea también
- [Cómo: Obtener un servicio](../extensibility/how-to-get-a-service.md)
- [Usar y proporcionar servicios](../extensibility/using-and-providing-services.md)
- [Elementos esenciales del servicio](../extensibility/internals/service-essentials.md)
