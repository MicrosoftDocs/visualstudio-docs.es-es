---
title: "Agregar una extensión de protocolo del servidor idioma | Documentos de Microsoft"
ms.custom: 
ms.date: 11/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e38c040e732571e3343c30d84745d2602a1088d
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2017
---
# <a name="adding-a-language-server-protocol-extension"></a>Agregar una extensión del protocolo de servidor de idioma

El protocolo de servidor de idioma (LSP) es un protocolo común, en forma de JSON RPC v2.0, usar para proporcionar características de servicio para varios editores de código de idioma. Mediante el protocolo, los programadores pueden escribir un único servidor de idioma para proporcionar características como IntelliSense, diagnósticos de errores del servicio de lenguaje, buscar todas las referencias, etcetera para varios editores de código que admiten el LSP. Tradicionalmente, se pueden agregar servicios de lenguaje en Visual Studio, ya sea mediante archivos de gramática TextMate para proporcionar funcionalidades básicas como resaltado de sintaxis, o al escribir servicios de lenguaje personalizado mediante el conjunto completo de API de extensibilidad de Visual Studio para proporcionar más datos. Ahora, la compatibilidad con el LSP ofrece una tercera opción.

![servicio de protocolo de servidor de lenguaje en Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protocolo de servidor de idioma

Para obtener más información sobre el propio protocolo, consulte la documentación [aquí](https://github.com/Microsoft/language-server-protocol). Implementación de Visual Studio de protocolo de idioma del servidor está en vista previa y soporte técnico debe considerarse experimental. La versión de vista previa está en forma de una extensión ([vista previa del cliente de protocolo de lenguaje Server](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)), **, pero esta extensión solo puede instalarse en el canal de vista previa de Visual Studio**. Una versión posterior de Visual Studio incluye compatibilidad integrada para el protocolo de servidor de lenguaje, momento en el que se van a quitar la marca de versión preliminar. **No se debe usar la vista previa para fines de producción.**

Para obtener más información sobre cómo crear un servidor de idioma de ejemplo o cómo integrar un servidor existente de idioma en el código de Visual Studio, consulte la documentación de [aquí](https://code.visualstudio.com/docs/extensions/example-language-server).

![implementación del protocolo de servidor de lenguaje](media/lsp-implementation.png)

Este artículo describe cómo crear una extensión de Visual Studio que usa un servidor de lenguaje basado en LSP. Se supone que ya se ha desarrollado un servidor de lenguaje basado en LSP y simplemente desea integrar en Visual Studio.

Para la compatibilidad con Visual Studio, los servidores de idioma pueden comunicarse con el cliente (Visual Studio) a través de los siguientes mecanismos:

* Flujos de entrada/salida estándar
* Canalizaciones con nombre
* sockets

El propósito de los LSP y soporte técnico para él en Visual Studio es a los servicios de lenguaje integrado que no forman parte del producto de Visual Studio. No está pensado para ampliar los servicios existentes de idioma (por ejemplo, C#) en Visual Studio. Para ampliar los lenguajes existentes, consulte la Guía de extensibilidad del servicio de lenguaje (por ejemplo, el ["Roslyn".NET Compiler Platform](https://docs.microsoft.com/visualstudio/extensibility/dotnet-compiler-platform-roslyn-extensibility)).

## <a name="language-server-protocol-features-supported"></a>Características de protocolo del servidor de idioma admitidas

Las siguientes características LSP hasta ahora se admiten en Visual Studio:

Mensaje | Tiene compatibilidad en Visual Studio
--- | ---
inicializar | sí
inicializado | 
cierre | sí
Salir | sí
$/ cancelRequest | sí
ventana/showMessage | sí
ventana/showMessageRequest | sí
ventana/logMessage | sí
evento de telemetría / |
cliente/registerCapability |
cliente/unregisterCapability |
área de trabajo/didChangeConfiguration | sí
área de trabajo/didChangeWatchedFiles | sí
área de trabajo/símbolos | sí
área de trabajo/executeCommand |
área de trabajo/applyEdit |
textDocument/publishDiagnostics | sí
textDocument/didOpen | sí
textDocument/didChange | sí
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave |
textDocument/didClose | sí
textDocument/finalización | sí
finalización/resolve | sí
textDocument/mantener el mouse |
textDocument/signatureHelp |
textDocument/referencias | sí
textDocument/documentHighlight |
textDocument/documentSymbol | sí
aplicar formato a textDocument / | sí
textDocument/rangeFormatting | sí
textDocument/onTypeFormatting |
textDocument/definición | sí
textDocument/codeAction |
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/rename |

## <a name="getting-started"></a>Introducción

### <a name="create-a-vsix-project"></a>Cree un proyecto VSIX

Para crear una extensión de servicio de lenguaje mediante un servidor de lenguaje basado en LSP, primero asegúrese de que tiene la **desarrollo de extensión de Visual Studio** instalado para la instancia de VS de carga de trabajo.

A continuación, cree un nuevo VSIXProject en blanco, desplácese hasta **archivo** > **nuevo proyecto** > **Visual C#**  >   **Extensibilidad** > **proyecto VSIX**:

![Crear proyecto de vsix](media/lsp-vsix-project.png)

Para la versión preliminar, compatibilidad con VS el LSP estará en la forma de una extensión VSIX ([Microsoft.VisualStudio.LanguageServer.Client.Preview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)). Los desarrolladores de extensión que desean crear una extensión mediante servidores de lenguaje LSP deben tomar una dependencia en este VSIX. Esto significa que para los clientes que deseen instalar una extensión de servidor del lenguaje **en primer lugar debe instalar VSIX de vista previa de lenguaje servidor Protocolo cliente.**

Para definir la dependencia VSIX, abra el Diseñador de manifiestos VSIX para su VSIX (haciendo doble clic en el archivo source.extension.vsixmanifest del proyecto) y navegue hasta **dependencias**:

![Agregar referencia al cliente de protocolo de servidor de idioma](media/lsp-reference-lsp-dependency.png)

Crea una nueva dependencia similar al siguiente:

![definir la dependencia de cliente de protocolo de servidor de idioma](media/lsp-define-lsp-dependency.png)

* **Origen**: definir manualmente
* **Nombre**: vista previa del cliente de protocolo de lenguaje Server
* **Identificador**: Microsoft.VisualStudio.LanguageServer.Client.Preview
* **Intervalo de versiones**: [1.0,2.0)
* **Forma dependencia resuelve**: instalado por el usuario
* **Dirección URL de descarga**: [https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)

>**Tenga en cuenta**: el **URL descargar** siempre debe rellenarse para instalar la extensión de los usuarios sepan cómo instalar la dependencia necesaria.

### <a name="language-server-and-runtime-installation"></a>Instalación del servidor y en tiempo de ejecución de idioma

De forma predeterminada, las extensiones que se crea para admitir servidores de lenguaje basado en LSP en Visual Studio no contendrá los propios servidores de lenguaje o los tiempos de ejecución necesarios para ejecutarlas. Los desarrolladores de extensiones están responsables de distribuir los servidores de idioma y los tiempos de ejecución que sea necesitado. Hay varias maneras de hacerlo:

* Servidores de lenguaje se pueden incrustar en la extensión VSIX como archivos de contenido.
* Crear un archivo MSI para instalar el servidor de idioma o necesita tiempos de ejecución.
* Se proporcionan instrucciones sobre informarles de Marketplace cómo obtener tiempos de ejecución y el idioma de servidores.

### <a name="textmate-grammar-files"></a>Archivos de gramática TextMate

El LSP no incluyen la especificación de cómo proporcionar coloración de texto de idiomas. Para proporcionar colores personalizados para los lenguajes de Visual Studio, los desarrolladores de extensiones pueden usar un archivo de gramática TextMate. Para agregar archivos personalizados de tema o gramática TextMate, siga estos pasos:

1. Cree una carpeta denominada "Gramáticas" dentro de la extensión (o puede ser cualquier nombre que elija).

2. Dentro de la carpeta "Gramáticas", incluyen los archivos de *.tmlanguage o *.tmtheme le gustaría que proporciona colores personalizados.

3. Haga doble clic en los archivos y seleccione **propiedades**. Cambiar la acción de compilación a **contenido** y **incluir en VSIX** propiedad en true.

4. Cree un archivo .pkgdef y agregue una línea similar al siguiente:

  ```xml
  [$RootKey$\TextMate\Repositories]
  "MyLang"="$PackageFolder$\Grammars"
  ```

5. Haga doble clic en los archivos y seleccione **propiedades**. Cambiar la acción de compilación a **contenido** y **incluir en VSIX** propiedad en true.

Esto agrega la carpeta "Gramáticas" en el directorio de instalación del paquete como un origen de repositorio con el nombre 'MyLang' ('MyLang' es simplemente un nombre para la anulación de ambigüedades y puede ser cualquier cadena única). Todas las gramáticas (archivos .tmlanguage) y el tema archivos (.tmtheme) en este directorio se recogen como ventas potenciales y reemplazan las gramáticas integradas proporcionadas con TextMate. Si extensiones declarado del archivo de gramática coincide con la extensión del archivo se abre, recorre paso a paso TextMate.

## <a name="creating-a-simple-language-client"></a>Creación de un cliente de un lenguaje simple

### <a name="main-interface---ilanguageclienthttpsdocsmicrosoftcomdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>Interfaz principal - [ILanguageClient](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Después de crear el proyecto VSIX, agregue los siguientes paquetes de NuGet al proyecto:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

A continuación, puede crear una nueva clase que implementa el [ILanguageClient](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) interfaz, la interfaz principal necesaria para clientes de lenguaje que se conectan a un servidor de lenguaje basado en LSP.

A continuación se muestra un ejemplo:

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync?.InvokeAsync(this, EventArgs.Empty);
        }
    }
}
```

Los métodos principales que deben implementarse son [OnLoadedAsync](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) y [ActivateAsync](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) se llama cuando Visual Studio ha cargado la extensión y el servidor de idioma está listo para iniciarse. En este método, puede invocar la [StartAsync](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegado inmediatamente para indicar que se debe iniciar el servidor de idioma, o puede hacer ninguna lógica adicional e invocar [StartAsync](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) más tarde. **Para activar el servidor de idioma se debe llamar a StartAsync en algún momento.**

[ActivateAsync](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) es el método invocado finalmente mediante una llamada a la [StartAsync](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegar; contiene la lógica para iniciar el servidor de idioma y establecer conexión con él. Un objeto de conexión deberá ser devuelta que contiene secuencias para escribir en el servidor y la lectura desde el servidor. Las excepciones producidas aquí se detecta y se mostrará al usuario a través de un mensaje de la barra de información en Visual Studio.

### <a name="activation"></a>Activación

Una vez que se implementa la clase de cliente de idioma, debe definir dos atributos que definen cómo se cargan en Visual Studio y activado:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio usa [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) para administrar sus puntos de extensibilidad. El [exportar](https://msdn.microsoft.com/library/system.componentmodel.composition.exportattribute(v=vs.110).aspx) atributo indica a Visual Studio que esta clase debe ser recoge como un punto de extensión y cargada en el momento adecuado.

Para utilizar MEF, debe definir también MEF como activo en el manifiesto de VSIX.

Abra el Diseñador de manifiestos VSIX y navegue hasta la **activos** ficha:

![Agregar MEF activo](media/lsp-add-asset.png)

Haga clic en nuevo para crear un nuevo recurso:

![definir el recurso MEF](media/lsp-define-asset.png)

* **Tipo de**: Microsoft.VisualStudio.MefComponent
* **Origen**: un proyecto en la solución actual
* **Proyecto**: [el proyecto]

### <a name="content-type-definition"></a>Definición de tipo de contenido

Actualmente la única manera de cargar la extensión de servidor de lenguaje basado en LSP es por tipo de contenido del archivo. Es decir, al definir la clase de cliente de idioma (que implementa [ILanguageClient](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), debe definir los tipos de archivos, cuando se abre, que cargará la extensión. Si no se ha abierto ningún archivo que coinciden con el tipo de contenido definido, no se cargará la extensión.

Esto se realiza a través de definir una o más clases de ContentTypeDefinition:

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;


        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

En el ejemplo anterior, se crea una definición de tipo de contenido para los archivos que terminan en la extensión de archivo .bar. La definición de tipo de contenido tiene la barra"name" y **debe** derivan de [CodeRemoteContentTypeName](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Después de agregar una definición de tipo de contenido, a continuación, puede definir cuándo se debe cargar la extensión de cliente de idioma en la clase de cliente de idioma:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Agregar compatibilidad con servidores de lenguaje LSP no sea necesario implementar su propio sistema de proyecto en Visual Studio. Los clientes pueden abrir un único archivo o una carpeta en Visual Studio para empezar a usar el servicio de lenguaje. De hecho, la compatibilidad con servidores LSP lenguaje está diseñado para funcionar solo en escenarios de carpeta o archivo abierto. Algunas características, como la configuración, no funcionará si se implementa un sistema de proyecto personalizado.

## <a name="advanced-features"></a>Características avanzadas

### <a name="settings"></a>Configuración

Compatibilidad de servidor de lenguaje personalizado específico de configuración está disponible para la versión preliminar de soporte técnico LSP en Visual Studio, pero aún está en proceso que se ha mejorado. Configuración es específica para lo que es compatible con el servidor de idioma y suele controlar cómo el servidor de lenguaje envía datos. Por ejemplo, un servidor de lenguaje podría tener un valor para el número máximo de errores notificados. Los autores de extensión tendría que definir un valor predeterminado, que puede ser cambiado por los usuarios para proyectos específicos.

Siga estos pasos para agregar compatibilidad para la configuración a la extensión de servicio de lenguaje LSP:

1. Agregue un archivo JSON (por ejemplo, "MockLanguageExtensionSettings.json") en el proyecto que contiene la configuración y sus valores predeterminados. Por ejemplo:

  ```json
  {
    "foo.maxNumberOfProblems": -1
  }
  ```
2. Haga clic con el botón secundario en el archivo JSON y seleccione **propiedades**. Cambiar el **compilar** acción "Contenido" y "incluir en VSIX' propiedad en true.

3. Implementar ConfigurationSections y devolver la lista de prefijos para la configuración definida en el archivo JSON (en código de Visual Studio, se podría asignar al nombre de sección de configuración en package.json):

  ```csharp
  public IEnumerable<string> ConfigurationSections
  {
      get
      {
          yield return "foo";
      }
  }
  ```
4. Agregue un archivo .pkgdef al proyecto (Agregar nuevo archivo de texto y cambie la extensión de archivo .pkgdef). El archivo pkgdef debe contener esta información:

  ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
  ```

5. Haga clic con el botón secundario en el archivo .pkgdef y seleccione **propiedades**. Cambiar el **generar** acción como "Contenido" y la propiedad "Incluir en VSIX" en true.

6. Abra la `source.extension.vsixmanifest` de archivos y agregar un activo en el **Asset** ficha:

  ![Editar activos de vspackage](media/lsp-add-vspackage-asset.png)

  * **Tipo de**: Microsoft.VisualStudio.VsPackage
  * **Origen**: archivo en filesystem
  * **Ruta de acceso**: [ruta de acceso al archivo pkgdef]

### <a name="user-editing-of-settings-for-a-workspace"></a>Edición de usuario de configuración para un área de trabajo

1. Usuario abre un área de trabajo que contiene archivos que posee el servidor.
2. Usuario agrega un archivo en la carpeta de "VS" denominada "VSWorkspaceSettings.json".
3. Usuario agrega una línea al archivo VSWorkspaceSettings.json para una configuración que proporciona el servidor. Por ejemplo:

  ```json
  {
    "foo.maxNumberOfProblems": 10
  }
  ```

### <a name="custom-messages"></a>Mensajes personalizados

Existen API en su lugar para facilitar la transferencia de mensajes a y recibir los mensajes desde el servidor de lenguaje que no forman parte del protocolo de servidor de lenguaje estándar. Para controlar los mensajes personalizados, implementar [ILanguageClientCustomMessage](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) interfaz en la clase de cliente de lenguaje. [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) biblioteca se utiliza para transmitir mensajes personalizados entre el cliente de idioma y el servidor de idioma. Puesto que la extensión del cliente de lenguaje LSP es igual que cualquier otra extensión de Visual Studio, puede decidir agregar características adicionales (que no se admiten por lo LSP) para Visual Studio (con otras API de Studio Visual) en la extensión a través de mensajes personalizados.

#### <a name="receiving-custom-messages"></a>Recibir mensajes personalizados

Para recibir mensajes personalizados desde el servidor de lenguaje, implemente el [CustomMessageTarget](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) propiedad [ILanguageClientCustomMessage](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) y devolver un objeto que sabe cómo tratar los mensajes personalizados . Ejemplo siguiente:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="sending-custom-messages"></a>Envío de mensajes personalizado

Para enviar mensajes personalizados en el servidor de lenguaje, implementar la [AttachForCustomMessageAsync](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) método [ILanguageClientCustomMessage](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Este método se invoca cuando el servidor de idioma se ha iniciado y está listo para recibir mensajes. A [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) objeto se pasa como un parámetro, que, a continuación, puede mantener para enviar mensajes en el servidor de idioma mediante [StreamJsonRpc VS](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) API. Ejemplo siguiente:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
}
```

### <a name="middle-layer"></a>Capa intermedia

A veces, un desarrollador de extensión deseará interceptar LSP los mensajes enviados y recibidos desde el servidor de idioma. Por ejemplo, un desarrollador de extensión puede desea modificar el parámetro de mensaje enviado un mensaje concreto de LSP o modificar los resultados devueltos desde el servidor de idioma de una característica LSP (por ejemplo, las finalizaciones). Cuando es necesario, los desarrolladores de extensión pueden utilizar la API MiddleLayer para interceptar los mensajes LSP.

Cada mensaje LSP tiene su propia interfaz de capa intermedia de interceptación. Para interceptar un mensaje determinado, cree una clase que implementa la interfaz de capa intermedia para ese mensaje. A continuación, implementar la [ILanguageClientCustomMessage](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) en la clase de cliente de idioma de interfaz y devolver una instancia del objeto en el [MiddleLayer](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) propiedad. Ejemplo siguiente:

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{

    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
}
```

La característica de capa intermedia está aún en desarrollo y todavía no es exhaustiva.

## <a name="sample-lsp-language-server-extension"></a>Ejemplo de extensión de servidor de lenguaje LSP

Para ver el código fuente de una extensión de ejemplo mediante la API de cliente LSP en Visual Studio, vea ejemplos de extensibilidad de VSSDK [ejemplo LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Preguntas más frecuentes

**Le gustaría crear un sistema de proyecto personalizadas para complementar mi servidor de lenguaje LSP para proporcionar una mayor compatibilidad de característica en Visual Studio, ¿cómo hago hacerlo?**

Compatibilidad con servidores de lenguaje basado en LSP en Visual Studio se basan en el [característica Abrir carpeta](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) y está diseñado específicamente para que no necesite un sistema de proyecto personalizado. Puede crear su propio sistema de proyecto personalizadas siguiendo las instrucciones [aquí](https://github.com/Microsoft/VSProjectSystem), pero algunas características, como la configuración, no funcionen. La lógica de inicialización predeterminada para los servidores de lenguaje LSP consiste en pasar la ubicación de la carpeta raíz de la carpeta que se está abierta actualmente, por lo que si usa un sistema de proyecto personalizado, puede que necesite proporcionar lógica personalizada durante la inicialización para asegurarse de su servidor de idioma puede iniciar correctamente.

**¿Cómo se agrega compatibilidad del depurador?**

Se va a proporcionar soporte técnico para el [comunes de depuración de protocolo](https://code.visualstudio.com/docs/extensionAPI/api-debugging) en una versión futura.

**Si ya hay un servicio de lenguaje compatible de VS instalado (por ejemplo, JavaScript), ¿puedo todavía instalar una extensión de servidor de lenguaje LSP que ofrece características adicionales (por ejemplo, linting)?**

Sí, pero no todas las características funcionarán correctamente. El objetivo definitivo para extensiones de servidor de lenguaje LSP consiste en habilitar los servicios de lenguaje no admitidos nativamente por Visual Studio. Puede crear extensiones que ofrecen una compatibilidad adicional con servidores de lenguaje LSP, pero algunas características, como IntelliSense, no será una experiencia sin problemas. En general, recomendamos que las extensiones de servidor de lenguaje LSP usarse para proporcionar nuevas experiencias de lenguaje, no extender los existentes.

**¿Dónde se puede publicar mi servidor de lenguaje LSP completada VSIX?**

Consulte las instrucciones de Marketplace [aquí](walkthrough-publishing-a-visual-studio-extension.md).
