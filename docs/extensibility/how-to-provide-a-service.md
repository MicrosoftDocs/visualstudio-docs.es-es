---
title: 'Cómo: proporcionar un servicio | Microsoft Docs'
description: Un VSPackage puede proporcionar servicios que otros VSPackages pueden utilizar. Obtenga información sobre cómo un VSPackage registra un servicio con Visual Studio y agrega el servicio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac89984539b0870d3921918a5a96b821297c009f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993736"
---
# <a name="how-to-provide-a-service"></a>Cómo: proporcionar un servicio
Un VSPackage puede proporcionar servicios que otros VSPackages pueden utilizar. Para proporcionar un servicio, un VSPackage debe registrar el servicio con Visual Studio y agregar el servicio.

 La <xref:Microsoft.VisualStudio.Shell.Package> clase implementa <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> y <xref:System.ComponentModel.Design.IServiceContainer> . <xref:System.ComponentModel.Design.IServiceContainer> contiene métodos de devolución de llamada que proporcionan servicios a petición.

 Para obtener más información acerca de los servicios, consulte [Service Essentials](../extensibility/internals/service-essentials.md) .

> [!NOTE]
> Cuando un VSPackage está a punto de descargarse, Visual Studio espera hasta que se hayan entregado todas las solicitudes de servicios que proporciona un VSPackage. No permite nuevas solicitudes para estos servicios. No debe llamar explícitamente al <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> método para revocar un servicio durante la descarga.

## <a name="implement-a-service"></a>Implementar un servicio

1. Cree un proyecto de VSIX (**archivo**  >  **nuevo**  >  **proyecto**  >  **Visual C#**  >  **extensibilidad**  >  **VSIX Project**).

2. Agregue un VSPackage al proyecto. Seleccione el nodo del proyecto en el **Explorador de soluciones** y haga clic en **Agregar**  >  **nuevo elemento**  >  **Visual C# elementos** de  >  **extensibilidad**  >  **Visual Studio Package**.

3. Para implementar un servicio, debe crear tres tipos:

   - Una interfaz que describe el servicio. Muchas de estas interfaces están vacías, es decir, no tienen ningún método.

   - Una interfaz que describe la interfaz de servicio. Esta interfaz incluye los métodos que se van a implementar.

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

1. Para registrar un servicio, agregue el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> al VSPackage que proporciona el servicio. Este es un ejemplo:

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     Este atributo se registra `SMyService` con Visual Studio.

    > [!NOTE]
    > Para registrar un servicio que reemplaza a otro servicio con el mismo nombre, use <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> . Tenga en cuenta que solo se permite una invalidación de un servicio.

### <a name="add-a-service"></a>Agregar un servicio

1. En el inicializador de VSPackage, agregue el servicio y agregue un método de devolución de llamada para crear los servicios. Este es el cambio que se realizará en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método:

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

3. Ahora puede obtener el servicio y usar sus métodos. En el ejemplo siguiente se muestra el uso del servicio en el inicializador, pero puede obtener el servicio en cualquier lugar en el que desee usar el servicio.

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

     El valor de `helloString` debe ser "Hello".

## <a name="see-also"></a>Consulte también
- [Cómo: obtener un servicio](../extensibility/how-to-get-a-service.md)
- [Usar y proporcionar servicios](../extensibility/using-and-providing-services.md)
- [Aspectos básicos del servicio](../extensibility/internals/service-essentials.md)
