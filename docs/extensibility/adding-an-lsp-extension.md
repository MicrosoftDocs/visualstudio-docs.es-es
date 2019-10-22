---
title: Agregando una extensión de protocolo del servidor de idioma | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d328eb525767205eeedc5781bb93129d5b2eb7f7
ms.sourcegitcommit: 3e74ec49a54e5c3da7631f4466128cdf4384af6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2019
ms.locfileid: "68711248"
---
# <a name="add-a-language-server-protocol-extension"></a>Adición de una extensión del protocolo de servidor de lenguaje

El protocolo de servidor de lenguaje (LSP) es un protocolo común, en forma de JSON RPC v 2.0, que se usa para proporcionar características del servicio de lenguaje a varios editores de código. Mediante el protocolo, los desarrolladores pueden escribir un único servidor de lenguaje para proporcionar características del servicio de lenguaje como IntelliSense, diagnóstico de errores, buscar todas las referencias, etc., a diversos editores de código que admiten el LSP. Tradicionalmente, los servicios de lenguaje de Visual Studio se pueden agregar mediante el uso de archivos de gramática de TextMate para proporcionar funcionalidades básicas como el resaltado de sintaxis o la escritura de servicios de lenguaje personalizados que usan el conjunto completo de API de extensibilidad de Visual Studio para proporcionar datos más completos. Con la compatibilidad de Visual Studio con LSP, hay una tercera opción.

