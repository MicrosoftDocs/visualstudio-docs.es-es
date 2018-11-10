---
title: Optimización del código de Azure en Visual Studio | Microsoft Docs
description: Obtenga información sobre cómo Azure código las herramientas de optimización en Visual Studio ayudan a hacer que el código sea más sólido y tenga un mejor rendimiento.
author: ghogen
manager: douge
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: d1d0f5a69015a6c6596e1a2b7ee85b12f4116d6b
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002516"
---
# <a name="optimizing-your-azure-code"></a>Optimización del código de Azure
Al programar aplicaciones que usan Microsoft Azure, hay algunas prácticas de codificación que deben seguirse para ayudar a evitar problemas con la escalabilidad de la aplicación, el comportamiento y rendimiento en un entorno de nube. Microsoft proporciona una herramienta de análisis de código de Azure que reconoce e identifica varios de estos problemas se suelen encontrar y ayuda a resolverlos. Puede descargar la herramienta en Visual Studio a través de NuGet.

## <a name="azure-code-analysis-rules"></a>Reglas de análisis de código de Azure
La herramienta de análisis de código de Azure usa las siguientes reglas para marcar automáticamente su código de Azure cuando encuentra problemas conocidos que repercuten en el rendimiento. Problemas detectados aparecen como advertencias o errores del compilador. Las correcciones de código o sugerencias para resolver la advertencia o error a menudo se proporcionan a través de un icono de bombilla.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Evite usar el modo de estado de sesión (en proceso) predeterminado
### <a name="id"></a>Id.
AP0000

### <a name="description"></a>Descripción
Si usa el modo de estado de sesión (en proceso) de forma predeterminada para las aplicaciones en la nube, puede perder el estado de sesión.

