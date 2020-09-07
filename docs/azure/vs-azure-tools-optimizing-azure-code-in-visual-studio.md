---
title: Optimización del código de Azure
description: Obtenga información sobre cómo las herramientas de optimización del código de Azure en Visual Studio ayudan a que el código sea más sólido y tenga un mejor rendimiento.
author: ghogen
manager: jillfra
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 3ee226aac0d705da29333260966781d5b9b627ed
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508462"
---
# <a name="optimizing-your-azure-code"></a>Optimización del código de Azure
Al programar aplicaciones que usan Microsoft Azure, debe seguir algunas prácticas de codificación para evitar problemas en la escalabilidad, el comportamiento y el rendimiento de la aplicación en un entorno en la nube. Microsoft proporciona una herramienta de análisis de código de Azure que reconoce e identifica varios de los problemas que se suelen encontrar y ayuda a resolverlos. Puede descargar la herramienta en Visual Studio a través de NuGet.

## <a name="azure-code-analysis-rules"></a>Reglas de análisis de código de Azure
La herramienta de análisis de código de Azure usa la siguientes reglas para marcar automáticamente su código de Azure cuando encuentra problemas conocidos que influyen en el rendimiento. Los problemas detectados aparecen como advertencias o errores del compilador. Con frecuencia, las correcciones de código o sugerencias para resolver la advertencia o el error se proporcionan con un icono de bombilla.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Evite usar el modo de estado de sesión predeterminado (en proceso)
### <a name="id"></a>Id.
AP0000

### <a name="description"></a>Descripción
Si usa el modo de estado de sesión (en proceso) de forma predeterminada para las aplicaciones de nube, puede perder el estado de sesión.

