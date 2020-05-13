---
title: Adición de una extensión de protocolo de servidor de lenguaje ( Language Server Protocol extension) Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef2093915538f09f425fc961420c4a3078043c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740237"
---
# <a name="add-a-language-server-protocol-extension"></a>Adición de una extensión del protocolo de servidor de lenguaje

El protocolo de servidor de lenguaje (LSP) es un protocolo común, en forma de JSON RPC v2.0, que se utiliza para proporcionar características de servicio de lenguaje a varios editores de código. Mediante el protocolo, los desarrolladores pueden escribir un único servidor de lenguaje para proporcionar características de servicio de lenguaje como IntelliSense, diagnóstico de errores, buscar todas las referencias, etc., a varios editores de código que admiten el LSP. Tradicionalmente, los servicios de lenguaje en Visual Studio se pueden agregar mediante el uso de archivos de gramática TextMate para proporcionar funcionalidades básicas, como resaltado de sintaxis o mediante la escritura de servicios de lenguaje personalizados que usan el conjunto completo de API de extensibilidad de Visual Studio para proporcionar datos más enriquecidos. Con la compatibilidad de Visual Studio con LSP, hay una tercera opción.

![servicio de protocolo de servidor de lenguaje en Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protocolo de servidor de lenguaje

![implementación del protocolo de servidor de lenguaje](media/lsp-implementation.png)

En este artículo se describe cómo crear una extensión de Visual Studio que usa un servidor de lenguaje basado en LSP. Se supone que ya ha desarrollado un servidor de lenguaje basado en LSP y solo desea integrarlo en Visual Studio.

Para la compatibilidad con Visual Studio, los servidores de lenguaje pueden comunicarse con el cliente (Visual Studio) a través de cualquier mecanismo de transmisión basado en secuencias, por ejemplo:

* Flujos de entrada/salida estándar
* Canalizaciones con nombre
* Sockets (solo TCP)

La intención del LSP y la compatibilidad con él en Visual Studio es incorporar servicios de lenguaje que no forman parte del producto de Visual Studio. No está pensado para extender los servicios de lenguaje existentes (por lo que C) en Visual Studio. Para ampliar los idiomas existentes, consulte la guía de extensibilidad del servicio de lenguaje (por ejemplo, ["Roslyn" .NET Compiler Platform)](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)o consulte [Extender el editor y](../extensibility/extending-the-editor-and-language-services.md)los servicios de lenguaje .

Para obtener más información sobre el protocolo en sí, consulte la documentación [aquí](https://github.com/Microsoft/language-server-protocol).

Para obtener más información sobre cómo crear un servidor de lenguaje de ejemplo o cómo integrar un servidor de lenguaje existente en Visual Studio Code, vea la documentación [aquí.](https://code.visualstudio.com/docs/extensions/example-language-server)

## <a name="language-server-protocol-supported-features"></a>Características compatibles con Language Server Protocol

En las tablas siguientes se muestran qué características de LSP se admiten en Visual Studio:

Message | Tiene soporte en Visual Studio
--- | ---
initialize | sí
inicializado | sí
shutdown | sí
exit | sí
$/cancelRequest | sí
window/showMessage | sí
window/showMessageRequest | sí
window/logMessage | sí
telemetría/evento |
cliente/registroCapability |
client/unregisterCapability |
workspace/didChangeConfiguration | sí
workspace/didChangeWatchedFiles | sí
espacio de trabajo/símbolo | sí
workspace/executeCommand | sí
workspace/applyEditar | sí
textDocument/publishDiagnostics | sí
textDocument/didOpen | sí
textDocument/didChange | sí
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | sí
textDocument/didClose | sí
textDocument/completion | sí
finalización/resolución | sí
textDocument/hover | sí
textDocument/signatureHelp | sí
textDocument/references | sí
textDocument/documentHighlight | sí
textDocument/documentSymbol | sí
textDocument/formatting | sí
textDocument/rangeFormatting | sí
textDocument/onTypeFormatting |
textDocument/definición | sí
textDocument/codeAction | sí
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/rename | sí

## <a name="get-started"></a>Introducción

> [!NOTE]
> A partir de Visual Studio 2017 versión 15.8, la compatibilidad con el protocolo de servidor de lenguaje común está integrada en Visual Studio. Si ha creado extensiones LSP con la versión preliminar de [Language Server Client VSIX,](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) dejarán de funcionar una vez que actualice a la versión 15.8 o posterior. Tendrá que hacer lo siguiente para que las extensiones LSP vuelvan a funcionar:
>
> 1. Desinstale microsoft Visual Studio Language Server Protocol Preview VSIX.
>
>    A partir de la versión 15.8, cada vez que se realiza una actualización en Visual Studio, la vista previa VSIX se detecta y quita automáticamente.
>
> 2. Actualice la referencia de Nuget a la última versión no preliminar para [paquetes LSP.](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)
>
> 3. Quite la dependencia a Microsoft Visual Studio Language Server Protocol Preview VSIX en el manifiesto VSIX.
>
> 4. Asegúrese de que VSIX especifica Visual Studio 2017 versión 15.8 Preview 3 como el límite inferior para el destino de instalación.
>
> 5. Vuelva a compilar e implementar.

### <a name="create-a-vsix-project"></a>Crear un proyecto VSIX

Para crear una extensión de servicio de lenguaje mediante un servidor de lenguaje basado en LSP, primero asegúrese de que tiene la carga de trabajo de desarrollo de extensión de **Visual Studio** instalada para la instancia de VS.

A continuación, cree un nuevo proyecto VSIX navegando a **Archivo** > **Nuevo proyecto** > **Proyecto** > de visual de**xextensibilidad** > **VSIX Proyecto:**

![crear proyecto vsix](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Servidor de idioma e instalación en tiempo de ejecución

De forma predeterminada, las extensiones creadas para admitir servidores de lenguaje basados en LSP en Visual Studio no contienen los propios servidores de lenguaje ni los tiempos de ejecución necesarios para ejecutarlos. Los desarrolladores de extensiones son responsables de distribuir los servidores de lenguaje y los tiempos de ejecución necesarios. Hay varias maneras de hacerlo:

* Los servidores de lenguaje se pueden incrustar en El VSIX como archivos de contenido.
* Cree un MSI para instalar el servidor de idioma y/o los tiempos de ejecución necesarios.
* Proporcione instrucciones sobre Marketplace para informar a los usuarios sobre cómo obtener tiempos de ejecución y servidores de idioma.

### <a name="textmate-grammar-files"></a>Archivos de gramática TextMate

El LSP no incluye especificaciones sobre cómo proporcionar coloración de texto para idiomas. Para proporcionar coloración personalizada para los lenguajes en Visual Studio, los desarrolladores de extensiones pueden usar un archivo de gramática TextMate. Para agregar archivos de tema o gramática TextMate personalizados, siga estos pasos:

1. Crea una carpeta llamada "Grammars" dentro de tu extensión (o puede ser el nombre que elijas).

2. Dentro de la carpeta *Gramáticas,* incluya los * \*archivos .tmlanguage*, * \*.plist*, * \*.tmtheme*o * \*.json* que desee que proporcionen una coloración personalizada.

   > [!TIP]
   > Un archivo *.tmtheme* define cómo se asignan los ámbitos a las clasificaciones de Visual Studio (denominadas claves de color). Para obtener instrucciones, puede hacer referencia al archivo *.tmtheme* global en el directorio *%ProgramFiles(x86)%-Microsoft Visual Studio\\\<>\\ \<SKU>.*

3. Cree un archivo *.pkgdef* y agregue una línea similar a esta:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Haga clic con el botón derecho en los archivos y seleccione **Propiedades**. Cambie la acción **Generar** a **Contenido** y cambie la propiedad **Incluir en VSIX** a **true**.

Después de completar los pasos anteriores, se agrega una carpeta *Grammars* al directorio install del paquete como un origen de repositorio denominado 'MyLang' ('MyLang' es solo un nombre para la desambiguación y puede ser cualquier cadena única). Todas las gramáticas (archivos *.tmlanguage)* y archivos de tema ( archivos *.tmtheme)* en este directorio se recogen como potenciales y reemplazan a las gramáticas integradas proporcionadas con TextMate. Si las extensiones declaradas del archivo de gramática coinciden con la extensión del archivo que se está queabriendo, TextMate pisará el paso.

## <a name="create-a-simple-language-client"></a>Crear un cliente de lenguaje simple

### <a name="main-interface---ilanguageclient"></a>Interfaz principal - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Después de crear el proyecto VSIX, agregue los siguientes paquetes NuGet al proyecto:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Cuando se toma una dependencia del paquete NuGet después de completar los pasos anteriores, los paquetes Newtonsoft.Json y StreamJsonRpc también se agregan al proyecto. **No actualice estos paquetes a menos que esté seguro de que esas nuevas versiones se instalarán en la versión de Visual Studio a**la que se dirige la extensión. Los ensamblados no se incluirán en su VSIX; en su lugar, se recogerán en el directorio de instalación de Visual Studio. Si hace referencia a una versión más reciente de los ensamblados que a lo que está instalado en el equipo de un usuario, la extensión no funcionará.

A continuación, puede crear una nueva clase que implemente la interfaz [ILanguageClient,](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) que es la interfaz principal necesaria para los clientes de lenguaje que se conectan a un servidor de lenguaje basado en LSP.

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

Los métodos principales que deben implementarse son [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) y [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) se llama cuando Visual Studio ha cargado la extensión y el servidor de idioma está listo para iniciarse. En este método, puede invocar el delegado [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) inmediatamente para indicar que se debe iniciar el servidor de lenguaje, o puede realizar lógica adicional e invocar [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) más adelante. **Para activar el servidor de idioma, debes llamar a StartAsync en algún momento.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) es el método finalmente invocado llamando al delegado [StartAsync.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) Contiene la lógica para iniciar el servidor de lenguaje y establecer conexión con él. Se debe devolver un objeto de conexión que contenga secuencias para escribir en el servidor y leer desde el servidor. Las excepciones que se producen aquí se detectan y se muestran al usuario a través de un mensaje infoBar en Visual Studio.

### <a name="activation"></a>Activación

Una vez implementada la clase de cliente de lenguaje, deberá definir dos atributos para que defina cómo se cargará en Visual Studio y se activará:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio usa [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) para administrar sus puntos de extensibilidad. El [Export](/dotnet/api/system.componentmodel.composition.exportattribute) export atributo indica a Visual Studio que esta clase debe recogerse como un punto de extensión y cargar en el momento adecuado.

Para utilizar MEF, también debe definir MEF como un recurso en el manifiesto VSIX.

Abra el diseñador de manifiestos VSIX y vaya a la pestaña **Activos:**

![añadir activo MEF](media/lsp-add-asset.png)

Haga clic en **Nuevo** para crear un nuevo recurso:

![definir el activo MEF](media/lsp-define-asset.png)

* **Tipo**: Microsoft.VisualStudio.MefComponent
* **Fuente**: Un proyecto en la solución actual
* **Proyecto**: [Su proyecto]

### <a name="content-type-definition"></a>Definición de tipo de contenido

Actualmente, la única manera de cargar la extensión de servidor de lenguaje basada en LSP es por tipo de contenido de archivo. Es decir, al definir la clase de cliente de lenguaje (que implementa [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), deberá definir los tipos de archivos que, cuando se abren, harán que se cargue la extensión. Si no se abre ningún archivo que coincida con el tipo de contenido definido, la extensión no se cargará.

Esto se hace mediante la `ContentTypeDefinition` definición de una o más clases:

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

En el ejemplo anterior, se crea una definición de tipo de contenido para los archivos que terminan en la extensión de archivo *.bar.* La definición de tipo de contenido recibe el nombre "bar" y debe derivar de [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Después de agregar una definición de tipo de contenido, puede definir cuándo cargar la extensión de cliente de idioma en la clase de cliente de idioma:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Agregar compatibilidad con servidores de lenguaje LSP no requiere que implemente su propio sistema de proyecto en Visual Studio. Los clientes pueden abrir un único archivo o una carpeta en Visual Studio para empezar a usar el servicio de lenguaje. De hecho, la compatibilidad con servidores de lenguaje LSP está diseñada para funcionar solo en escenarios de carpetas/archivos abiertos. Si se implementa un sistema de proyecto personalizado, algunas características (como la configuración) no funcionarán.

## <a name="advanced-features"></a>Características avanzadas

### <a name="settings"></a>Configuración

La compatibilidad con la configuración personalizada específica del servidor de idioma está disponible, pero todavía está en proceso de mejora. La configuración es específica de lo que admite el servidor de lenguaje y normalmente controla cómo el servidor de idioma emite los datos. Por ejemplo, un servidor de idioma puede tener una configuración para el número máximo de errores notificados. Los autores de extensiones definirían un valor predeterminado, que los usuarios pueden cambiar para proyectos específicos.

Siga estos pasos para agregar compatibilidad con la configuración a la extensión del servicio de lenguaje LSP:

1. Agregue un archivo JSON (por ejemplo, *MockLanguageExtensionSettings.json*) al proyecto que contenga la configuración y sus valores predeterminados. Por ejemplo:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Haga clic con el botón derecho en el archivo JSON y seleccione **Propiedades**. Cambie la acción **Generar** a "Contenido" y la propiedad "Incluir en VSIX" a **true**.

3. Implemente ConfigurationSections y devuelva la lista de prefijos para la configuración definida en el archivo JSON (en Visual Studio Code, esto se asignaría al nombre de la sección de configuración en package.json):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Agregue un archivo .pkgdef al proyecto (agregue un nuevo archivo de texto y cambie la extensión de archivo a .pkgdef). El archivo pkgdef debe contener esta información:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Sample:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Haga clic con el botón derecho en el archivo .pkgdef y seleccione **Propiedades**. Cambie la acción **Generar** a **Contenido** y la propiedad **Incluir en VSIX** a **true**.

6. Abra el archivo *source.extension.vsixmanifest* y agregue un recurso en la pestaña **Asset:**

   ![editar vspackage asset](media/lsp-add-vspackage-asset.png)

   * **Tipo**: Microsoft.VisualStudio.VsPackage
   * **Fuente**: Archivo en el sistema de archivos
   * **Ruta :**[Ruta de acceso al archivo *.pkgdef]*

### <a name="user-editing-of-settings-for-a-workspace"></a>Edición por parte del usuario de la configuración de un espacio de trabajo

1. El usuario abre un espacio de trabajo que contiene los archivos que posee el servidor.
2. El usuario agrega un archivo en la carpeta *.vs* denominado *VSWorkspaceSettings.json*.
3. El usuario agrega una línea al archivo *VSWorkspaceSettings.json* para una configuración que proporciona el servidor. Por ejemplo:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Habilitar el seguimiento de diagnósticos

El seguimiento de diagnósticos se puede habilitar para generar todos los mensajes entre el cliente y el servidor, lo que puede ser útil al depurar problemas. Para habilitar el seguimiento de diagnóstico, haga lo siguiente:

1. Abra o cree el archivo de configuración del área de trabajo *VSWorkspaceSettings.json* (consulte "Edición de usuario de la configuración de un área de trabajo").
2. Agregue la siguiente línea en el archivo json de configuración:

```json
{
    "foo.trace.server": "Off"
}
```

Hay tres valores posibles para la verbosidad de seguimiento:

* "Off": el rastreo se apagó por completo
* "Messages": seguimiento activado, pero solo se rastrean el nombre del método y el identificador de respuesta.
* "Verbose": seguimiento activado; se rastrea todo el mensaje rpc.

Cuando se activa el seguimiento, el contenido se escribe en un archivo en el directorio *%temp%-VisualStudio-LSP.* El registro sigue el formato de nomenclatura *[LanguageClientName]-[Datetime Stamp].log*. Actualmente, el seguimiento solo se puede habilitar para escenarios de carpetas abiertas. Abrir un único archivo para activar un servidor de lenguaje no tiene compatibilidad con el seguimiento de diagnósticos.

### <a name="custom-messages"></a>Mensajes personalizados

Existen API para facilitar el envío de mensajes y la recepción de mensajes desde el servidor de idioma que no forman parte del protocolo de servidor de idioma estándar. Para controlar los mensajes personalizados, implemente la interfaz [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) en la clase de cliente de lenguaje. La biblioteca [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) se utiliza para transmitir mensajes personalizados entre el cliente de lenguaje y el servidor de lenguaje. Dado que la extensión de cliente de lenguaje LSP es igual que cualquier otra extensión de Visual Studio, puede decidir agregar características adicionales (que no son compatibles con el LSP) a Visual Studio (mediante otras API de Visual Studio) en la extensión a través de mensajes personalizados.

#### <a name="receive-custom-messages"></a>Recibir mensajes personalizados

Para recibir mensajes personalizados desde el servidor de lenguaje, implemente la propiedad [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) en [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) y devuelva un objeto que sepa cómo controlar los mensajes personalizados. Ejemplo a continuación:

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

#### <a name="send-custom-messages"></a>Enviar mensajes personalizados

Para enviar mensajes personalizados al servidor de lenguaje, implemente el método [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) en [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Este método se invoca cuando se inicia el servidor de lenguaje y está listo para recibir mensajes. Un objeto [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) se pasa como parámetro, que puede mantener para enviar mensajes al servidor de lenguaje mediante las API de [VS-StreamJsonRpc.](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) Ejemplo a continuación:

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

### <a name="middle-layer"></a>Capa media

A veces, un desarrollador de extensiones puede interceptar los mensajes LSP enviados y recibidos desde el servidor de lenguaje. Por ejemplo, un desarrollador de extensiones puede modificar el parámetro de mensaje enviado para un mensaje LSP determinado o modificar los resultados devueltos desde el servidor de idioma para una característica LSP (por ejemplo, terminaciones). Cuando sea necesario, los desarrolladores de extensiones pueden usar la API MiddleLayer para interceptar mensajes LSP.

Cada mensaje LSP tiene su propia interfaz de capa media para la interceptación. Para interceptar un mensaje determinado, cree una clase que implemente la interfaz de capa intermedia para ese mensaje. A continuación, implemente la interfaz [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) en la clase de cliente de lenguaje y devuelva una instancia del objeto en la propiedad [MiddleLayer.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) Ejemplo a continuación:

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

La entidad de capa media todavía está en desarrollo y aún no está completa.

## <a name="sample-lsp-language-server-extension"></a>Extensión del servidor de lenguaje LSP de ejemplo

Para ver el código fuente de una extensión de ejemplo mediante la API de cliente LSP en Visual Studio, vea VSSDK-Extensibility-Samples [LSP sample](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Preguntas más frecuentes

**Me gustaría crear un sistema de proyecto personalizado para complementar mi servidor de lenguaje LSP para proporcionar compatibilidad con características más ricas en Visual Studio, ¿cómo puedo hacerlo?**

La compatibilidad con servidores de lenguaje basados en LSP en Visual Studio se basa en la característica de [carpeta abierta](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) y está diseñada para no requerir un sistema de proyecto personalizado. Puede crear su propio sistema de proyecto personalizado siguiendo las instrucciones [aquí,](https://github.com/Microsoft/VSProjectSystem)pero algunas características, como la configuración, pueden no funcionar. La lógica de inicialización predeterminada para los servidores de lenguaje LSP es pasar la ubicación de la carpeta raíz de la carpeta que se está abiertando actualmente, por lo que si utiliza un sistema de proyecto personalizado, es posible que deba proporcionar lógica personalizada durante la inicialización para asegurarse de que el servidor de idioma se puede iniciar correctamente.

**¿Cómo agrego compatibilidad con el depurador?**

Proporcionaremos soporte para el [protocolo de depuración común](https://code.visualstudio.com/docs/extensionAPI/api-debugging) en una versión futura.

**Si ya hay un servicio de lenguaje compatible con VS instalado (por ejemplo, JavaScript), ¿puedo instalar una extensión de servidor de lenguaje LSP que ofrezca características adicionales (como linting)?**

Sí, pero no todas las características funcionarán correctamente. El objetivo final de las extensiones de servidor de lenguaje LSP es habilitar servicios de lenguaje no admitidos de forma nativa por Visual Studio. Puede crear extensiones que ofrezcan compatibilidad adicional mediante servidores de lenguaje LSP, pero algunas características (como IntelliSense) no serán una experiencia fluida. En general, se recomienda utilizar extensiones de servidor de lenguaje LSP para proporcionar nuevas experiencias de idioma, no para extender las existentes.

**¿Dónde publico mi servidor de lenguaje LSP VSIX completado?**

Consulte las instrucciones de Marketplace [aquí](walkthrough-publishing-a-visual-studio-extension.md).

## <a name="see-also"></a>Vea también

- [Agregar compatibilidad con otros lenguajes en el editor de Visual Studio](../ide/adding-visual-studio-editor-support-for-other-languages.md)