Comparta sus ideas y comentarios en [comentarios de análisis de código de Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
De forma predeterminada, el modo de estado de sesión especificado en el archivo web.config es en proceso. Además, si ninguna entrada especificada en el archivo de configuración, el modo de estado de sesión de forma predeterminada en el proceso. El modo en proceso almacena el estado de sesión en la memoria en el servidor web. Cuando se reinicia una instancia o se usa una nueva instancia de equilibrio de carga o soporte de conmutación por error, no se guarda el estado de sesión almacenado en memoria en el servidor web. Esta situación impide que la aplicación sea escalable en la nube.

Estado de sesión ASP.NET es compatible con distintas opciones de almacenamiento para datos de estado de sesión: InProc, StateServer, SQLServer, personalizado y Off. Se recomienda que use el modo personalizado para hospedar los datos en un almacén de estado de sesión externo, como [proveedor de estado de sesión de Azure para Redis](http://go.microsoft.com/fwlink/?LinkId=401521).

### <a name="solution"></a>Soluciones
Una solución recomendada consiste en almacenar el estado de sesión en un servicio de caché administrado. Aprenda a usar [proveedor de estado de sesión de Azure para Redis](http://go.microsoft.com/fwlink/?LinkId=401521) para almacenar el estado de sesión. También puede almacenar el estado de sesión en otros lugares para garantizar que su aplicación sea escalable en la nube. Para obtener más información sobre soluciones alternativas, lea [modos de estado de sesión](https://msdn.microsoft.com/library/ms178586).

## <a name="run-method-should-not-be-async"></a>Método de ejecución no debe ser asincrónico
### <a name="id"></a>Id.
AP1000

### <a name="description"></a>Descripción
Cree métodos asincrónicos (como [await](https://msdn.microsoft.com/library/hh156528.aspx)) fuera de la [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) método y, a continuación, llame a los métodos asincrónicos desde [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx). Declarar el [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) método como asincrónico hace que el rol de trabajo escribir un bucle de reinicio.

Comparta sus ideas y comentarios en [comentarios de análisis de código de Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Llamar a métodos asincrónicos desde el [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) método hace que el runtime del servicio en la nube recicla el rol de trabajo. Cuando se inicia un rol de trabajo, toda la ejecución del programa tiene lugar dentro de la [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) método. Cerrando el [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) método hace que el rol de trabajo se reinicia. Cuando el tiempo de ejecución del rol de trabajo alcanza el método asincrónico, distribuye todas las operaciones posteriores al método asincrónico y, a continuación, se devuelve. Esto hace que el rol de trabajo salir de la [ [ [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) método y el reinicio. En la siguiente iteración de la ejecución, el rol de trabajo alcanza el método asincrónico nuevo y se reinicia, haciendo que el rol de trabajo también se vuelve de reciclaje.

### <a name="solution"></a>Soluciones
Coloque todas las operaciones asincrónicas fuera de la [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) método. A continuación, llame al método asincrónico refactorizado desde dentro de la [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) método, como RunAsync () .wait. La herramienta de análisis de código de Azure puede ayudarle a solucionar este problema.

El fragmento de código siguiente muestra la corrección de código para este problema:

```
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

    Task<string> urlString = client.GetStringAsync("http://msdn.microsoft.com");

    while (true)
    {
        Thread.Sleep(10000);
        Trace.TraceInformation("Working");

        string stream = await urlString;
    }

}
```

## <a name="use-service-bus-shared-access-signature-authentication"></a>Usar la autenticación de firma de acceso compartido de Service Bus
### <a name="id"></a>Id.
AP2000

### <a name="description"></a>Descripción
Utilice la firma de acceso compartido (SAS) para la autenticación. Access Control Service (ACS) está en desuso para la autenticación de bus de servicio.

Comparta sus ideas y comentarios en [comentarios de análisis de código de Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Para mejorar la seguridad, Azure Active Directory está sustituyendo la autenticación ACS con la autenticación de SAS. Consulte [Azure Active Directory es el futuro de ACS](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) para obtener información sobre el plan de transición.

### <a name="solution"></a>Soluciones
Usar autenticación de SAS en sus aplicaciones. El ejemplo siguiente muestra cómo usar un token SAS para acceder a un espacio de nombres de bus de servicio o la entidad.

```
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Vea los temas siguientes para obtener más información.

* Para obtener información general, consulte [autenticación de firma de acceso compartido con Service Bus](https://msdn.microsoft.com/library/dn170477.aspx)
* [Cómo usar la autenticación de firma de acceso compartido con Service Bus](https://msdn.microsoft.com/library/dn205161.aspx)
* Para un proyecto de ejemplo, vea [autenticación de uso de firma de acceso compartido (SAS) con suscripciones de Service Bus](http://code.msdn.microsoft.com/windowsazure/Using-Shared-Access-e605b37c)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>Considere la posibilidad de usar el método OnMessage para evitar "bucle de recepción"
### <a name="id"></a>Id.
AP2002

### <a name="description"></a>Descripción
Para evitar entrar en un "bucle de recepción," llamar a la **OnMessage** método es una mejor solución para recibir los mensajes que llamar a la **recepción** método. Sin embargo, si debe utilizar el **recepción** método y especificar un tiempo de espera del servidor no predeterminado, asegúrese de que el tiempo de espera del servidor es más de un minuto.

Comparta sus ideas y comentarios en [comentarios de análisis de código de Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Al llamar a **OnMessage**, el cliente inicia un suministro de mensajes interno que sondea constantemente la cola o suscripción. Este suministro de mensajes contiene un bucle infinito que emite una llamada para recibir mensajes. Si la llamada agota el tiempo de espera, emite una llamada nueva. El intervalo de tiempo de espera está determinado por el valor de la [OperationTimeout](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactorysettings.operationtimeout.aspx) propiedad de la [MessagingFactory](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactory.aspx)que se utiliza.

La ventaja de usar **OnMessage** en comparación con **recepción** es que los usuarios no tienen que sondear en busca de mensajes, controlar las excepciones, procesar varios mensajes en paralelo y completar los mensajes manualmente.

Si se llama a **recepción** sin utilizar su valor predeterminado, asegúrese del *ServerWaitTime* valor es más de un minuto. Establecer *ServerWaitTime* a más de un minuto evita que el servidor de tiempo de espera antes de que el mensaje se reciba completamente.

### <a name="solution"></a>Soluciones
Consulte los siguientes ejemplos de código para usos recomendados. Para obtener más información, consulte [método QueueClient.OnMessage (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.onmessage.aspx)y [método QueueClient.Receive (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.receive.aspx).

Para mejorar el rendimiento de la infraestructura de mensajería de Azure, vea el patrón de diseño [manual de mensajería asincrónica](https://msdn.microsoft.com/library/dn589781.aspx).

El siguiente es un ejemplo del uso de **OnMessage** para recibir mensajes.

```
void ReceiveMessages()
{
    // Initialize message pump options.
    OnMessageOptions options = new OnMessageOptions();
    options.AutoComplete = true; // Indicates if the message-pump should call complete on messages after the callback has completed processing.
    options.MaxConcurrentCalls = 1; // Indicates the maximum number of concurrent calls to the callback the pump should initiate.
    options.ExceptionReceived += LogErrors; // Enables you to get notified of any errors encountered by the message pump.

    // Start receiving messages.
    QueueClient client = QueueClient.Create("myQueue");
    client.OnMessage((receivedMessage) => // Initiates the message pump and callback is invoked for each message that is recieved, calling close on the client will stop the pump.
    {
        // Process the message.
    }, options);
    Console.WriteLine("Press any key to exit.");
    Console.ReadKey();
```

El siguiente es un ejemplo del uso de **recepción** con el servidor de forma predeterminada el tiempo de espera.

```
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

El siguiente es un ejemplo del uso de **recepción** con un servidor no predeterminado de tiempo de espera.

```
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
## <a name="consider-using-asynchronous-service-bus-methods"></a>Considere la posibilidad de usar métodos asincrónicos de Service Bus
### <a name="id"></a>Id.
AP2003

### <a name="description"></a>Descripción
Utilice los métodos asincrónicos de Service Bus para mejorar el rendimiento con la mensajería asíncrona.

Comparta sus ideas y comentarios en [comentarios de análisis de código de Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Usar métodos asincrónicos permite la simultaneidad de programas de aplicación porque ejecutar cada llamada no bloquea el subproceso principal. Cuando se usa Service Bus, los métodos de mensajería, realizar una operación (enviar, recibir, eliminar, etc.) lleva tiempo. Este tiempo incluye el procesamiento de la operación por el servicio de Service Bus, además de la latencia de la solicitud y la respuesta. Para aumentar el número de operaciones por tiempo, las operaciones deberán ejecutarse simultáneamente. Para obtener más información, consulte [procedimientos recomendados para rendimiento mejoras de uso de Service Bus Brokered Messaging](https://msdn.microsoft.com/library/azure/hh528527.aspx).

### <a name="solution"></a>Soluciones
Consulte [clase QueueClient (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.aspx) para obtener información sobre cómo usar el método asincrónico recomendado.

Para mejorar el rendimiento de la infraestructura de mensajería de Azure, vea el patrón de diseño [manual de mensajería asincrónica](https://msdn.microsoft.com/library/dn589781.aspx).

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Considere la posibilidad de partición de temas y colas de Service Bus
### <a name="id"></a>Id.
AP2004

### <a name="description"></a>Descripción
Partición de colas de Service Bus y temas para mejorar el rendimiento con la mensajería de Service Bus.

Comparta sus ideas y comentarios en [comentarios de análisis de código de Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
La partición de temas y colas de Service Bus aumenta la disponibilidad de rendimiento y el servicio de rendimiento porque el rendimiento general de una cola o tema particionado ya no está limitado por el rendimiento de un solo agente o almacén de mensajería. Además, una interrupción temporal de un almacén de mensajería no hace que una cola o tema particionado no está disponible. Para obtener más información, consulte [particionamiento de entidades de mensajería](https://msdn.microsoft.com/library/azure/dn520246.aspx).

### <a name="solution"></a>Soluciones
El fragmento de código siguiente muestra cómo crear particiones de las entidades de mensajería.

```
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Para obtener más información, consulte [temas y colas con particiones de Service Bus | Blog de Microsoft Azure](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) y eche un vistazo el [cola con particiones de Microsoft Azure Service Bus](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) ejemplo.

## <a name="do-not-set-sharedaccessstarttime"></a>No establezca SharedAccessStartTime
### <a name="id"></a>Id.
AP3001

### <a name="description"></a>Descripción
Debe evitar el uso de sharedaccessstarttime establecido en la hora actual para iniciar inmediatamente la directiva de acceso compartido. Solo necesita establecer esta propiedad si desea iniciar la directiva de acceso compartido en un momento posterior.

Comparta sus ideas y comentarios en [comentarios de análisis de código de Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Sincronización de relojes provoca una ligera diferencia de tiempo entre los centros de datos. Por ejemplo, pensar que establecer la hora de inicio de una directiva SAS de almacenamiento de la hora actual mediante DateTime.Now o un método similar hará que la directiva SAS surta efecto inmediatamente. Sin embargo, la ligera diferencia de tiempo entre los centros de datos puede causar problemas con esto ya que algunas veces del centro de datos podrían ser ligeramente posteriores a la hora de inicio, mientras que otros por delante de él. Como resultado, la directiva SAS puede expirar rápidamente (o incluso inmediatamente) si la duración de la directiva se establece demasiado corta.

Para obtener instrucciones sobre cómo usar la firma de acceso compartido en almacenamiento de Azure, consulte [presentación de tabla SAS (firma de acceso compartido), SAS de cola y actualización a SAS de Blob - Blog del equipo de almacenamiento de Microsoft Azure - inicio - sitio Blogs de MSDN](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx).

### <a name="solution"></a>Soluciones
Quite la instrucción que establece la hora de inicio de la directiva de acceso compartido. La herramienta de análisis de código de Azure proporciona una corrección para este problema. Para obtener más información sobre la administración de seguridad, consulte el patrón de diseño [patrón Valet Key](https://msdn.microsoft.com/library/dn568102.aspx).

El fragmento de código siguiente muestra la corrección de código para este problema.

```
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

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>Hora de expiración debe ser más de cinco minutos de directiva de acceso compartido
### <a name="id"></a>Id.
AP3002

### <a name="description"></a>Descripción
Puede haber como cinco minutos de diferencia en los relojes entre los centros de datos en diferentes ubicaciones debido a una condición conocida como "sesgo de reloj." Para evitar que la SAS token directiva expire antes de lo planeado, establezca la hora de expiración en más de cinco minutos.

Comparta sus ideas y comentarios en [comentarios de análisis de código de Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Los centros de datos en diferentes ubicaciones en todo el mundo para sincronizar una señal de reloj. Dado que se tarda tiempo señal de reloj en viajar a ubicaciones diferentes, puede haber una variación de tiempo entre los centros de datos en distintas ubicaciones geográficas aunque supuestamente todo está sincronizado. Esta diferencia de tiempo puede afectar el intervalo de tiempo y la expiración del inicio de directivas de acceso compartido. Por lo tanto, para asegurarse de que la directiva de acceso compartido surte efecto inmediatamente, no especifique la hora de inicio. Además, asegúrese de que la hora de expiración es más de 5 minutos para evitar que expire muy pronto.

Para obtener más información sobre el uso de firma de acceso compartido en Azure storage, consulte [presentación de tabla SAS (firma de acceso compartido), SAS de cola y actualización a SAS de Blob - Blog del equipo de almacenamiento de Microsoft Azure - inicio - sitio Blogs de MSDN](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx).

### <a name="solution"></a>Soluciones
Para obtener más información sobre la administración de seguridad, consulte el patrón de diseño [patrón Valet Key](https://msdn.microsoft.com/library/dn568102.aspx).

El siguiente es un ejemplo de no especificar una hora de inicio de la directiva de acceso compartido.

```
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

El siguiente es un ejemplo de especificar una hora de inicio de la directiva de acceso compartido con una duración de expiración de la directiva superior a cinco minutos.

```
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

Para obtener más información, consulte [crear y usar una firma de acceso compartido](https://msdn.microsoft.com/library/azure/jj721951.aspx).

## <a name="use-cloudconfigurationmanager"></a>Usar CloudConfigurationManager
### <a name="id"></a>Id.
AP4000

### <a name="description"></a>Descripción
Mediante el [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) clase para los proyectos como sitio Web de Azure y Azure mobile services no presentan problemas de tiempo de ejecución. Como práctica recomendada, sin embargo, es una buena idea usar en la nube[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) como una manera unificada de administración de configuraciones para todas las aplicaciones de nube de Azure.

Comparta sus ideas y comentarios en [comentarios de análisis de código de Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
CloudConfigurationManager lee el archivo de configuración adecuado para el entorno de aplicación.

[CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)

### <a name="solution"></a>Soluciones
Refactorizar el código para usar el [CloudConfigurationManager Class](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx). La herramienta de análisis de código de Azure proporciona una corrección de código para este problema.

El fragmento de código siguiente muestra la corrección de código para este problema. Reemplazar

`var settings = ConfigurationManager.AppSettings["mySettings"];`

with

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Este es un ejemplo de cómo almacenar el valor de configuración en un archivo App.config o Web.config. Agregue la configuración a la sección appSettings del archivo de configuración. Este es el archivo Web.config de ejemplo de código anterior.

```
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>  
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Evite el uso de las cadenas de conexión codificadas de forma rígida
### <a name="id"></a>Id.
AP4001

### <a name="description"></a>Descripción
Si utiliza las cadenas de conexión codificadas de forma rígida y necesita actualizarlas más adelante, tendrá que realizar cambios en el código fuente y volver a compilar la aplicación. Sin embargo, si almacena las cadenas de conexión en un archivo de configuración, puede cambiarlas más adelante simplemente actualizando el archivo de configuración.

Comparta sus ideas y comentarios en [comentarios de análisis de código de Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
De forma rígida las cadenas de conexión es una práctica incorrecta porque presenta problemas cuando las cadenas de conexión deben cambiarse rápidamente. Además, si el proyecto debe activarse en el control de código fuente, las cadenas de conexión codificadas de forma rígida incorporan vulnerabilidades de seguridad ya que las cadenas se pueden ver en el código fuente.

### <a name="solution"></a>Soluciones
Store las cadenas de conexión en los archivos de configuración o entornos de Azure.

* Las aplicaciones independientes, use app.config para almacenar la configuración de la cadena de conexión.
* Para las aplicaciones web hospedadas en IIS, use web.config para almacenar cadenas de conexión.
* Para las aplicaciones de ASP.NET vNext, use configuration.json para almacenar cadenas de conexión.

Para obtener información sobre el uso de archivos de configuración como web.config o app.config, consulte [directrices de configuración de ASP.NET Web](https://msdn.microsoft.com/library/vstudio/ff400235\(v=vs.100\).aspx). Para obtener información sobre cómo Azure funcionan las variables de entorno, consulte [sitios Web de Azure: How Application Strings y cadenas de conexión funciona](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/). Para obtener información sobre cómo almacenar la cadena de conexión de control de código fuente, vea [evitar colocar información confidencial como cadenas de conexión en archivos que se almacenan en el repositorio de código fuente](http://www.asp.net/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Archivo de configuración de diagnósticos de uso
### <a name="id"></a>Id.
AP5000

### <a name="description"></a>Descripción
En lugar de configurar la configuración de diagnóstico en el código como mediante el uso de la API de programación de Microsoft.WindowsAzure.Diagnostics, debe configurar la configuración de diagnóstico en el archivo diagnostics.wadcfg. (O bien, diagnostics.wadcfgx si usa Azure SDK 2.5). Al hacerlo, puede cambiar la configuración de diagnóstico sin tener que volver a compilar el código.

Comparta sus ideas y comentarios en [comentarios de análisis de código de Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Antes de Azure SDK 2.5 (que utiliza diagnósticos de Azure 1.3), Azure Diagnostics (WAD) puede configurarse mediante varios métodos diferentes: adición al blob de configuración en el almacenamiento, utilizando código imperativo, configuración declarativa o el valor predeterminado configuración. Sin embargo, la mejor manera de configurar los diagnósticos es usar un archivo de configuración XML (diagnostics.wadcfg o diagnositcs.wadcfgx para SDK 2.5 y versiones posteriores) en el proyecto de aplicación. En este enfoque, el archivo diagnostics.wadcfg completamente define la configuración y puede actualizar y volver a implementar a voluntad. Si combina el uso del archivo de configuración diagnostics.wadcfg con los métodos de establecimiento de configuraciones mediante programación el [DiagnosticMonitor](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.diagnosticmonitor.aspx)o [RoleInstanceDiagnosticManager](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.management.roleinstancediagnosticmanager.aspx)las clases pueden llevar a confusión. Consulte [inicializar o cambiar la configuración de diagnósticos de Azure](https://msdn.microsoft.com/library/azure/hh411537.aspx) para obtener más información.

A partir de WAD 1.3 (incluido con Azure SDK 2.5), ya no es posible usar código para configurar los diagnósticos. Como resultado, solo puede proporcionar la configuración al aplicar o actualizar la extensión de diagnósticos.

### <a name="solution"></a>Soluciones
Use el Diseñador de configuración de diagnósticos para mover la configuración de diagnóstico al archivo de configuración de diagnósticos (diagnositcs.wadcfg o diagnositcs.wadcfgx para SDK 2.5 y versiones posteriores). También se recomienda que instale [Azure SDK 2.5](http://go.microsoft.com/fwlink/?LinkId=513188) y usar la característica de diagnóstico más reciente.

1. En el menú contextual para el rol que desea configurar, elija Propiedades y, a continuación, seleccione la ficha configuración.
2. En el **diagnósticos** sección, asegúrese de que el **habilitar diagnósticos** casilla está activada.
3. Elija la **configurar** botón.

   ![Obtener acceso a la opción Habilitar diagnósticos](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Consulte [configurar diagnósticos para Azure Cloud Services y Virtual Machines](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) para obtener más información.

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>Evite declarar objetos DbContext como estáticos
### <a name="id"></a>Id.
AP6000

### <a name="description"></a>Descripción
Para ahorrar memoria, evite declarar objetos DBContext como estáticos.

Comparta sus ideas y comentarios en [comentarios de análisis de código de Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Los objetos DBContext contienen los resultados de consulta de cada llamada. Los objetos DBContext estáticos no se eliminan hasta que se descarga el dominio de aplicación. Por lo tanto, un objeto DBContext estático puede consumir grandes cantidades de memoria.

### <a name="solution"></a>Soluciones
Declare DBContext como una variable local o un campo de instancia no estático, úselo para una tarea y, a continuación, deje que se elimine de tras su uso.

La clase de controlador MVC de ejemplo siguiente muestra cómo usar el objeto DBContext.

```
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
Para obtener más información sobre la optimización y solución de problemas de aplicaciones de Azure, consulte [solucionar problemas de una aplicación web en Azure App Service mediante Visual Studio](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio).
