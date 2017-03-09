---
title: "Windows Communication Foundation Services and WCF Data Services in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services, WCF Data"
  - "WCF services, binding to"
  - "WCF services, asynchronous service methods"
  - "service references [Visual Studio]"
  - "WCF Data Services"
  - "asynchronous calls"
  - "service references [Visual Studio], type sharing"
  - "endpoints [WCF]"
  - "asynchronous service methods"
  - "service references [Visual Studio] endpoints"
  - "WCF services, type sharing"
  - "Windows Communication Foundation, in Visual Studio"
  - "services, WCF"
  - "WCF service, Visual Studio"
  - "data services, WCF"
  - "services, in Visual Studio"
  - "data binding [Visual Studio], WCF"
  - "service endpoints [Visual Studio]"
  - "service references [Visual Studio], asynchronous calls"
  - "services, Windows Communication Foundation"
  - "type sharing in WCF services"
  - "WCF services, endpoints"
  - "service method, called asynchronously[Visual Studio]"
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: 26
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Communication Foundation Services and WCF Data Services in Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 2008 proporciona las herramientas necesarias para trabajar con Windows Communication Foundation \(WCF\) y [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], tecnologías de Microsoft para crear aplicaciones distribuidas.  En este tema se proporciona una introducción a los servicios desde una perspectiva de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## ¿Qué es WCF?  
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] es un marco de trabajo unificado para crear aplicaciones distribuidas seguras, confiables, interoperables y por transacción.  En versiones anteriores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], era posible la comunicación entre aplicaciones gracias a la existencia de varias tecnologías.  
  
 Para compartir información de tal forma que se pudiera tener acceso a ella desde cualquier plataforma, se usaría un servicio Web \(también conocido como servicio Web ASMX\).  Para mover simplemente datos entre un cliente y servidor que se ejecutaban en el sistema operativo Windows, se usaría .NET Remoting.  Para realizar comunicaciones por transacción, se usaría Enterprise Services \(DCOM\) o para un modelo en cola, se usaría Microsoft Message Queuing \(también conocido como MSMQ\).  
  
 WCF reúne la funcionalidad de todas esas tecnologías bajo un modelo de programación unificado.  Así se simplifica la experiencia de desarrollar aplicaciones distribuidas.  
  
#### Qué son los Servicios de datos de WCF  
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] son servicios que interactúan directamente con una base de datos, permitiendo devolver datos mediante el uso de verbos HTTP estándar como GET, POST, PUT o DELETE.  En general, [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] es una buena opción para las aplicaciones que se utilizan para crear, actualizar o eliminar registros en una base de datos.  Para obtener más información, vea .  
  
### Modelo de programación de WCF  
 El modelo de programación de WCF está basado en la comunicación entre dos entidades: un servicio WCF y un cliente WCF.  El modelo de programación se encapsula en el espacio de nombres <xref:System.ServiceModel> de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