Comparta sus ideas y comentarios en [Comentarios de análisis de código de Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
De forma predeterminada, el modo de estado de sesión especificado en el archivo web.config es en proceso. Además, si no hay ninguna entrada especificada en el archivo de configuración, el modo de estado de sesión pasa de forma predeterminada a en proceso. El modo en proceso almacena el estado de sesión en memoria en el servidor web. Cuando se reinicia una instancia o se usa una nueva para el equilibrio de carga o para el soporte contra conmutaciones por error, no se guarda el estado de sesión almacenado en memoria en el servidor web. Esta situación impide que la aplicación sea escalable en la nube.

El estado de sesión ASP.NET es compatible con distintas opciones de almacenamiento para los datos de estado de sesión: InProc, StateServer, SQLServer, personalizado y desactivado. Se recomienda usar el modo personalizado para hospedar datos en un almacén de estado de sesión externo, como el [Proveedor de estado de sesión de Azure para Redis](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/).

### <a name="solution"></a>Solución
Una solución recomendada es almacenar el estado de sesión en un servicio de caché administrado. Aprenda a usar el [Proveedor de estado de sesión de Azure para Redis](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/) para almacenar el estado de sesión. También puede almacenar el estado de sesión en otros lugares para garantizar que su aplicación sea escalable en la nube. Para obtener más información acerca de soluciones alternativas, lea [Modos de estado de sesión](/previous-versions/ms178586(v=vs.140)).

## <a name="run-method-should-not-be-async"></a>El método de ejecución no debe ser asincrónico
### <a name="id"></a>Id.
AP1000

### <a name="description"></a>Descripción
Cree métodos asincrónicos (como [await](/dotnet/csharp/language-reference/operators/await)) fuera del método [Run()](/previous-versions/azure/reference/ee772746(v=azure.100)) y luego llame a los métodos asincrónicos desde [Run()](/previous-versions/azure/reference/ee772746(v=azure.100)). Si se declara el método [[Run()](/previous-versions/azure/reference/ee772746(v=azure.100))](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) como asincrónico, el rol de trabajo entra en un bucle de reinicio.

Comparta sus ideas y comentarios en [Comentarios de análisis de código de Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
Si se llama a métodos asincrónicos desde el método [Run()](/previous-versions/azure/reference/ee772746(v=azure.100)) , el tiempo de ejecución del servicio en la nube recicla el rol de trabajo. Cuando se inicia un rol de trabajo, toda la ejecución del programa tiene lugar dentro del método [Run()](/previous-versions/azure/reference/ee772746(v=azure.100)) . Al salir del método Run, el rol de trabajo se reinicia. Cuando el tiempo de ejecución del rol de trabajo alcanza el método asincrónico, distribuye todas las operaciones posteriores al método asincrónico y luego regresa. Esto hace que el rol de trabajo salga del método Run y se reinicie. En la siguiente iteración de la ejecución, el rol de trabajo vuelve a alcanzar el método asincrónico y se reinicia, por lo que el rol de trabajo también se vuelve a reciclar.

### <a name="solution"></a>Solución
Coloque todas las operaciones asincrónicas fuera del método [Run()](/previous-versions/azure/reference/ee772746(v=azure.100)) . A continuación, llame al método asincrónico refactorizado desde dentro del método Run, como RunAsync (). Wait. La herramienta de análisis de código de Azure puede ayudarle a arreglar este problema.

El siguiente fragmento de código muestra la corrección de código para este problema:

```csharp
public override void Run()
{
    RunAsync().Wait();
}

public async Task RunAsync()
{
    //Asynchronous operations code logic
    // This is a sample worker implementation. Replace with your logic.

    Trace.TraceInformation("WorkerRole1 entry point called");

    HttpClient client = new HttpClient();

    Task<string> urlString = client.GetStringAsync("https://msdn.microsoft.com");

    while (true)
    {
        Thread.Sleep(10000);
        Trace.TraceInformation("Working");

        string stream = await urlString;
    }

}
```

## <a name="use-service-bus-shared-access-signature-authentication"></a>Use la autenticación con firma de acceso compartido de Service Bus
### <a name="id"></a>Id.
AP2000

### <a name="description"></a>Descripción
Use SAS (firma de acceso compartido) para la autenticación. El servicio de control de acceso (ACS) se está desusando para la autenticación de Bus de servicio.

Comparta sus ideas y comentarios en [Comentarios de análisis de código de Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
Para mejorar la seguridad, Azure Active Directory está sustituyendo la autenticación ACS por la autenticación SAS. Consulte el blog [Azure Active Directory is the future of ACS](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) (Azure Active Directory es el futuro de ACS) para obtener información sobre el plan de transición.

### <a name="solution"></a>Solución
Use la autenticación SAS en sus aplicaciones. El ejemplo siguiente muestra cómo usar un token SAS para acceder a un espacio de nombres o entidad de Bus de servicio.

```csharp
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Para más información, consulte los temas siguientes.

* Para obtener información general, consulte [Autenticación con firma de acceso compartido en Service Bus](/azure/service-bus-messaging/service-bus-sas)
* [Usar la autenticación con firma de acceso compartido con Service Bus](/azure/service-bus-messaging/service-bus-sas)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>Considere usar el método OnMessage para evitar un "bucle de recepción"
### <a name="id"></a>Id.
AP2002

### <a name="description"></a>Descripción
Para evitar entrar en un "bucle de recepción", la mejor solución para recibir mensajes es llamar al método **OnMessage** en lugar de llamar al método **Receive**. Sin embargo, si debe usar el método **Receive** y especifica un tiempo de espera del servidor no predeterminado, asegúrese de que el tiempo de espera del servidor es superior a un minuto.

Comparta sus ideas y comentarios en [Comentarios de análisis de código de Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
Al llamar a **OnMessage**, el cliente inicia un suministro de mensajes interno que sondea constantemente la cola o la suscripción. Este suministro de mensajes contiene un bucle infinito que emite una llamada para recibir mensajes. Si la llamada agota el tiempo de espera, emite una llamada nueva. El intervalo de tiempo de espera está determinado por el valor de la propiedad [OperationTimeout](/dotnet/api/microsoft.servicebus.messaging.messagingfactorysettings) de [MessagingFactory](/dotnet/api/microsoft.servicebus.messaging.messagingfactory) que se usa.

La ventaja de usar **OnMessage** en comparación con **Receive** es que los usuarios no tienen que sondear en busca de mensajes, controlar excepciones, procesar varios mensajes en paralelo ni completar los mensajes manualmente.

Si llama a **Receive** sin usar su valor predeterminado, asegúrese de que el valor *ServerWaitTime* es superior a un minuto. La configuración de *ServerWaitTime* en un valor superior a un minuto evita que el servidor agote el tiempo de espera antes de que el mensaje se reciba completamente.

### <a name="solution"></a>Solución
Consulte los ejemplos de código siguientes para usos recomendados. Para más detalles, consulte [Método QueueClient.OnMessage (Microsoft.ServiceBus.Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient) y [Método QueueClient.Receive (Microsoft.ServiceBus.Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient).

Para mejorar el rendimiento de la infraestructura de mensajería de Azure, consulte el modelo de diseño [Manual de mensajería asincrónica](/previous-versions/msp-n-p/dn589781(v=pandp.10)).

El siguiente es un ejemplo del uso de **OnMessage** para recibir mensajes.

```csharp
void ReceiveMessages()
{
    // Initialize message pump options.
    OnMessageOptions options = new OnMessageOptions();
    options.AutoComplete = true; // Indicates if the message-pump should call complete on messages after the callback has completed processing.
    options.MaxConcurrentCalls = 1; // Indicates the maximum number of concurrent calls to the callback the pump should initiate.
    options.ExceptionReceived += LogErrors; // Enables you to get notified of any errors encountered by the message pump.

    // Start receiving messages.
    QueueClient client = QueueClient.Create("myQueue");
    client.OnMessage((receivedMessage) => // Initiates the message pump and callback is invoked for each message that is received, calling close on the client will stop the pump.
    {
        // Process the message.
    }, options);
    Console.WriteLine("Press any key to exit.");
    Console.ReadKey();
```

El siguiente es un ejemplo del uso de **Receive** con el tiempo de espera del servidor predeterminado.

```csharp
string connectionString =
CloudConfigurationManager.GetSetting("Microsoft.ServiceBus.ConnectionString");

QueueClient Client =
    QueueClient.CreateFromConnectionString(connectionString, "TestQueue");

while (true)
{
   BrokeredMessage message = Client.Receive();
   if (message != null)
   {
      try
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
```

El siguiente es un ejemplo del uso de **Receive** con un tiempo de espera del servidor no predeterminado.

```csharp
while (true)
{
   BrokeredMessage message = Client.Receive(new TimeSpan(0,1,0));

   if (message != null)
   {
      try
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
}
```

## <a name="consider-using-asynchronous-service-bus-methods"></a>Considere usar los métodos asincrónicos de Service Bus
### <a name="id"></a>Id.
AP2003

### <a name="description"></a>Descripción
Usar métodos asincrónicos de Service Bus para mejorar el rendimiento de la mensajería asíncrona.

Comparta sus ideas y comentarios en [Comentarios de análisis de código de Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
Usar métodos asincrónicos permite la simultaneidad de programas de aplicación porque ejecutar cada llamada no bloquea el subproceso principal. Cuando se usan los métodos de mensajería de Service Bus, realizar una operación (enviar, recibir, eliminar, etc.) lleva tiempo. Este tiempo incluye el procesamiento de la operación por el servicio Service Bus, además de la latencia de la solicitud y la respuesta. Para aumentar el número de operaciones por tiempo, las operaciones deberán ejecutarse simultáneamente. Para más información, consulte [Prácticas recomendadas para mejorar el rendimiento mediante la mensajería asíncrona de Service Bus](/previous-versions/azure/hh528527(v=azure.100)).

### <a name="solution"></a>Solución
Consulte [Clase QueueClient (Microsoft.ServiceBus.Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient) para obtener información sobre cómo usar el método asincrónico recomendado.

Para mejorar el rendimiento de la infraestructura de mensajería de Azure, consulte el modelo de diseño [Manual de mensajería asincrónica](/previous-versions/msp-n-p/dn589781(v=pandp.10)).

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Considere crear particiones de temas y colas de Service Bus
### <a name="id"></a>Id.
AP2004

### <a name="description"></a>Descripción
Partición de temas y colas de Service Bus para mejorar el rendimiento de la mensajería de Service Bus.

Comparta sus ideas y comentarios en [Comentarios de análisis de código de Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
La partición de temas y colas de Service Bus aumenta el rendimiento y la disponibilidad de servicios porque el rendimiento general de una cola o tema particionado ya no está limitado por el rendimiento de un solo agente de mensajes o almacén de mensajería. Además, una interrupción temporal de un almacén de mensajería no hace que una cola o tema particionado deje de estar disponible. Para obtener más información, consulte [Particionamiento de entidades de mensajería](/previous-versions/azure/dn520246(v=azure.100)).

### <a name="solution"></a>Solución
El fragmento de código siguiente muestra cómo crear particiones de las entidades de mensajería.

```csharp
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Para más información, consulte [Partitioned Service Bus Queues and Topics](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) (Temas y colas de Service Bus con particiones) del blog de Microsoft Azure y consulte el ejemplo de [Microsoft Azure Service Bus Partitioned Queue](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) (Cola con particiones de Microsoft Azure Service Bus).

## <a name="do-not-set-sharedaccessstarttime"></a>No establezca SharedAccessStartTime
### <a name="id"></a>Id.
AP3001

### <a name="description"></a>Descripción
Debe evitar el uso de SharedAccessStartTime establecido en la hora actual para iniciar inmediatamente la directiva de acceso compartido. Solo es necesario establecer esta propiedad si quiere iniciar la directiva de acceso compartido en un momento posterior.

Comparta sus ideas y comentarios en [Comentarios de análisis de código de Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
La sincronización de relojes provoca una ligera diferencia de tiempo entre los centros de datos. Por ejemplo, puede pensar que establecer el tiempo de inicio de una directiva SAS de almacenamiento en el tiempo actual mediante DateTime.Now o un método similar hará que la directiva SAS surta efecto inmediatamente. Sin embargo, la ligera diferencia de tiempo entre los distintos centros de datos puede causar problemas, ya que las horas de algunos centros de datos pueden presentar un retraso con respecto al tiempo de inicio, mientras que otros pueden ir adelantados. Como resultado, la directiva SAS puede expirar rápidamente (o incluso inmediatamente) si se establece un tiempo de vida de la directiva muy corto.

Para obtener instrucciones sobre cómo usar la firma de acceso compartido en Azure Storage, consulte [Introducción a SAS (firma de acceso compartido) de tabla, SAS de fila y actualización a SAS de blob - Blog del equipo de Microsoft Azure Storage - Página principal del sitio - Blogs de MSDN](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Solución
Quite la instrucción que establece el tiempo de inicio de la directiva de acceso compartido. La herramienta de análisis de código de Azure proporciona una corrección para este problema. Para obtener más información sobre la administración de seguridad, consulte el modelo de diseño [Patrón de clave valet](/previous-versions/msp-n-p/dn568102(v=pandp.10)).

El siguiente fragmento de código muestra la corrección de código para este problema.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>El tiempo de expiración de la directiva de acceso compartido debe ser superior a cinco minutos.
### <a name="id"></a>Id.
AP3002

### <a name="description"></a>Descripción
Puede haber hasta cinco minutos de diferencia entre los relojes de los centros de datos en diferentes ubicaciones debido a una condición conocida como "desplazamiento del reloj". Para evitar que el token de la directiva de SAS expire antes de lo planeado, establezca el tiempo de expiración en un valor superior a cinco minutos.

Comparta sus ideas y comentarios en [Comentarios de análisis de código de Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
Los centros de datos en diferentes ubicaciones de todo el mundo se sincronizan por una señal de reloj. Dado que la señal de reloj tarda en viajar a ubicaciones diferentes, puede haber una variación de tiempo entre los centros de datos en distintas ubicaciones geográficas aunque supuestamente todo está sincronizado. Esta diferencia de tiempo puede afectar el intervalo expiración y a la hora de inicio de la directiva de acceso compartido. Por lo tanto, para asegurarse de que la directiva de acceso compartido surte efecto inmediatamente, no especifique ninguna hora de inicio. Además, asegúrese de que el tiempo de expiración es superior a 5 minutos para evitar que expire muy pronto.

Para obtener más información acerca de cómo usar la firma de acceso compartido en el almacenamiento de Azure, consulte [Introducción a SAS (firma de acceso compartido) de tabla, SAS de fila y actualización a SAS de blob - Blog del equipo de Microsoft Azure Storage - Página principal del sitio - Blogs de MSDN](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Solución
Para obtener más información sobre la administración de seguridad, consulte el modelo de diseño [Patrón de clave valet](/previous-versions/msp-n-p/dn568102(v=pandp.10)).

El siguiente es un ejemplo de no especificar una hora de inicio a la directiva de acceso compartido.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

El siguiente es un ejemplo de especificar una hora de inicio a la directiva de acceso compartido con una duración de expiración de la directiva superior a los cinco minutos.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
  SharedAccessStartTime = new DateTime(2014,1,20),
 SharedAccessExpiryTime = new DateTime(2014, 1, 21),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Para más información, consulte [Configuración del acceso de lectura público anónimo a contenedores y blobs](/azure/storage/blobs/anonymous-read-access-configure?tabs=portal).

## <a name="use-cloudconfigurationmanager"></a>Use CloudConfigurationManager
### <a name="id"></a>Id.
AP4000

### <a name="description"></a>Descripción
El uso de la clase [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) para proyectos como Sitio web de Azure y Azure Mobile Services no presentará problemas de tiempo de ejecución. Sin embargo, se recomienda usar Cloud[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) como una manera unificada de administración de configuraciones para todas las aplicaciones de nube de Azure.

Comparta sus ideas y comentarios en [Comentarios de análisis de código de Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
CloudConfigurationManager lee el archivo de configuración adecuado para el entorno de aplicación.

[CloudConfigurationManager](/previous-versions/azure/)

### <a name="solution"></a>Solución
Refactorice el código para que use la [Clase CloudConfigurationManager+](/previous-versions/azure/reference/mt634650(v=azure.100)). La herramienta de análisis de código de Azure proporciona una corrección para este problema.

El siguiente fragmento de código muestra la corrección de código para este problema. Replace

`var settings = ConfigurationManager.AppSettings["mySettings"];`

con

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Este es un ejemplo de cómo almacenar la configuración en un archivo App.config o Web.config. Agregue la configuración a la sección appSettings del archivo de configuración. El siguiente es el archivo Web.config para el ejemplo de código anterior.

```xml
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Evite usar cadenas de conexión codificadas de forma rígida
### <a name="id"></a>Id.
AP4001

### <a name="description"></a>Descripción
Si usa las cadenas de conexión codificadas de forma rígida y necesita actualizarlas más adelante, tendrá que realizar cambios en el código fuente y volver a compilar la aplicación. Sin embargo, si almacena las cadenas de conexión en un archivo de configuración, puede cambiarlas más adelante simplemente actualizando el archivo de configuración.

Comparta sus ideas y comentarios en [Comentarios de análisis de código de Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
Codificar las cadenas de conexión de forma rígida es una práctica incorrecta porque presenta problemas cuando las cadenas de conexión deben cambiarse rápidamente. Además, si el proyecto debe protegerse en el control de código fuente, las cadenas de conexión codificadas de forma rígida incorporan vulnerabilidades de seguridad, ya que las cadenas se pueden ver en el código fuente.

### <a name="solution"></a>Solución
Almacene las cadenas de conexión en los archivos de configuración o entornos de Azure.

* Para aplicaciones independientes, use app.config para almacenar la configuración de las cadenas de conexión.
* Para aplicaciones web hospedadas en IIS, use web.config para almacenar cadenas de conexión.
* Para aplicaciones ASP.NET vNext, use configuration.json para almacenar cadenas de conexión.

Para obtener información sobre el uso de archivos de configuración como web.config o app.config, consulte [Directrices de configuración web de ASP.NET](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/web-config-transformations). Para obtener información sobre cómo funcionan las variables de entorno de Azure, consulte [Sitios web Microsoft Azure: cómo funcionan las cadenas de aplicaciones y las cadenas de conexión](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/). Para obtener información sobre cómo almacenar la cadena de conexión en el control de código fuente, consulte [Evitar colocar información confidencial, como cadenas de conexión, en archivos que se almacenan en el repositorio de código fuente.](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control)

## <a name="use-diagnostics-configuration-file"></a>Uso del archivo de configuración de diagnóstico
### <a name="id"></a>Id.
AP5000

### <a name="description"></a>Descripción
En lugar de configurar opciones de diagnóstico en el código como mediante la API de programación de Microsoft.WindowsAzure.Diagnostics, debe configurar las opciones de diagnóstico en el archivo diagnostics.wadcfg. (O bien, diagnostics.wadcfgx si usa Azure SDK 2.5). Al hacer eso, puede cambiar la configuración de diagnóstico sin tener que volver a compilar el código.

Comparta sus ideas y comentarios en [Comentarios de análisis de código de Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
Antes de Azure SDK 2.5 (que usa el diagnóstico de Azure 1.3), Diagnósticos de Azure (WAD) puede configurarse mediante varios métodos diferentes: puede agregarlos al blob de configuración en el almacenamiento, o usar código imperativo, configuración declarativa o la configuración predeterminada. Pero la mejor manera de configurar los diagnósticos es usar un archivo de configuración XML (diagnostics.wadcfg o diagnostics.wadcfgx para SDK 2.5 y versiones posteriores) en el proyecto de aplicación. En este enfoque, el archivo diagnostics.wadcfg define completamente la configuración y se puede actualizar y volver a implementar según se quiera. Si combina el uso del archivo de configuración diagnostics.wadcfg con los métodos de establecimiento de configuraciones mediante programación con las clases [DiagnosticMonitor](/previous-versions/azure/reference/ee758597(v=azure.100)) o [RoleInstanceDiagnosticManager](/previous-versions/azure/reference/ee773157(v=azure.100)) puede crearle confusión. Consulte [Inicializar o cambiar la configuración de Diagnósticos de Azure](/previous-versions/azure/hh411537(v=azure.100)) para obtener más información.

A partir de WAD 1.3 (incluido con Azure SDK 2.5), ya no es posible usar código para configurar los diagnósticos. Como resultado, solo puede proporcionar la configuración al aplicar o actualizar la extensión de diagnósticos.

### <a name="solution"></a>Solución
Use el diseñador de configuración de diagnósticos para mover la configuración de diagnóstico al archivo de configuración de diagnósticos (diagnostics.wadcfg o diagnostics.wadcfgx para SDK 2.5 y versiones posteriores). También se recomienda que instale [Azure SDK 2.5](https://social.msdn.microsoft.com/Forums/en-US/home) y use la característica de diagnóstico más reciente.

1. En el menú contextual del rol que quiere configurar, elija Propiedades, y luego elija la pestaña Configuración.
2. En la sección **Diagnósticos**, asegúrese de que la casilla **Habilitar diagnósticos** está seleccionada.
3. Elija el botón **Configurar**.

   ![Acceso a la opción de habilitar diagnósticos](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Consulte [Configuración de los diagnósticos para Azure Cloud Services y Virtual Machines](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) para obtener más información.

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>Evite declarar objetos DbContext como estáticos
### <a name="id"></a>Id.
AP6000

### <a name="description"></a>Descripción
Para ahorrar memoria, evite declarar objetos DBContext como estáticos.

Comparta sus ideas y comentarios en [Comentarios de análisis de código de Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
Los objetos DBContext contienen los resultados de consulta de cada llamada. Los objetos DBContext estáticos no se eliminan hasta que se descarga el dominio de aplicación. Por lo tanto, un objeto DBContext estático puede consumir grandes cantidades de memoria.

### <a name="solution"></a>Solución
Declare DBContext como un campo de instancia variable o no estático, úselo para una tarea y, luego, deje que se elimine después de usarlo.

El ejemplo siguiente de clase de controlador MVC muestra cómo usar el objeto DBContext.

```csharp
public class BlogsController : Controller
    {
        //BloggingContext is a subclass to DbContext
        private BloggingContext db = new BloggingContext();
        // GET: Blogs
        public ActionResult Index()
        {
            //business logics…
            return View();
        }
        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
```

## <a name="next-steps"></a>Pasos siguientes
Para obtener más información sobre cómo optimizar y solucionar problemas de Azure App Service, consulte [Solución de problemas de una aplicación web en Azure App Service con Visual Studio](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio).
