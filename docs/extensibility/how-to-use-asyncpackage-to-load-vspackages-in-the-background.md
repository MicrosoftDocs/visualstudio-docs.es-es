---
title: "C&#243;mo: utilizar AsyncPackage para cargar VSPackages en segundo plano | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 8
ms.author: "gregvanl"
caps.handback.revision: 8
---
# C&#243;mo: utilizar AsyncPackage para cargar VSPackages en segundo plano
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cargar e inicializar un VS package pueden dar lugar a E\/S de disco. Si dicha E\/S ocurre en el subproceso de interfaz de usuario, puede provocar problemas de capacidad de respuesta. Para solucionar este problema, Visual Studio 2015 introdujo la <xref:Microsoft.VisualStudio.Shell.AsyncPackage> clase que permite la carga del paquete en un subproceso en segundo plano.  
  
## Crear un AsyncPackage  
 Puede empezar por crear un proyecto VSIX \(**archivo \/ nuevo \/ proyecto \/ Visual C\# \/ extensibilidad \/ proyecto VSIX**\) y la adición de un paquete VSPackage al proyecto \(haga clic en el proyecto y **Agregar nuevo elemento \/ C\# elemento\/extensibilidad\/Visual Studio paquete**\). A continuación, puede crear sus servicios y agregar dichos servicios al paquete.  
  
1.  Derivar el paquete desde <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.  
  
2.  Si va a proporcionar servicios cuya consulta puede provocar el paquete de carga:  
  
     Para indicar a Visual Studio que el paquete es seguro para la carga en segundo plano y para participar en este comportamiento, su <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> debe establecer **AllowsBackgroundLoading** propiedad en true en el constructor de atributo.  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Para indicar a Visual Studio que es seguro crear instancias de su servicio en un subproceso en segundo plano, debe establecer el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> propiedad en true en el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> constructor.  
  
    ```c#  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  Si está cargando a través de los contextos de la interfaz de usuario, debe especificar **PackageAutoLoadFlags.BackgroundLoad** para el <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> o el valor \(0 x 2\) en los indicadores se escribe como el valor de entrada de carga automática de su paquete.  
  
    ```c#  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  Si tiene trabajo inicialización asincrónica, debe invalidar <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Quitar el **Initialize\(\)** método proporcionado por la plantilla VSIX. \(El **Initialize\(\)** método **AsyncPackage** está sellado\). Puede utilizar cualquiera de los <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> métodos para agregar servicios asincrónicos al paquete.  
  
     Nota: Para llamar a **base. InitializeAsync\(\)**, puede cambiar el código fuente para:  
  
    ```c#  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  Debe tener cuidado para no hacer RPC \(llamada de procedimiento quitar\) desde el código de inicialización asincrónica \(en **InitializeAsync**\). Estos pueden producirse cuando se llama <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> directa o indirectamente.  Cuando cargas de sincronización son necesarias, el subproceso de interfaz de usuario se bloqueará con <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. El modelo bloqueo predeterminada deshabilita RPC. Esto significa que si intenta utilizar una llamada RPC desde sus tareas asincrónicas, generará un interbloqueo si el subproceso de UI es esperando el paquete de carga. La alternativa general es calcular las referencias de su código en el subproceso de interfaz de usuario si es necesario usar algo como **Generador de tareas puede unir**de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> o algún otro mecanismo que no utiliza una llamada RPC.  No utilice **ThreadHelper.Generic.Invoke** o generalmente bloquear el subproceso de llamada en espera para obtener el subproceso de interfaz de usuario.  
  
     Nota: Debe evitar el uso **GetService** o **QueryService** en su **InitializeAsync** método. Si tiene que usar aquellos, debe cambiar primero al subproceso de interfaz de usuario. La alternativa consiste en utilizar <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> desde la **AsyncPackage** \(convirtiéndolo a <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.\)  
  
 C\#: Cree una AsyncPackage:  
  
```c#  
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
  
## Convertir un VSPackage existente en AsyncPackage  
 La mayoría del trabajo es lo mismo que crear una nueva **AsyncPackage**. Debe seguir los pasos del 1 al 5 anteriores. También debe tomar las precauciones adicionales en lo siguiente:  
  
1.  No olvide quitar la **inicializar** invalidación que tenía en el paquete.  
  
2.  Evitar los interbloqueos: podría haber oculto de RPC en el código que se producen ahora en un subproceso en segundo plano. Debe asegurarse de que si va a realizar una llamada RPC \(por ejemplo, **GetService**\), necesario para cambiar al subproceso principal \(1\) o \(2\) use la versión asincrónica de la API, si existe \(por ejemplo, **GetServiceAsync**\).  
  
3.  No se puede cambiar entre los subprocesos con demasiada frecuencia. Intenta localizar el trabajo que puede ocurrir en un subproceso en segundo plano. Esto reduce el tiempo de carga.  
  
## Consultar los servicios de AsyncPackage  
 Un **AsyncPackage** puede o no puede cargar de forma asincrónica según el llamador. Por ejemplo,  
  
-   Si el llamador llama **GetService** o **QueryService** \(ambas API sincrónico\) o  
  
-   Si el llamador llama **IVsShell::LoadPackage** \(o **IVsShell5::LoadPackageWithContext**\) o  
  
-   La carga se desencadena por un contexto de interfaz de usuario, pero no especifica que el mecanismo de contexto de la interfaz de usuario puede cargar asincrónicamente  
  
 a continuación, el paquete se cargará sincrónicamente.  
  
 Tenga en cuenta que el paquete todavía tiene una oportunidad \(en la fase de inicialización asincrónica\) para que funcione el subproceso de interfaz de usuario, aunque se bloqueará el subproceso de interfaz de usuario para la finalización de ese trabajo. Si el llamador usa **IAsyncServiceProvider** asincrónicamente la consulta para el servicio, a continuación, la carga e inicialización hará asincrónicamente suponiendo que no bloqueen inmediatamente en el objeto de tarea resultante.  
  
 C\#: Cómo consultar el servicio de forma asincrónica:  
  
```c#  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```