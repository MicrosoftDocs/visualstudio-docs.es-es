---
title: Agregar una extensión del protocolo del servidor idioma | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d7590350fdcfb74f90cd4441e97503a60b298c66
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954285"
---
# <a name="add-a-language-server-protocol-extension"></a>Agregar una extensión del protocolo de servidor de lenguaje

El protocolo de servidor de lenguaje (LSP) es un protocolo común, en el formulario de la versión 2.0 de JSON RPC, usar para proporcionar características de servicio a varios editores de código de lenguaje. Mediante el protocolo, los desarrolladores pueden escribir un servidor único idioma para proporcionar características como IntelliSense, diagnósticos de errores del servicio de lenguaje, busque todas las referencias, etc. para varios editores de código que admiten el LSP. Tradicionalmente, se pueden agregar servicios de lenguaje en Visual Studio, puede usar los archivos de gramática de TextMate para proporcionar funcionalidades básicas como resaltado de sintaxis, o mediante la escritura de servicios de lenguaje personalizado con el conjunto completo de API de extensibilidad de Visual Studio para proporcionar datos enriquecidos. Ahora, la compatibilidad con lo LSP ofrece una tercera opción.

![servicio de protocolo de servidor de lenguaje de Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protocolo de servidor de lenguaje

![implementación del protocolo de servidor de lenguaje](media/lsp-implementation.png)

En este artículo se describe cómo crear una extensión de Visual Studio que usa un servidor de lenguaje basado en LSP. Se supone que ya ha desarrollado un servidor de lenguaje basado en LSP y solo desea integrarla en Visual Studio.

Para la compatibilidad con Visual Studio, servidores de lenguaje pueden comunicarse con el cliente (Visual Studio) a través de cualquier mecanismo de transmisión de flujo en función, por ejemplo:

* Flujos de entrada/salida estándar
* Canalizaciones con nombre
* Sockets (TCP solo)

Servicios de lenguaje integrado que no forman parte del producto de Visual Studio es la intención de los LSP y soporte técnico para él en Visual Studio. No está pensado para ampliar los servicios de lenguaje existentes (por ejemplo, C#) en Visual Studio. Para ampliar lenguajes existentes, consulte la Guía de extensibilidad del servicio de lenguaje (por ejemplo, el ["Roslyn" de .NET Compiler Platform](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)).

Para obtener más información sobre el mismo protocolo, consulte la documentación [aquí](https://github.com/Microsoft/language-server-protocol).

Para obtener más información sobre cómo crear un servidor de lenguaje del ejemplo o cómo integrar un servidor existente de lenguaje en Visual Studio Code, consulte la documentación [aquí](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-features-supported"></a>Características de protocolo del servidor de lenguaje admitidas

Las siguientes características LSP hasta ahora se admiten en Visual Studio:

Mensaje | Tiene compatibilidad en Visual Studio
--- | ---
inicializar | sí
inicializado | sí
cierre | sí
exit | sí
$/cancelRequest | sí
window/showMessage | sí
window/showMessageRequest | sí
window/logMessage | sí
evento de telemetría / |
client/registerCapability |
client/unregisterCapability |
workspace/didChangeConfiguration | sí
workspace/didChangeWatchedFiles | sí
workspace/symbol | sí
workspace/executeCommand | sí
workspace/applyEdit | sí
textDocument/publishDiagnostics | sí
textDocument/didOpen | sí
textDocument/didChange | sí
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | sí
textDocument/didClose | sí
textDocument/completion | sí
finalización o resolver | sí
textDocument/hover | sí
textDocument/signatureHelp | sí
textDocument/references | sí
textDocument/documentHighlight | sí
textDocument/documentSymbol | sí
textDocument/formatting | sí
textDocument/rangeFormatting | sí
textDocument/onTypeFormatting |
textDocument/definition | sí
textDocument/codeAction | sí
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/rename | sí

## <a name="getting-started"></a>Introducción

> [!NOTE]
> A partir de Visual Studio 15,8 Preview 3, compatibilidad con el protocolo de servidor de lenguaje común está integrado en Visual Studio. Si ha creado con la versión preliminar de extensiones LSP [VSIX de cliente de servidor de lenguaje](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) versión, dejará de funcionar una vez para que haya actualizado a 15,8 Preview 3 o posterior. Deberá hacer lo siguiente para obtener las extensiones LSP funcione de nuevo:
>
> 1. Desinstale el protocolo de servidor de Microsoft Visual Studio lenguaje Preview VSIX. A partir de 15,8 Preview 4, cada vez que realice una actualización en Visual Studio, hemos automáticamente detectará y quitar la versión preliminar de VSIX automáticamente durante el proceso de actualización.
>
> 2. Actualizar la referencia de Nuget a la última versión sin vista previa para [paquetes LSP](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Quite la dependencia para Microsoft Visual Studio lenguaje servidor Protocolo de vista previa de VSIX en el manifiesto de VSIX.
>
> 4. Asegúrese de que el proyecto de VSIX especifica 15,8 Preview 3 de Visual Studio como el límite inferior para el destino de la instalación.
>
> 5. Recompile y vuelva a implementar.

### <a name="create-a-vsix-project"></a>Cree un proyecto VSIX

Para crear una extensión de servicio de lenguaje mediante un lenguaje basado en LSP de servidor, primero debe asegurarse de que tiene el **desarrollo de extensiones de Visual Studio** carga de trabajo instalada para la instancia de VS.

A continuación, cree un nuevo VSIXProject en blanco, vaya a **archivo** > **nuevo proyecto** > **Visual C#**  >   **Extensibilidad** > **proyecto VSIX**:

![Crear proyecto de vsix](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Instalación de servidor y en tiempo de ejecución de lenguaje

De forma predeterminada, las extensiones que se crea para admitir servidores de lenguaje basado en LSP en Visual Studio no contendrá los propios servidores de lenguaje o los tiempos de ejecución necesarios para ejecutarlos. Los desarrolladores de extensiones son responsables de la distribución de los servidores de lenguaje y los tiempos de ejecución es necesitado. Hay varias maneras de hacerlo:

* Servidores de idiomas se pueden incrustar en el archivo VSIX como archivos de contenido.
* Crear un archivo MSI para instalar el servidor de lenguaje, o necesita tiempos de ejecución.
* Se proporcionan instrucciones sobre informarles de Marketplace para obtener tiempos de ejecución y de idioma de los servidores.

### <a name="textmate-grammar-files"></a>Archivos de gramática de TextMate

El LSP no incluye la especificación sobre cómo proporcionar la coloración de texto de idiomas. Para proporcionar personalizada coloración para lenguajes de Visual Studio, los desarrolladores de extensiones pueden usar un archivo de gramática de TextMate. Para agregar archivos personalizados de tema o la gramática de TextMate, siga estos pasos:

1. Cree una carpeta denominada "Gramáticas" dentro de la extensión (o puede ser cualquier nombre que elija).

2. Dentro de la *gramáticas* carpeta, incluya ningún  *\*.tmlanguage*,  *\*.plist*,  *\*.tmtheme*, o  *\*.json* archivos que le gustaría que proporciona la coloración personalizada.

3. Haga doble clic en los archivos y seleccione **propiedades**. Cambiar el **compilar** acción a **contenido** y el **incluir en VSIX** propiedad en true.

4. Crear un *.pkgdef* archivo y agregue una línea similar a esto:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

5. Haga doble clic en los archivos y seleccione **propiedades**. Cambiar el **compilar** acción a **contenido** y el **incluir en VSIX** propiedad en true.

Después de completar los pasos anteriores, un *gramáticas* carpeta se agrega a la instalación del paquete en el directorio como un origen de repositorio denominado 'MyLang' ('MyLang' es simplemente un nombre para la desambiguación y puede ser cualquier cadena única). Todas las gramáticas (*.tmlanguage* archivos) y archivos de tema (*.tmtheme* archivos) en este directorio se recogen como ventas potenciales y reemplazan las gramáticas integradas proporcionadas con TextMate. Si las extensiones declarado del archivo de gramática coincide con la extensión del archivo está abierto, irá TextMate.

## <a name="create-a-simple-language-client"></a>Crear a un cliente de un lenguaje simple

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>Interfaz principal - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Después de crear el proyecto VSIX, agregue los siguientes paquetes de NuGet al proyecto:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Al tomar una dependencia en el paquete NuGet después de completar los pasos anteriores, los paquetes de Newtonsoft.Json y StreamJsonRpc se agregan a su proyecto. **No se actualizan estos paquetes si no está seguro de que esas versiones se instalará en la versión de Visual Studio que se dirija su extensión**. Los ensamblados no se incluirá en el proyecto de VSIX, en su lugar, seleccionará en el directorio de instalación de Visual Studio. Si se hace referencia a una versión más reciente de los ensamblados que lo que está instalado en el equipo del usuario, la extensión *no funcionará*.

A continuación, puede crear una nueva clase que implementa el [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) interfaz, la interfaz principal necesaria para clientes de lenguaje que se conectan a un servidor de lenguaje basado en LSP.

Este es un ejemplo:

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
            await StartAsync.InvokeAsync(this, EventArgs.Empty);
        }

        public Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Los métodos principales que deben implementarse son [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) y [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) se llama cuando Visual Studio ha cargado la extensión y el servidor de lenguaje está listo para iniciarse. En este método, puede invocar el [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegado inmediatamente para indicar que se debe iniciar el servidor de lenguaje, o puede hacer lógica adicional e invocar [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) más adelante. **Para activar el servidor de lenguaje, se debe llamar a StartAsync en algún momento.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) es el método finalmente invocado por una llamada a la [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegar; contiene la lógica para iniciar el servidor de lenguaje y establecer conexión con él. Se debe devolver un objeto de conexión que contiene secuencias para escribir en el servidor y leer desde el servidor. Detecta las excepciones producidas aquí y se muestra al usuario a través de un mensaje de la barra de información en Visual Studio.

### <a name="activation"></a>Activación

Una vez que se implementa la clase de cliente de lenguaje, necesita definir dos atributos que definen cómo se cargan en Visual Studio y activado:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio usa [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) para administrar sus puntos de extensibilidad. El [exportar](/dotnet/api/system.componentmodel.composition.exportattribute) atributo indica a Visual Studio que esta clase debe recoge como un punto de extensión y se cargan en el momento adecuado.

Para utilizar MEF, también debe definir MEF como activo en el manifiesto de VSIX.

Abra el Diseñador de manifiestos VSIX y navegue hasta la **activos** pestaña:

![Agregar recurso MEF](media/lsp-add-asset.png)

Haga clic en nuevo para crear un nuevo recurso:

![definir el recurso MEF](media/lsp-define-asset.png)

* **Tipo**: Microsoft.VisualStudio.MefComponent
* **Origen**: Un proyecto de la solución actual
* **Proyecto**: [su proyecto]

### <a name="content-type-definition"></a>Definición de tipo de contenido

Actualmente, la única manera de cargar la extensión de servidor de lenguaje basado en LSP es por tipo de contenido del archivo. Es decir, al definir la clase de cliente de idioma (que implementa [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), deberá definir los tipos de archivos que, cuando se abre, hará que la extensión cargar. Si no hay archivos que coincidan con el tipo de contenido definido se abren, no se cargará la extensión.

Esto se realiza a través de definir una o más clases ContentTypeDefinition:

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

En el ejemplo anterior, se crea una definición de tipo de contenido para los archivos que terminan en *.bar* la extensión de archivo. La definición de tipo de contenido tiene la barra"nombre" y **debe** derivan [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Después de agregar una definición de tipo de contenido, a continuación, puede definir cuándo se debe cargar la extensión de cliente de idioma en la clase de cliente de lenguaje:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Agregar compatibilidad con servidores de lenguaje LSP no requiere implementar su propio sistema de proyecto en Visual Studio. Los clientes pueden abrir un único archivo o una carpeta en Visual Studio para empezar a usar el servicio de lenguaje. De hecho, la compatibilidad con servidores LSP lenguaje está diseñado para funcionar solo en escenarios de carpeta o el archivo abierto. Si se implementa un sistema de proyectos personalizados, algunas características (como la configuración) no funcionarán.

## <a name="advanced-features"></a>Características avanzadas

### <a name="settings"></a>Configuración

Soporte técnico para la configuración específica del servidor de lenguaje personalizada está disponible, pero aún está en proceso que se ha mejorado. Valores son específicos para lo que es compatible con el servidor de lenguaje y suele controlar cómo el servidor de lenguaje emite datos. Por ejemplo, un servidor de lenguaje podría tener un valor para el número máximo de errores notificados. Los autores de extensiones definiría un valor predeterminado, que se puede cambiar por los usuarios para proyectos específicos.

Siga estos pasos para agregar compatibilidad para la configuración a la extensión de servicio de lenguaje LSP:

1. Agregue un archivo JSON (por ejemplo, *MockLanguageExtensionSettings.json*) en el proyecto que contiene la configuración y sus valores predeterminados. Por ejemplo:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```
2. Haga doble clic en el archivo JSON y seleccione **propiedades**. Cambio la **compilar** acción para "Content" y "incluir en VSIX' propiedad en true.

3. Implementar ConfigurationSections y devolver la lista de los prefijos de la configuración definida en el archivo JSON (en Visual Studio Code, se podría asignar al nombre de sección de configuración en package.json):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Agregue un archivo .pkgdef en el proyecto (Agregar nuevo archivo de texto y cambie la extensión de archivo .pkgdef). El archivo pkgdef debe contener esta información:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Ejemplo:
    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Haga clic con el botón derecho en el archivo .pkgdef y seleccione **propiedades**. Cambiar el **compilar** acción a **contenido** y el **incluir en VSIX** propiedad en true.

6. Abra el *source.extension.vsixmanifest* archivo y agregue un recurso en el **activos** pestaña:

   ![Editar recurso de vspackage](media/lsp-add-vspackage-asset.png)

   * **Tipo**: Microsoft.VisualStudio.VsPackage
   * **Origen**: Archivo en filesystem
   * **Ruta de acceso**: [ruta de acceso a su *.pkgdef* archivo]

### <a name="user-editing-of-settings-for-a-workspace"></a>Edición del usuario de configuración para un área de trabajo

1. Usuario abre un área de trabajo que contiene los archivos que posee el servidor.
2. Usuario agrega un archivo en el *.vs* carpeta denominada *VSWorkspaceSettings.json*.
3. Usuario agrega una línea a la *VSWorkspaceSettings.json* archivo para una configuración que proporciona el servidor. Por ejemplo:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enabling-diagnostics-tracing"></a>Habilitar el seguimiento de diagnóstico

Seguimiento de diagnóstico puede habilitarse para todos los mensajes entre el cliente y servidor, que puede ser útil al depurar problemas de salida. Para habilitar el seguimiento de diagnóstico, haga lo siguiente:

4. Abra o cree el archivo de configuración de área de trabajo *VSWorkspaceSettings.json* (vea "Edición del usuario de configuración para un área de trabajo").
5. Agregue la siguiente línea en el archivo de configuración de json:

```json
{
    "foo.trace.server": "Off"
}
```

Hay tres valores posibles para el nivel de detalle del seguimiento:
* "Desactivado": el seguimiento desactivado completamente
* "Los mensajes": activado pero el identificador de nombre y la respuesta de método solo se realiza un seguimiento.
* "Detallado": activado; el mensaje rpc todo se realiza un seguimiento.

Cuando está activado el seguimiento del contenido se escribe en un archivo en el *%temp%\VisualStudio\LSP* directory. El registro sigue el formato de nomenclatura *[LanguageClientName]-[marca de fecha y hora] .log*. Actualmente, el seguimiento solo puede habilitarse para escenarios de carpeta abierta. Apertura de un único archivo para activar un servidor de lenguaje no tiene soporte de seguimiento de diagnóstico.

### <a name="custom-messages"></a>Mensajes personalizados

Existen API en su lugar para facilitar la transferencia de mensajes y recibir mensajes desde el servidor de lenguaje que no forman parte del protocolo de servidor estándar de lenguaje. Para controlar mensajes personalizados, implementar [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) interfaz en la clase de cliente de lenguaje. [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) biblioteca se usa para transmitir mensajes personalizados entre el cliente de lenguaje y el servidor de lenguaje. Puesto que la extensión de cliente de lenguaje LSP es igual que cualquier otra extensión de Visual Studio, puede decidir agregar características adicionales (que no se admiten por lo LSP) para Visual Studio (con otras API de Visual Studio) en la extensión a través de mensajes personalizados.

#### <a name="receiving-custom-messages"></a>Recepción de mensajes personalizado

Para recibir mensajes personalizados desde el servidor de lenguaje, implemente el [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) propiedad [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) y devolver un objeto que sabe cómo tratar los mensajes personalizados . Ejemplo siguiente:

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

Para enviar mensajes personalizados en el servidor de lenguaje, implemente el [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) método [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Este método se invoca cuando el servidor de lenguaje está iniciado y preparado para recibir mensajes. Un [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) objeto se pasa como un parámetro, que, a continuación, puede mantener para enviar mensajes en el servidor de lenguaje mediante [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) API. Ejemplo siguiente:

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
}
```

### <a name="middle-layer"></a>Capa intermedia

A veces, un desarrollador de extensión puede interceptar los mensajes enviados y recibidos desde el servidor de lenguaje LSP. Por ejemplo, un desarrollador de extensiones es posible que desea modificar el parámetro de mensaje enviado un mensaje concreto de LSP o modificar los resultados devueltos desde el servidor de lenguaje para una característica LSP (por ejemplo, las finalizaciones). Cuando es necesario, los desarrolladores de extensiones pueden usar la API MiddleLayer para interceptar los mensajes LSP.

Cada mensaje LSP tiene su propia interfaz de capa intermedia de intercepción. Para interceptar un mensaje concreto, cree una clase que implementa la interfaz de capa intermedia para ese mensaje. A continuación, implemente el [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) en la clase de cliente de idioma de interfaz y devolver una instancia del objeto en el [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) propiedad. Ejemplo siguiente:

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
}
```

La característica de capa intermedia está aún en desarrollo y todavía no es exhaustiva.

## <a name="sample-lsp-language-server-extension"></a>Ejemplo de extensión de servidor de lenguaje LSP

Para ver el código fuente de una extensión de ejemplo mediante la API de cliente LSP en Visual Studio, vea los ejemplos de extensibilidad de VSSDK [ejemplo LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Preguntas más frecuentes

**Me gustaría crear un sistema de proyecto personalizadas para complementar mi servidor de lenguaje LSP para proporcionar compatibilidad con las características más completa en Visual Studio, ¿cómo ir sobre cómo hacer que?**

Compatibilidad con lenguajes basados en LSP servidores en Visual Studio se basa en el [característica Abrir carpeta](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) y está específicamente diseñado para no requerir un sistema de proyecto personalizado. Puede crear su propio sistema de proyecto personalizado siguiendo las instrucciones [aquí](https://github.com/Microsoft/VSProjectSystem), pero algunas características, como la configuración, podrían no funcionar. La lógica de inicialización predeterminado para los servidores de lenguaje LSP consiste en pasar la ubicación de la carpeta raíz de la carpeta que se está abierta actualmente, por lo que es posible que si usa un sistema de proyectos personalizados, deberá proporcionar lógica personalizada durante la inicialización para asegurarse de su servidor de lenguaje puede iniciar correctamente.

**¿Cómo se puede agregar compatibilidad con el depurador?**

Le proporcionaremos soporte técnico para el [comunes de depuración de protocolo](https://code.visualstudio.com/docs/extensionAPI/api-debugging) en una versión futura.

**Si ya hay un servicio de lenguaje admitidos de VS instalado (por ejemplo, JavaScript), ¿puedo todavía instalar una extensión de servidor de lenguaje LSP que ofrece características adicionales (por ejemplo, linting)?**

Sí, pero no todas las características funcionará correctamente. El objetivo final para extensiones de servidor de lenguaje LSP es habilitar los servicios de lenguaje no admitidos nativamente por Visual Studio. Puede crear extensiones que ofrecen compatibilidad adicional con servidores de LSP en idiomas, pero algunas características (por ejemplo, IntelliSense) no será una experiencia fluida. En general, se recomienda que las extensiones de servidor de lenguaje LSP se usar para proporcionar nuevas experiencias de lenguaje, no ampliar los existentes.

**¿Dónde se pueden publicar mi servidor de lenguaje LSP VSIX completado?**

Consulte las instrucciones de Marketplace [aquí](walkthrough-publishing-a-visual-studio-extension.md).