#### WCF Service  
 Un servicio WCF está basado en una interfaz que define un contrato entre el servicio y el cliente.  Está marcado con un atributo <xref:System.ServiceModel.ServiceContractAttribute>, como se muestra en el siguiente código:  
  
 [!code-cs[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]  
  
 [!code-cs[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]  
  
 Defina las funciones o métodos expuestos por un servicio WCF y márquelos con un atributo <xref:System.ServiceModel.OperationContractAttribute>.  Además, puede exponer los datos serializados marcando un tipo compuesto con un atributo <xref:System.Runtime.Serialization.DataContractAttribute>.  Esto habilita el enlace de datos en un cliente.  
  
 Después de definir una interfaz y sus métodos, se encapsulan en una clase que implementa la interfaz.  Una clase de servicio WCF única puede implementar varios contratos de servicio.  
  
 Un servicio WCF se expone para el consumo a través de lo que se conoce como *punto final*.  El punto final proporciona la única manera de comunicación con el servicio; no puede tener acceso al servicio a través de una referencia directa como lo haría con otras clases.  
  
 Un punto final está compuesto de una dirección, un enlace y un contrato.  La dirección define la ubicación del servicio; ésta podría ser una dirección URL, una dirección FTP o una ruta de acceso local o de red.  Un enlace define la manera de establecer comunicación con el servicio.  Los enlaces de WCF proporcionan un modelo versátil para especificar un protocolo como HTTP o FTP, un mecanismo de seguridad como autenticación de Windows o nombres de usuario y contraseñas, y mucho más.  Un contrato incluye las operaciones expuestas por la clase de servicio WCF.  
  
 Se pueden exponer varios puntos finales para un servicio WCF único.  Esto permite a distintos clientes establecer comunicación con el mismo servicio de varias maneras.  Por ejemplo, un servicio bancario podría proporcionar un punto final para empleados y otro para los clientes, cada uno mediante una dirección, enlace y\/o contrato diferentes.  
  
#### Cliente WCF  
 Un cliente WCF está compuesto de un *proxy* que habilita a una aplicación para poder establecer comunicación con un servicio WCF y un punto final que coincide con un punto final definido para el servicio.  El proxy se genera en el cliente en el archivo app.config e incluye información sobre los tipos y métodos expuestos por el servicio.  Para los servicios que exponen varios puntos finales, el cliente puede seleccionar el que mejor se ajuste a sus necesidades, por ejemplo, para establecer una comunicación a través de HTTP y usar la autenticación de Windows.  
  
 Una vez creado un cliente WCF, haga referencia al servicio en el código tal y como lo haría con cualquier otro objeto.  Por ejemplo, para llamar al método `GetData` mostrado anteriormente, debería escribir un código similar al siguiente:  
  
 [!code-cs[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]  
  
## Herramientas WCF en Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 2008 proporciona las herramientas de ayuda necesarias para crear tanto servicios WCF como clientes WCF.  Para obtener un tutorial donde se muestran las herramientas, vea [Walkthrough: Creating and Accessing WCF Services](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).  
  
### Crear y probar servicios WCF  
 Puede usar las plantillas WCF de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como un fundamento para crear su propio servicio rápidamente.  A continuación, puede usar el Host de servicio WCF y el Cliente de prueba WCF para depurar y probar el servicio.  Estas herramientas juntas proporcionan tanto una depuración como un ciclo de prueba rápido y conveniente, además de eliminar el requisito de confirmación de un modelo de hospedaje en una fase temprana.  
  
#### Plantillas WCF  
 Las plantillas WCF de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporcionan una estructura de clase básica para el desarrollo del servicio.  Hay varias plantillas WCF disponibles en el cuadro de diálogo **Agregar nuevo proyecto**.  Éstas incluyen proyectos de biblioteca de servicios WCF, sitios web de servicios WCF y plantillas de elemento de servicios WCF.  
  
 Al seleccionar una plantilla, se agregan los archivos para un contrato de servicios, una implementación del servicio y una configuración de servicio.  Ya se han agregado los atributos necesarios y se ha creado un tipo de servicio sencillo "Hello World", y no tiene que escribir ningún código.  Por supuesto, quizá desee agregar código que proporcione funciones y métodos a su servicio en un escenario real, pero las plantillas proporcionan el fundamento básico.  
  
 Para obtener más información sobre las plantillas WCF, vea [Plantillas de Visual Studio para WCF](../Topic/WCF%20Visual%20Studio%20Templates.md)..  
  
#### Host de servicio WCF  
 Al iniciar el depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(presionando F5\) para un proyecto del servicio WCF, se inicia automáticamente la herramienta Host de servicio WCF para hospedar el servicio de forma local.  El Host de servicio WCF enumera los servicios en un proyecto del servicio WCF, carga la configuración del proyecto y crea instancias de un host para cada servicio que encuentra.  
  
 Mediante el Host de servicio WCF, puede probar un servicio WCF sin tener que escribir código adicional o confirmar a un host concreto durante el desarrollo.  
  
 Para obtener más información sobre el Host de servicio WCF, vea [Host de servicio WCF \(WcfSvcHost.exe\)](../Topic/WCF%20Service%20Host%20\(WcfSvcHost.exe\).md).  
  
#### Cliente de prueba WCF  
 La herramienta Cliente de prueba WCF le permite incluir parámetros de pruebas, enviar esos parámetros a un servicio WCF y ver la respuesta que devuelve el servicio.  Proporciona una experiencia de pruebas de servicios adecuada al combinarla con el Host de servicio WCF.  
  
 Al presionar F5 para depurar un proyecto de servicio WCF, se abre el Cliente de prueba WCF y muestra una lista de los puntos finales de servicios definidos en el archivo de configuración.  Puede probar los parámetros e iniciar el servicio, y repetir este proceso para probar y validar continuamente su servicio.  
  
 Para obtener más información sobre el Cliente de prueba WCF, vea [Cliente de prueba de WCF \(WcfTestClient.exe\)](../Topic/WCF%20Test%20Client%20\(WcfTestClient.exe\).md).  
  
### Obtener acceso a los servicios WCF en Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] simplifica la tarea de crear clientes WCF, ya que genera automáticamente un proxy y un punto final para los servicios que se agregan mediante el cuadro de diálogo **Agregar referencia de servicio** .  Toda la información de configuración necesaria se agrega al archivo app.config. En la mayoría de los casos, lo único que debe hacer es crear una instancia del servicio para utilizarlo.  
  
 El cuadro de diálogo **Agregar referencia de servicio** le permite escribir la dirección de un servicio o buscar un servicio definido en la solución.  El cuadro de diálogo devuelve una lista de los servicios y las operaciones proporcionadas por esos servicios.  También le permite definir el espacio de nombres por el que se referirá a los servicios en el código.  
  
 El cuadro de diálogo **Configurar referencia de servicio** le permite personalizar la configuración para un servicio.  Puede cambiar la dirección de un servicio, especificar el nivel de acceso, el comportamiento asincrónico y los tipos de contrato de mensaje, y volver a usar el tipo de configuración.  
  
## Cómo: Seleccione un extremo de Servicio  
 Algunos servicios de Windows Communication Foundation \(WCF\) exponen varios extremos a través de los que un cliente puede comunicarse con el servicio.  Por ejemplo, un servicio puede exponer un extremo que utilice un enlace HTTP y seguridad de nombre de usuario\/contraseña y un segundo extremo que utilice Autenticación de Windows y FTP.  El primer extremo podrían utilizarlo aplicaciones que tienen acceso al servicio desde fuera de un firewall, mientras que el segundo podría utilizarse en una intranet.  
  
 En tal caso, puede especificar `endpointConfigurationName` como parámetro para el constructor de una referencia de servicio.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para seleccionar un extremo de servicios  
  
1.  Agregue una referencia a un servicio WCF.  Para obtener más información, consulte [How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md).  
  
2.  En el editor de código, agregue un constructor para la referencia de servicio:  
  
    ```vb#  
    Dim proxy As New ServiceReference.Service1Client(  
    ```  
  
    ```c#  
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(  
    ```  
  
    > [!NOTE]
    >  Reemplace *ServiceReference* por el espacio de nombres de la referencia de servicio y *Service1Client* por el nombre del servicio.  
  
3.  Aparecerá una lista de IntelliSense con las sobrecargas del constructor.  Seleccione la sobrecarga `endpointConfigurationName As String`.  
  
4.  Después de la sobrecarga, escriba `=` *ConfigurationName*, donde *ConfigurationName* es el nombre del extremo que desea utilizar.  
  
    > [!NOTE]
    >  Si no conoce los nombres de los extremos disponibles, puede buscarlos en el archivo app.config.  
  
#### Para buscar los extremos disponibles para un servicio WCF  
  
1.  En **Explorador de soluciones**, haga clic con el botón secundario en el archivo app.config del proyecto que contiene la referencia de servicio y, a continuación, haga clic en **Abrir**.  El archivo aparecerá en el editor de código.  
  
2.  Busque la etiqueta `<Client>` en el archivo.  
  
3.  Busque debajo de la etiqueta `<Client>` una etiqueta que empieza por `<Endpoint>`.  
  
     Si la referencia de servicio proporciona varios extremos, habrá dos o más etiquetas `<Endpoint`.  
  
4.  Dentro de la etiqueta `<EndPoint>` encontrará el parámetro `name="`*SomeService*`"` \(donde *SomeService* representa el nombre de un extremo\).  Este es el nombre para el extremo que se puede pasar a la sobrecarga `endpointConfigurationName As String` de un constructor para una referencia de servicio.  
  
## Cómo: Llame a un método Asincrónicamente de Service  
 Se puede llamar a la mayoría de los métodos de servicios de Windows Communication Foundation \(WCF\) de forma sincrónica o asincrónica.  Llamar a un método de forma asincrónica habilita a la aplicación para que continúe funcionando mientras se llama al método, cuando éste funciona a través de una conexión lenta.  
  
 De forma predeterminada, cuando una referencia de servicio se agrega a un proyecto se configura para llamar a los métodos de forma sincrónica.  Se puede cambiar el comportamiento de llamada a métodos de forma asincrónica cambiando un valor en el cuadro de diálogo **Configurar referencia de servicio**.  
  
> [!NOTE]
>  Esta opción se establece para cada servicio.  Si se llama a un método para un servicio de forma asincrónica, se debe llamar a todos los métodos de forma asincrónica.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para llamar a un método de servicio de forma asincrónica  
  
1.  En el **Explorador de soluciones**, seleccione la referencia de servicio.  
  
2.  En el menú **Proyecto**, haga clic en **Configurar referencia de servicio**.  
  
3.  En el cuadro de diálogo **Configurar referencia de servicio**, active la casilla **Generar operaciones asincrónicas**.  
  
## Cómo: Enlace los datos devueltos por un Servicio  
 Puede enlazar datos devueltos por un servicio Windows Communication Foundation \(WCF\) a un control, de la misma manera que puede enlazar cualquier otro origen de datos a un control.  Al agregar una referencia a un servicio WCF, si el servicio contiene tipos compuesto que devuelven datos, se agregan automáticamente a la ventana **Orígenes de datos**.  
  
#### Para enlazar un control a un campo de datos único devuelto por un servicio WCF  
  
1.  En el menú **Datos**, haga clic en **Mostrar orígenes de datos**.  Aparecerá la ventana **Orígenes de datos**.  
  
2.  En la ventana **Orígenes de datos**, expanda el nodo para obtener la referencia de servicio.  Se mostrará cualquier tipo compuesto devuelto por el servicio.  
  
3.  Expanda un nodo para un tipo.  Se mostrarán los campos de datos para ese tipo.  
  
4.  Seleccione un campo y haga clic en la flecha de lista desplegable para mostrar una lista de controles disponibles para el tipo de datos.  
  
5.  Haga clic en el tipo de control al que desea enlazar.  
  
6.  Arrastre el campo a un formulario.  El control se agregará al formulario junto con un componente <xref:System.Windows.Forms.BindingSource> y un componente <xref:System.Windows.Forms.BindingNavigator>.  
  
7.  Repita los pasos del 4 al 6 para cualquier otro campo que desee enlazar.  
  
#### Para enlazar un control al tipo compuesto devuelto por un servicio WCF  
  
1.  En el menú **Datos**, seleccione **Mostrar orígenes de datos**.  Aparecerá la ventana **Orígenes de datos**.  
  
2.  En la ventana **Orígenes de datos**, expanda el nodo para obtener la referencia de servicio.  Se mostrará cualquier tipo compuesto devuelto por el servicio.  
  
3.  Seleccione un nodo para un tipo y haga clic en la flecha de lista desplegable para mostrar una lista de opciones disponibles.  
  
4.  Haga clic en **DataGridView** para mostrar los datos en una cuadrícula o bien, haga clic en **Detalles** para mostrar los datos en controles individuales.  
  
5.  Arrastre el nodo al formulario.  Los controles se agregarán al formulario junto con un componente <xref:System.Windows.Forms.BindingSource> y un componente <xref:System.Windows.Forms.BindingNavigator>.  
  
## Cómo: Configurar un Servicio para reutilizar tipos existente  
 Cuando una referencia de servicio se agrega a un proyecto, cualquier tipo definido en el servicio se genera en el proyecto local.  En muchos casos, esto crea tipos duplicados cuando un servicio usa tipos [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] comunes o cuando los tipos se definen en una biblioteca compartida.  
  
 Para evitar este problema, los tipos en los ensamblados a los que hace referencia se comparte de forma predeterminada.  Si desea deshabilitar el uso compartido de tipos para uno o más ensamblados, puede hacerlo en el cuadro de diálogo **Configurar referencia de servicio**.  
  
#### Para deshabilitar el uso compartido de tipos en un ensamblado único  
  
1.  En el **Explorador de soluciones**, seleccione la referencia de servicio.  
  
2.  En el menú **Proyecto**, haga clic en **Configurar referencia de servicio**.  
  
3.  En el cuadro de diálogo **Configurar referencia de servicio**, seleccione **Volver a usar tipos en los ensamblados especificados**.  
  
4.  Active la casilla para cada ensamblado en el que desea habilitar el uso compartido de tipo.  Para deshabilitar el uso compartido de tipos para un ensamblado, desactive la casilla.  
  
#### Para deshabilitar el uso compartido de tipos en todos los ensamblados  
  
1.  En el **Explorador de soluciones**, seleccione la referencia de servicio.  
  
2.  En el menú **Proyecto**, haga clic en **Configurar referencia de servicio**.  
  
3.  En el cuadro de diálogo **Configurar referencia de servicio**, desactive la casilla **Volver a usar tipos en ensamblados a los que se hace referencia**.  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Walkthrough: Creating and Accessing WCF Services](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Se proporciona una demostración paso a paso sobre cómo crear y utilizar servicios de WCF en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Proporciona una demostración paso a paso de cómo crear y utilizar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Utilización de las herramientas de desarrollo de WCF](../Topic/Using%20the%20WCF%20Development%20Tools.md)|Se explica cómo crear y probar servicios de WCF en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)|Describe cómo agregar, actualizar o quitar los servicios WCF de un proyecto.|  
|[How to: Add, Update, or Remove a WCF Data Service Reference](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Describe cómo se puede hacer referencia a, y utilizar, [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[How to: Add a Reference to a Web Service](../Topic/How%20to:%20Add%20a%20Reference%20to%20a%20Web%20Service.md)|Describe cómo agregar a un proyecto una referencia a un servicio Web XML \(ASMX\).|  
|[Troubleshooting Service References](../data-tools/troubleshooting-service-references.md)|Presenta algunos de los errores más frecuentes que pueden ocurrir durante referencias a servicios e indica cómo evitarlos.|  
|[Depurar servicios WCF](../debugger/debugging-wcf-services.md)|Describe técnicas y problemas de depuración comunes que pueden aparecer en la depuración de servicios de WCF.|  
|[Windows Communication Foundation Authentication Service Overview](../Topic/Windows%20Communication%20Foundation%20Authentication%20Service%20Overview.md)|Describe cómo utilizar WCF para proporcionar un servicio de roles a un sitio web.|  
|[Messaging in the .NET Compact Framework](http://msdn.microsoft.com/es-es/fb74d82c-f81e-46f9-aceb-f875c5c6be4f)|Describe la compatibilidad para la capa de mensajería de WCF en .NET Compact Framework.|  
|[Tutorial: Crear una aplicación de datos con n niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Proporciona instrucciones paso a paso para crear un conjunto de datos con tipo y separar la TableAdapter y el código del conjunto de datos en varios proyectos.|  
|[Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)|Describe los elementos de la interfaz de usuario del cuadro de diálogo **Agregar referencia de servicio**.|  
|[Configurar referencia de servicio \(Cuadro de diálogo\)](../data-tools/configure-service-reference-dialog-box.md)|Describe los elementos de la interfaz de usuario del cuadro de diálogo **Configurar referencia de servicio**.|  
  
## Referencia  
 <xref:System.ServiceModel>  
  
 <xref:System.Data.Services>