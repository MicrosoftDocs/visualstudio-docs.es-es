---
title: "Cómo: utilizar AsyncPackage para cargar VSPackages en segundo plano | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.technology: vs-ide-sdk
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
ms.workload:
- vssdk
ms.openlocfilehash: 18c420381e9fa0451bee846ea5fb9de5c74ddbf8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Cómo: utilizar AsyncPackage para cargar VSPackages en segundo plano
Cargar e inicializar un paquete de VS pueden dar lugar a E/S de disco. Si este tipo E/S ocurre en el subproceso de interfaz de usuario, puede provocar problemas de capacidad de respuesta. Para solucionar este problema, Visual Studio 2015 introdujo la <xref:Microsoft.VisualStudio.Shell.AsyncPackage> clase que permite la carga del paquete en un subproceso en segundo plano.  
  
## <a name="creating-an-asyncpackage"></a>Crear un AsyncPackage  
 Puede empezar a crear un proyecto VSIX (**archivo > Nuevo > proyecto > Visual C# > extensibilidad > proyecto VSIX**) y la adición de un paquete VSPackage al proyecto (haga clic con el botón secundario en el proyecto y **Agregar/nuevo elemento / elemento de C# / Paquete de Extensibility/Visual Studio**). A continuación, puede crear sus servicios y agregar esos servicios al paquete.  
  
1.  Derivar el paquete desde <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.  
  
2.  Si va a proporcionar servicios cuya consulta puede provocar el paquete de carga:  
  
     Para indicar a Visual Studio que el paquete es seguro para la carga en segundo plano y no formen parte de este comportamiento, el <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> debe establecer **AllowsBackgroundLoading** propiedad en true en el constructor de atributo.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Para indicar a Visual Studio que es seguro crear una instancia del servicio en un subproceso en segundo plano, debe establecer el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> propiedad en true en el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> constructor.  
  
    ```csharp  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  Si va a cargar a través de contextos de la interfaz de usuario, debe especificar **PackageAutoLoadFlags.BackgroundLoad** para el <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> o el valor (0 x 2) en los indicadores se escribe como el valor de entrada de carga automática de su paquete.  
  
    ```csharp  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  Si tiene trabajo inicialización asincrónica, se debe invalidar <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Quitar el **Initialize()** método proporcionada la plantilla VSIX. (El **Initialize()** método **AsyncPackage** está sellado). Puede usar cualquiera de los <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> métodos para agregar servicios asincrónicos al paquete.  
  
     Nota: Para llamar a **base. InitializeAsync()**, puede cambiar el código fuente para:  
  
    ```csharp  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  Debe tener cuidado para no hacer RPC (llamada a procedimiento remoto) desde el código de inicialización asincrónica (en **InitializeAsync**). Estos pueden producirse cuando se llama a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> directa o indirectamente.  Cuando se requieren las cargas de sincronización, el subproceso de interfaz de usuario se bloqueará con <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. El modelo bloqueo predeterminado deshabilita RPC. Esto significa que si intenta usar una llamada RPC de sus tareas asincrónicas, interbloquee si el subproceso de interfaz de usuario es esperando el paquete que desea cargar. La alternativa general es calcular las referencias de código para el subproceso de interfaz de usuario si es necesario usar algo parecido a **generador de tareas que se puede unir**del <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> o algún otro mecanismo que no usa una RPC.  No utilice **ThreadHelper.Generic.Invoke** o generalmente bloquear el subproceso que realiza la llamada espera obtener al subproceso de interfaz de usuario.  
  
     Nota: Debe evitar el uso **GetService** o **QueryService** en su **InitializeAsync** método. Si tiene que utilizarlos, debe cambiar al subproceso de interfaz de usuario en primer lugar. La alternativa es usar <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> desde su **AsyncPackage** (convirtiéndolo a <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)  
  
 C#: Cree una AsyncPackage:  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]       
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]   
public sealed class TestPackage : AsyncPackage   
{   
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)   
    {               
        this.AddService(typeof(SMyTestService), CreateService, true);   
        return Task.FromResult<object>(null);   
    }   
}  
```  
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Convertir un VSPackage existente en AsyncPackage  
 La mayoría del trabajo es lo mismo que crear un nuevo **AsyncPackage**. Debe seguir los pasos del 1 al 5 anterior. También debe tomar las precauciones adicionales en lo siguiente:  
  
1.  No olvide quitar la **inicializar** invalidación que tenía en el paquete.  
  
2.  Evitar los interbloqueos: pueden producirse errores ocultos RPC en el código que realizará ahora de un subproceso en segundo plano. Debe asegurarse de que si va a realizar una llamada RPC (p. ej. **GetService**), es necesario (1) cambia para el subproceso principal o (2) use la versión asincrónica de la API si existe (por ejemplo, **GetServiceAsync**).  
  
3.  No cambie entre los subprocesos con demasiada frecuencia. Intenta localizar el trabajo que puede suceder en un subproceso en segundo plano. Esto reduce el tiempo de carga.  
  
## <a name="querying-services-from-asyncpackage"></a>Enviando consulta a servicios de AsyncPackage  
 Un **AsyncPackage** puede o no puede cargar de forma asincrónica según el llamador. Por ejemplo,  
  
-   Si el llamador llama **GetService** o **QueryService** (ambas API sincrónico) o  
  
-   Si el llamador llama **IVsShell::LoadPackage** (o **IVsShell5::LoadPackageWithContext**) o  
  
-   La carga se desencadena en un contexto de la interfaz de usuario, pero no especificó que el mecanismo de contexto de la interfaz de usuario puede cargar asincrónicamente  
  
 a continuación, el paquete se cargará sincrónicamente.  
  
 Tenga en cuenta que el paquete todavía tiene una oportunidad (en su fase de inicialización asincrónica) para que funcione el subproceso de interfaz de usuario, aunque se bloqueará el subproceso de interfaz de usuario para la finalización de ese trabajo. Si el llamador usa **IAsyncServiceProvider** asincrónicamente la consulta para el servicio, a continuación, la carga e inicialización hará asincrónicamente suponiendo que no bloqueen inmediatamente en el objeto de tarea resultante.  
  
 C#: Cómo consultar el servicio de forma asincrónica:  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```
  