![servicio de protocolo del servidor de lenguaje en Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protocolo de servidor de lenguaje

![implementación del Protocolo de servidor de lenguaje](media/lsp-implementation.png)

En este artículo se describe cómo crear una extensión de Visual Studio que utiliza un servidor de idiomas basado en LSP. Se supone que ya ha desarrollado un servidor de idiomas basado en LSP y solo desea integrarlo en Visual Studio.

Para la compatibilidad con Visual Studio, los servidores de idioma pueden comunicarse con el cliente (Visual Studio) a través de cualquier mecanismo de transmisión basado en secuencias, por ejemplo:

* Flujos de entrada/salida estándar
* Canalizaciones con nombre
* Sockets (solo TCP)

La intención del LSP y del soporte técnico en Visual Studio es incorporar servicios de lenguaje que no formen parte del producto de Visual Studio. No está diseñado para extender los servicios de lenguaje existentes ( C#como) en Visual Studio. Para ampliar los lenguajes existentes, consulte la guía de extensibilidad del servicio de lenguaje (por ejemplo, el [.net Compiler Platform "Roslyn"](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)) o vea [extender el editor y los servicios de lenguaje](../extensibility/extending-the-editor-and-language-services.md).

Para obtener más información sobre el protocolo en sí, consulte la documentación [aquí](https://github.com/Microsoft/language-server-protocol).

Para obtener más información sobre cómo crear un servidor de lenguaje de ejemplo o cómo integrar un servidor de idioma existente en Visual Studio Code, consulte la documentación [aquí](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-supported-features"></a>Características compatibles con el protocolo de servidor de lenguaje

En las tablas siguientes se muestran las características de LSP que se admiten en Visual Studio:

Message | Tiene compatibilidad con Visual Studio
--- | ---
inicia | sí
inicializado | sí
cierre | sí
abandonar | sí
$/cancelRequest | sí
Window/showMessage | sí
window/showMessageRequest | sí
Window/logMessage | sí
telemetría/evento |
client/registerCapability |
cliente/unregisterCapability |
workspace/didChangeConfiguration | sí
workspace/didChangeWatchedFiles | sí
área de trabajo/símbolo | sí
workspace/executeCommand | sí
área de trabajo/applyEdit | sí
textDocument/publishDiagnostics | sí
textDocument/didOpen | sí
textDocument/didChange | sí
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | sí
textDocument/didClose | sí
textDocument/completion | sí
completar o resolver | sí
textDocument/hover | sí
textDocument/signatureHelp | sí
textDocument/references | sí
textDocument/documentHighlight | sí
textDocument/documentSymbol | sí
textDocument/formato | sí
textDocument/rangeFormatting | sí
textDocument/onTypeFormatting |
textDocument/definición | sí
textDocument/codeAction | sí
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolver |
textDocument/rename | sí

## <a name="get-started"></a>Introducción

> [!NOTE]
> A partir de la versión 15,8 de Visual Studio 2017, la compatibilidad con el protocolo de Common Language Server está integrada en Visual Studio. Si ha creado extensiones de LSP mediante la versión de [VSIX del cliente del servidor de idioma](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) de vista previa, dejarán de funcionar una vez que actualice a la versión 15,8 o superior. Tendrá que hacer lo siguiente para que las extensiones de LSP funcionen de nuevo:
>
> 1. Desinstale la versión de vista previa del protocolo del servidor de idioma Microsoft Visual Studio VSIX.
>
>    A partir de la versión 15,8, cada vez que realiza una actualización en Visual Studio, la vista previa de VSIX se detecta y se quita automáticamente.
>
> 2. Actualice la referencia de Nuget a la versión más reciente que no sea de vista previa para los [paquetes de LSP](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Quite la dependencia de la vista previa del protocolo del servidor de lenguaje de Microsoft Visual Studio VSIX en el manifiesto de VSIX.
>
> 4. Asegúrese de que VSIX especifica Visual Studio 2017 versión 15,8 Preview 3 como límite inferior para el destino de instalación.
>
> 5. Vuelva a generar e implementar.

### <a name="create-a-vsix-project"></a>Crear un proyecto VSIX

Para crear una extensión de servicio de lenguaje mediante un servidor de lenguaje basado en LSP, primero asegúrese de que tiene instalada la carga de trabajo **desarrollo de extensión de Visual Studio** para su instancia de vs.

A continuación, cree un nuevo proyecto > de VSIX; para ello, vaya a **archivo** > **nuevo proyecto** > extensión de**visualización C#**   > de proyecto**VSIX**:

![crear Proyecto VSIX](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Instalación del servidor de idioma y del tiempo de ejecución

De forma predeterminada, las extensiones creadas para admitir servidores de idioma basados en LSP en Visual Studio no contienen los propios servidores de idioma o los tiempos de ejecución necesarios para ejecutarlos. Los desarrolladores de extensiones son responsables de la distribución de los servidores de idioma y los tiempos de ejecución necesarios. Hay varias maneras de hacerlo:

* Los servidores de idioma se pueden incrustar en VSIX como archivos de contenido.
* Cree un archivo MSI para instalar el servidor de idioma o los tiempos de ejecución necesarios.
* Proporcione instrucciones sobre Marketplace para informar a los usuarios sobre cómo obtener los tiempos de ejecución y los servidores de idioma.

### <a name="textmate-grammar-files"></a>Archivos de gramática de TextMate

El LSP no incluye especificación sobre cómo proporcionar coloración de texto para los idiomas. Para proporcionar una coloración personalizada para los idiomas de Visual Studio, los desarrolladores de extensiones pueden usar un archivo de gramática de TextMate. Para agregar archivos de tema o gramática TextMate personalizados, siga estos pasos:

1. Cree una carpeta denominada "Grammes" dentro de la extensión (o puede ser cualquier nombre que elija).

2. Dentro de la carpeta de gramáticas, incluya los  *\*archivos. tmLanguage*,  *\*. plist*,  *\*. tmTheme*o  *\*. JSON* que desee que proporcionen coloración personalizada.

   > [!TIP]
   > Un archivo *. tmTheme* define cómo se asignan los ámbitos a las clasificaciones de Visual Studio (claves de color denominadas). Para obtener instrucciones, puede hacer referencia al archivo global *. tmTheme* en la *versión% ProgramFiles (x86)%\\\ Microsoft Visual Studio\\\<>\<SKU > \Common7\IDE\CommonExtensions\Microsoft\ Directorio TextMate\Starterkit\Themesg*

3. Cree un archivo *. pkgdef* y agregue una línea similar a la siguiente:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Haga clic con el botón derecho en los archivos y seleccione **propiedades**. Cambie la acción de **compilación** a **contenido** y cambie la propiedad **incluir en VSIX** a **true**.

Después de completar los pasos anteriores, se agrega una carpeta de gramáticas al directorio de instalación del paquete como un origen de repositorio denominado ' Moreno ' (' Moreno ' es simplemente un nombre para la desambiguación y puede ser cualquier cadena única). Todas las gramáticas (archivos *. tmLanguage* ) y los archivos de tema (archivos *. tmTheme* ) de este directorio se seleccionan como posibles y reemplazan a las gramáticas integradas que se proporcionan con Textmate. Si las extensiones declaradas del archivo de gramática coinciden con la extensión del archivo que se está abriendo, TextMate se devolverá.

## <a name="create-a-simple-language-client"></a>Creación de un cliente de lenguaje simple

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>Interfaz principal: [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Después de crear el Proyecto VSIX, agregue los siguientes paquetes de NuGet al proyecto:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Cuando se toma una dependencia en el paquete NuGet después de completar los pasos anteriores, los paquetes Newtonsoft. JSON y StreamJsonRpc también se agregan al proyecto. **No actualice estos paquetes a menos que esté seguro de que esas nuevas versiones se instalarán en la versión de Visual Studio a la que se destina la extensión**. Los ensamblados no se incluirán en el VSIX; en su lugar, se seleccionarán en el directorio de instalación de Visual Studio. Si hace referencia a una versión más reciente de los ensamblados que la instalada en el equipo de un usuario, la extensión no funcionará.

Después, puede crear una nueva clase que implementa la interfaz [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) , que es la interfaz principal necesaria para que los clientes de idioma se conecten a un servidor de idioma basado en LSP.

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

Los métodos principales que deben implementarse son [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) y [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). Se llama a [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) cuando Visual Studio ha cargado su extensión y el servidor de idioma está listo para iniciarse. En este método, puede invocar el delegado [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) inmediatamente para indicar que se debe iniciar el servidor de idioma, o bien, puede realizar una lógica adicional e invocar [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) más adelante. **Para activar el servidor de idioma, debe llamar a StartAsync en algún momento.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) es el método que finalmente se invoca llamando al delegado [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) . Contiene la lógica para iniciar el servidor de idioma y establecer la conexión con él. Debe devolverse un objeto de conexión que contenga secuencias para escribir en el servidor y leer desde el servidor. Las excepciones que se produzcan aquí se detectarán y se mostrarán al usuario a través de un mensaje de la barra de información en Visual Studio.

### <a name="activation"></a>Activación

Una vez implementada la clase de cliente de lenguaje, deberá definir dos atributos para que defina cómo se cargará en Visual Studio y se activará:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio usa [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) para administrar sus puntos de extensibilidad. El atributo [Export](/dotnet/api/system.componentmodel.composition.exportattribute) indica a Visual Studio que esta clase se debe recoger como punto de extensión y cargarse en el momento adecuado.

Para usar MEF, también debe definir MEF como un recurso en el manifiesto de VSIX.

Abra el diseñador de manifiestos VSIX y navegue hasta la pestaña **activos** :

![Agregar activo MEF](media/lsp-add-asset.png)

Haga clic en **nuevo** para crear un nuevo recurso:

![definir el activo de MEF](media/lsp-define-asset.png)

* **Tipo**: Microsoft.VisualStudio.MefComponent
* **Origen**: Proyecto en la solución actual
* **Proyecto**: [su proyecto]

### <a name="content-type-definition"></a>Definición de tipo de contenido

Actualmente, la única manera de cargar la extensión de servidor de idioma basado en LSP es por tipo de contenido de archivo. Es decir, al definir la clase de cliente de lenguaje (que implementa [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), deberá definir los tipos de archivos que, al abrirse, hará que se cargue la extensión. Si no se abren archivos que coincidan con el tipo de contenido definido, la extensión no se cargará.

Esto se hace a través de la definición `ContentTypeDefinition` de una o varias clases:

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

En el ejemplo anterior, se crea una definición de tipo de contenido para los archivos que finalizan en la extensión de archivo *. bar* . La definición del tipo de contenido recibe el nombre "bar" y debe derivar de [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Después de agregar una definición de tipo de contenido, puede definir cuándo cargar la extensión de cliente de lenguaje en la clase de cliente de lenguaje:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

La adición de compatibilidad con servidores de idiomas de LSP no requiere la implementación de su propio sistema de proyectos en Visual Studio. Los clientes pueden abrir un solo archivo o una carpeta en Visual Studio para empezar a usar el servicio de lenguaje. De hecho, la compatibilidad con los servidores de idiomas de LSP está diseñada para funcionar solo en escenarios de archivo o carpeta abiertos. Si se implementa un sistema de proyectos personalizado, algunas características (como la configuración) no funcionarán.

## <a name="advanced-features"></a>Características avanzadas

### <a name="settings"></a>Configuración

La compatibilidad con la configuración específica del servidor de idioma personalizado está disponible, pero aún está en proceso de mejorar. La configuración es específica de lo que admite el servidor de idioma y normalmente controla el modo en que el servidor de idioma emite los datos. Por ejemplo, un servidor de idioma puede tener un valor para el número máximo de errores que se han comunicado. Los autores de la extensión definirían un valor predeterminado, que los usuarios pueden cambiar para proyectos concretos.

Siga estos pasos para agregar compatibilidad con la configuración de la extensión del servicio de lenguaje LSP:

1. Agregue un archivo JSON (por ejemplo, *MockLanguageExtensionSettings. JSON*) al proyecto que contenga la configuración y sus valores predeterminados. Por ejemplo:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Haga clic con el botón derecho en el archivo JSON y seleccione **propiedades**. Cambie la acción de **compilación** a "contenido" y la propiedad "incluir en VSIX" a **true**.

3. Implemente ConfigurationSections y devuelva la lista de prefijos para los valores definidos en el archivo JSON (en Visual Studio Code, esto se asignaría al nombre de la sección de configuración en package. JSON):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Agregue un archivo. pkgdef al proyecto (agregue un nuevo archivo de texto y cambie la extensión de archivo a. pkgdef). El archivo pkgdef debe contener esta información:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Ejemplo:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Haga clic con el botón derecho en el archivo. pkgdef y seleccione **propiedades**. Cambie la acción de **compilación** a **contenido** y la propiedad **incluir en VSIX** a **true**.

6. Abra el archivo *source. Extension. vsixmanifest* y agregue un recurso en la pestaña **Asset (recurso** ):

   ![editar el recurso de VSPackage](media/lsp-add-vspackage-asset.png)

   * **Tipo**: Microsoft.VisualStudio.VsPackage
   * **Origen**: Archivo en el sistema de archivos
   * **Ruta de acceso**: [ruta de acceso al archivo *. pkgdef* ]

### <a name="user-editing-of-settings-for-a-workspace"></a>Edición del usuario de la configuración de un área de trabajo

1. El usuario abre un área de trabajo que contiene los archivos que posee el servidor.
2. El usuario agrega un archivo en la carpeta *. vs* denominada *VSWorkspaceSettings. JSON*.
3. El usuario agrega una línea al archivo *VSWorkspaceSettings. JSON* para establecer la configuración que proporciona el servidor. Por ejemplo:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Habilitar seguimiento de diagnósticos

El seguimiento de diagnósticos se puede habilitar para mostrar todos los mensajes entre el cliente y el servidor, lo que puede resultar útil al depurar problemas. Para habilitar el seguimiento de diagnóstico, haga lo siguiente:

1. Abra o cree el archivo de configuración del área de trabajo *VSWorkspaceSettings. JSON* (consulte "edición de usuario de la configuración de un área de trabajo").
2. Agregue la siguiente línea en el archivo de configuración JSON:

```json
{
    "foo.trace.server": "Off"
}
```

Hay tres valores posibles para el nivel de detalle del seguimiento:

* "Desactivado": el seguimiento se ha desactivado por completo
* "Mensajes": seguimiento activado, pero solo se realiza un seguimiento del nombre del método y del ID. de respuesta.
* "Verbose": seguimiento activado; se realiza un seguimiento del mensaje RPC completo.

Cuando se activa el seguimiento, el contenido se escribe en un archivo en el directorio *%temp%\VisualStudio\LSP* El registro sigue el formato de nomenclatura *[LanguageClientName]-[DateTime Stamp]. log*. Actualmente, el seguimiento solo se puede habilitar para escenarios de carpeta abierta. Al abrir un único archivo para activar un servidor de idioma, no se admite el seguimiento de diagnósticos.

### <a name="custom-messages"></a>Mensajes personalizados

Existen API para facilitar el paso de mensajes y la recepción de mensajes desde el servidor de idioma que no forman parte del Protocolo de servidor de lenguaje estándar. Para controlar los mensajes personalizados, implemente la interfaz [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) en la clase de cliente de lenguaje. La biblioteca [vs-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) se usa para transmitir mensajes personalizados entre el cliente de lenguaje y el servidor de idioma. Como la extensión de cliente de idioma de LSP es igual que cualquier otra extensión de Visual Studio, puede decidir agregar características adicionales (que no son compatibles con el LSP) a Visual Studio (con otras API de Visual Studio) en la extensión a través de mensajes personalizados.

#### <a name="receive-custom-messages"></a>Recibir mensajes personalizados

Para recibir mensajes personalizados del servidor de idioma, implemente la propiedad [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) en [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) y devuelva un objeto que sepa cómo administrar los mensajes personalizados. Ejemplo siguiente:

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

Para enviar mensajes personalizados al servidor de idioma, implemente el método [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) en [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Este método se invoca cuando se inicia el servidor de idioma y está listo para recibir mensajes. Un objeto [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) se pasa como un parámetro, que puede conservar para enviar mensajes al servidor de idioma mediante las API [vs-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) . Ejemplo siguiente:

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

### <a name="middle-layer"></a>Nivel intermedio

En ocasiones, es posible que un desarrollador de extensiones desee interceptar los mensajes de LSP enviados y recibidos desde el servidor de idioma. Por ejemplo, es posible que un desarrollador de extensiones desee modificar el parámetro de mensaje enviado para un mensaje de LSP determinado o modificar los resultados devueltos desde el servidor de idioma para una característica de LSP (por ejemplo, finalizaciones). Cuando es necesario, los desarrolladores de extensiones pueden usar la API MiddleLayer para interceptar los mensajes de LSP.

Cada mensaje de LSP tiene su propia interfaz de nivel intermedio para la interceptación. Para interceptar un mensaje determinado, cree una clase que implemente la interfaz de capa intermedia para ese mensaje. A continuación, implemente la interfaz [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) en la clase de cliente de lenguaje y devuelva una instancia del objeto en la propiedad [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) . Ejemplo siguiente:

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

La característica de nivel intermedio todavía está en desarrollo y aún no es completa.

## <a name="sample-lsp-language-server-extension"></a>Extensión de servidor de idioma LSP de ejemplo

Para ver el código fuente de una extensión de ejemplo mediante la API de cliente de LSP en Visual Studio, consulte VSSDK-Extensibility-samples [LSP Sample](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Preguntas más frecuentes

**Me gustaría crear un sistema de proyectos personalizado que complemente el servidor de lenguaje de LSP para ofrecer compatibilidad con características más enriquecidas en Visual Studio, ¿cómo puedo hacer esto?**

La compatibilidad con servidores de idioma basados en LSP en Visual Studio se basa en la [característica abrir carpeta](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) y se ha diseñado para que no requiera un sistema de proyecto personalizado. Puede crear su propio sistema de proyecto personalizado siguiendo las instrucciones que se indican [a continuación](https://github.com/Microsoft/VSProjectSystem), pero es posible que algunas características, como la configuración, no funcionen. La lógica de inicialización predeterminada para los servidores de idiomas LSP es pasar a la ubicación de la carpeta raíz de la carpeta que se está abriendo actualmente, por lo que si usa un sistema de proyectos personalizado, es posible que tenga que proporcionar lógica personalizada durante la inicialización para asegurarse de que el servidor de idioma puede iniciar correctamente.

**¿Cómo agregar compatibilidad del depurador?**

Proporcionaremos soporte técnico para el protocolo de depuración [común](https://code.visualstudio.com/docs/extensionAPI/api-debugging) en una versión futura.

**Si ya hay un servicio de lenguaje compatible con VS instalado (por ejemplo, JavaScript), ¿puedo instalar una extensión de servidor de idioma de LSP que ofrezca características adicionales (como la detección de errores)?**

Sí, pero no todas las características funcionarán correctamente. El objetivo final de las extensiones de servidor de idiomas LSP es habilitar los servicios de lenguaje no compatibles de forma nativa con Visual Studio. Puede crear extensiones que ofrecen compatibilidad adicional con servidores de idiomas de LSP, pero algunas características (como IntelliSense) no serán una experiencia fluida. En general, se recomienda usar las extensiones de servidor de idioma de LSP para proporcionar nuevas experiencias de idioma, no para extender las existentes.

**¿Dónde puedo publicar el VSIX del servidor de idioma de LSP completado?**

Vea las instrucciones de Marketplace [aquí](walkthrough-publishing-a-visual-studio-extension.md).

## <a name="see-also"></a>Vea también

- [Agregar compatibilidad con el editor de Visual Studio para otros lenguajes](../ide/adding-visual-studio-editor-support-for-other-languages.md)
