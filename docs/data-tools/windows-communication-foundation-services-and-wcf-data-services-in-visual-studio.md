---
title: Servicios de Windows Communication Foundation y Data Services de WCF en Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3f3a558e91496006b0d4750492f0ec9abce7333f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Servicios de Windows Communication Foundation y Data Services de WCF en Visual Studio
Visual Studio proporciona herramientas para trabajar con Windows Communication Foundation (WCF) y [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], las tecnologías de Microsoft para crear aplicaciones distribuyen. Este tema proporciona una introducción a los servicios desde un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] perspectiva. Para obtener la documentación completa, vea [4.5 de servicios de datos de WCF](/dotnet/framework/data/wcf/index).

## <a name="what-is-wcf"></a>¿Qué es WCF?
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] es un marco unificado para crear aplicaciones distribuidas seguras, confiables, transacciones e interoperables. Reemplaza las tecnologías de comunicación entre procesos anteriores como servicios Web ASMX, .NET Remoting, Enterprise Services (DCOM) y MSMQ. WCF reúne la funcionalidad de todas esas tecnologías bajo un modelo de programación unificado. Esto simplifica la experiencia de desarrollo de aplicaciones distribuidas.

#### <a name="what-are-wcf-data-services"></a>¿Cuáles son los servicios de datos de WCF
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] es una implementación del protocolo Open Data (OData) estándar.  WCF Data Services le permite exponer datos tabulares como un conjunto de API de REST, lo que le permite devolver datos mediante los verbos HTTP estándar como GET, POST, PUT o DELETE. En el servidor, que se sustituye por WCF Data Services [ASP.NET Web API](http://www.asp.net/web-api) para la creación de nuevos servicios de OData. La biblioteca de cliente de WCF Data Services sigue siendo una buena elección para consumir servicios de OData en una aplicación .NET de Visual Studio (**proyecto &#124; Agregar referencia de servicio**). Para obtener más información, consulte [4.5 de servicios de datos de WCF](http://go.microsoft.com/fwlink/?LinkID=119952).

### <a name="wcf-programming-model"></a>Modelo de programación WCF
 El modelo de programación de WCF se basa en la comunicación entre dos entidades: un servicio WCF y un cliente WCF. El modelo de programación se encapsula en la <xref:System.ServiceModel> espacio de nombres en el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

#### <a name="wcf-service"></a>Servicio WCF
 Un servicio WCF se basa en una interfaz que define un contrato entre el servicio y el cliente. Se marca con un <xref:System.ServiceModel.ServiceContractAttribute> de atributo, como se muestra en el código siguiente:

 [!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]

 [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]

 Definir funciones o métodos expuestos por un servicio WCF marcándolos con un <xref:System.ServiceModel.OperationContractAttribute> atributo. Además, puede exponer los datos serializados marcando un tipo compuesto con un <xref:System.Runtime.Serialization.DataContractAttribute> atributo. Esto habilita el enlace de datos en un cliente.

 Después de definición una interfaz y sus métodos, se encapsulan en una clase que implementa la interfaz. Una sola clase de servicio WCF puede implementar varios contratos de servicio.

 Un servicio WCF se expone de consumo mediante lo que se conoce como un *punto de conexión*. El punto de conexión proporciona la única manera de comunicarse con el servicio; no se puede tener acceso al servicio a través de una referencia directa como lo haría con otras clases.

 Un extremo está compuesto por una dirección, un enlace y un contrato. La dirección define dónde se ubica; el servicio podría tratarse de una dirección URL, una dirección FTP, o una red o la ruta de acceso local. Un enlace define la manera en que se comunica con el servicio. Enlaces de WCF proporcionan un modelo versátil para especificar un protocolo como HTTP o FTP, un mecanismo de seguridad como la autenticación de Windows o nombres de usuario y contraseñas y mucho más. Un contrato incluye las operaciones expuestas por la clase de servicio WCF.

 Se pueden exponer varios puntos de conexión para un solo servicio WCF. Esto permite a los clientes diferentes para comunicarse con el mismo servicio de maneras diferentes. Por ejemplo, un servicio de banca podría proporcionar un punto de conexión para los empleados y otra para los clientes externos, cada uno con una dirección diferente, el enlace o contrato.

#### <a name="wcf-client"></a>Cliente de WCF
 Un cliente de WCF consta de un *proxy* que permite a una aplicación para comunicarse con un servicio WCF y un punto de conexión que coincide con un punto de conexión definido para el servicio. El proxy generado en el lado del cliente en el archivo app.config e incluye información sobre los tipos y métodos expuestos por el servicio. Para los servicios que exponen varios puntos de conexión, el cliente puede seleccionar uno que mejor se adapte a sus necesidades, por ejemplo, para comunicarse a través de HTTP y usar la autenticación de Windows.

 Una vez creado un cliente WCF, haga referencia al servicio en el código como haría con cualquier otro objeto. Por ejemplo, para llamar a la `GetData` método mostrado anteriormente, habría que escribir código que tiene el siguiente aspecto:

 [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]

## <a name="wcf-tools-in-visual-studio"></a>Herramientas WCF en Visual Studio
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona herramientas para ayudarle a crear servicios WCF y clientes de WCF. Para ver un tutorial que muestra las herramientas, consulte [Tutorial: crear un servicio de WCF sencillo en formularios Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="creating-and-testing-wcf-services"></a>Crear y probar los servicios de WCF
 Puede usar WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] plantillas como base para crear rápidamente su propio servicio. A continuación, puede usar el Host de servicio WCF y el cliente de prueba WCF para depurar y probar el servicio. Juntas, estas herramientas proporcionan una depuración cómodo y rápido y un ciclo de prueba y eliminan la necesidad de adaptarse a un modelo de hospedaje en una fase temprana.

#### <a name="wcf-templates"></a>Plantillas WCF
 WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] plantillas proporcionan una estructura de clase básica para el desarrollo del servicio. Existen varias plantillas WCF en el **Agregar nuevo proyecto** cuadro de diálogo. Estos incluyen proyectos de biblioteca de servicios WCF, sitios Web de servicios de WCF y plantillas de elementos de servicio de WCF.

 Cuando selecciona una plantilla, se agregan archivos para un contrato de servicio, una implementación de servicio y una configuración del servicio. Todos los atributos necesarios ya se han agregado, crear un tipo de "Hello World" simple del servicio, y no tenía que escribir ningún código. Por supuesto, deseará agregar código para proporcionar funciones y métodos para el servicio del mundo real, pero las plantillas proporcionan el fundamento básico.

 Para más información acerca de las plantillas WCF, consulte [plantillas de Visual Studio para WCF](/dotnet/framework/wcf/wcf-vs-templates).

#### <a name="wcf-service-host"></a>Host de servicio de WCF
 Al iniciar el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] del depurador (presionando F5) para un proyecto de servicio WCF, el Host de servicio WCF herramienta se inicia automáticamente para hospedar el servicio localmente. Host de servicio WCF enumera los servicios de un proyecto de servicio WCF, carga la configuración del proyecto y crea una instancia de un host para cada servicio que busca.

 Mediante el uso de Host de servicio WCF, puede probar un servicio WCF sin escribir código adicional ni confirmar a un host concreto durante el desarrollo.

 Para obtener más información sobre el Host de servicio WCF, vea [Host de servicio WCF (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).

#### <a name="wcf-test-client"></a>Cliente de prueba WCF
 La herramienta de cliente de prueba WCF le permite especificar parámetros de prueba, enviar esa entrada a un servicio WCF y ver la respuesta que devuelve el servicio. Proporciona un servicio adecuado de prueba cuando se combinan con el Host de servicio WCF. La herramienta se puede encontrar en la carpeta \Common7\IDE, que para Visual Studio 2015 instalados en la unidad C: está aquí: **C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\IDE\\**.

 Cuando se presiona F5 para depurar un proyecto de servicio WCF, el cliente de prueba WCF se abre y muestra una lista de extremos de servicio que se definen en el archivo de configuración. Puede probar los parámetros e iniciar el servicio y repetir este proceso para probar y validar el servicio continuamente.

 Para obtener más información sobre el cliente de prueba WCF, vea [WCF Test Client (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).

### <a name="accessing-wcf-services-in-visual-studio"></a>Acceso a los servicios WCF en Visual Studio
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] simplifica la tarea de creación de clientes de WCF, generar automáticamente un proxy y un punto de conexión para servicios que se agregan mediante el uso de la **Agregar referencia de servicio** cuadro de diálogo. Toda la información de configuración necesaria se agrega al archivo app.config. La mayoría de los casos, todo lo que tienes que hacer es crear instancias del servicio para poder utilizarlo.

 El **Agregar referencia de servicio** cuadro de diálogo le permite introducir la dirección de un servicio o buscar un servicio que se define en la solución. El cuadro de diálogo devuelve una lista de servicios y las operaciones proporcionadas por esos servicios. También permite definir el espacio de nombres por el que se hace referencia a los servicios en el código.

 El **configurar referencia de servicio** cuadro de diálogo le permite personalizar la configuración para un servicio. Puede cambiar la dirección de un servicio, especifique el nivel de acceso, el comportamiento asincrónico y los tipos de contrato de mensaje y configurar la reutilización de tipos.

## <a name="how-to-select-a-service-endpoint"></a>Cómo: seleccionar un extremo de servicio
Algunos servicios de Windows Communication Foundation (WCF) exponen varios puntos de conexión a través del cual un cliente puede comunicarse con el servicio. Por ejemplo, un servicio puede exponer un punto de conexión que utiliza un nombre de usuario y el enlace de HTTP / seguridad de contraseña y un segundo punto de conexión que utiliza autenticación de Windows y FTP. El primer punto de conexión podría utilizarse en aplicaciones que tienen acceso el servicio desde fuera de un firewall, mientras que el segundo podría utilizarse en una intranet.

En tal caso, puede especificar el `endpointConfigurationName` como un parámetro al constructor de una referencia de servicio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-select-a-service-endpoint"></a>Para seleccionar un extremo de servicio

1.  Agregue una referencia a un servicio WCF haciendo clic en el nodo del proyecto en el Explorador de soluciones y elegir **Agregar referencia de servicio**.

2.  En el Editor de código, agregue un constructor para la referencia de servicio:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    >  Reemplace *ServiceReference* con el espacio de nombres para la referencia de servicio y el reemplazo *Service1Client* con el nombre del servicio.

3.  Se mostrará una lista de IntelliSense con las sobrecargas del constructor. Seleccione el `endpointConfigurationName As String` de sobrecarga.

4.  Después de la sobrecarga, escriba `=` *ConfigurationName*, donde *ConfigurationName* es el nombre del punto de conexión que desea usar.

    > [!NOTE]
    >  Si no conoce los nombres de los extremos disponibles, puede encontrarlos en el archivo app.config.

#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Para buscar los extremos disponibles para un servicio WCF

1.  En **el Explorador de soluciones**, haga clic en el archivo app.config para el proyecto que contiene la referencia de servicio y, a continuación, haga clic en **abiertos**. El archivo aparecerá en el Editor de código.

2.  Busque la `<Client>` etiqueta en el archivo.

3.  Busque debajo de la `<Client>` etiqueta de una etiqueta que empieza por `<Endpoint>`.

     Si la referencia de servicio proporciona varios extremos, habrá dos o más `<Endpoint` etiquetas.

4.  Dentro de la `<EndPoint>` etiqueta encontrará un `name="` *SomeService* `"` parámetro (donde *SomeService* representa un nombre de punto de conexión). Este es el nombre para el extremo que puede pasarse a la `endpointConfigurationName As String` sobrecarga de un constructor para una referencia de servicio.

## <a name="how-to-call-a-service-method-asynchronously"></a>Cómo: llamar a un método de servicio de forma asincrónica
Mayoría de los métodos en los servicios de Windows Communication Foundation (WCF) se puede llamar de forma sincrónica o asincrónica. Llamar a un método de forma asincrónica permite que la aplicación continuar trabajando mientras se está llamando al método cuando funciona con una conexión lenta.

De forma predeterminada, cuando se agrega una referencia de servicio a un proyecto se configura para llamar a métodos de forma sincrónica. Puede cambiar el comportamiento para llamar a métodos de forma asincrónica cambiando un valor en el **configurar referencia de servicio** cuadro de diálogo.

> [!NOTE]
>  Esta opción se establece de forma por servicio. Si se llama a un método de un servicio de forma asincrónica, se deben llamar de forma asincrónica todos los métodos.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-call-a-service-method-asynchronously"></a>Llamar a un método de servicio de forma asincrónica

1.  En **el Explorador de soluciones**, seleccione la referencia de servicio.

2.  En el **proyecto** menú, haga clic en **configurar referencia de servicio**.

3.  En el **configurar referencia de servicio** cuadro de diálogo, seleccione la **generar operaciones asincrónicas** casilla de verificación.

## <a name="how-to-bind-data-returned-by-a-service"></a>Cómo: enlazar datos devueltos por un servicio
Puede enlazar los datos devueltos por un servicio de Windows Communication Foundation (WCF) a un control, tal y como cualquier otro origen de datos se puede enlazar a un control. Cuando se agrega una referencia a un servicio WCF, si el servicio contiene tipos compuesto que devuelven datos, se agregan automáticamente a la **orígenes de datos** ventana.

#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Para enlazar un control con el único campo de datos devuelto por un servicio WCF

1.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**. El **orígenes de datos** aparecerá la ventana.

2.  En el **orígenes de datos** ventana, expanda el nodo de la referencia de servicio. Se mostrará cualquier tipo compuesto devuelto por el servicio.

3.  Expanda un nodo para un tipo. Se mostrará los campos de datos para ese tipo.

4.  Seleccione un campo y haga clic en la flecha de lista desplegable para mostrar una lista de controles que están disponibles para el tipo de datos.

5.  Haga clic en el tipo de control que desea enlazar.

6.  Arrastre el campo a un formulario. El control se agregará al formulario junto con un <xref:System.Windows.Forms.BindingSource> componente y una <xref:System.Windows.Forms.BindingNavigator> componente.

7.  Repita los pasos 4 aunque 6 para cualquier otro que los campos que desea enlazar.

#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Para enlazar un control al tipo compuesto devuelto por un servicio WCF

1.  En el **datos** menú, seleccione **Mostrar orígenes de datos**. El **orígenes de datos** aparecerá la ventana.

2.  En el **orígenes de datos** ventana, expanda el nodo de la referencia de servicio. Se mostrará cualquier tipo compuesto devuelto por el servicio.

3.  Seleccione un nodo para un tipo y haga clic en la flecha de lista desplegable para mostrar una lista de opciones disponibles.

4.  Haga clic en **DataGridView** para mostrar los datos en una cuadrícula o **detalles** para mostrar los datos en controles individuales.

5.  Arrastre el nodo al formulario. Los controles se agregarán al formulario junto con un <xref:System.Windows.Forms.BindingSource> componente y una <xref:System.Windows.Forms.BindingNavigator> componente.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Cómo: configurar un servicio para volver a usar tipos existentes
Cuando se agrega una referencia de servicio a un proyecto, los tipos definidos en el servicio se generan en el proyecto local. En muchos casos, esto crea tipos duplicados cuando un servicio utiliza comunes [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] tipos o cuando se definen los tipos de una biblioteca compartida.

Para evitar este problema, los tipos en los ensamblados se comparten de forma predeterminada. Si desea deshabilitar el uso compartido para uno o más ensamblados de tipos, también puede hacer esto en el **configurar referencia de servicio** cuadro de diálogo.

#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Para deshabilitar el uso compartido en un único ensamblado de tipos

1.  En **el Explorador de soluciones**, seleccione la referencia de servicio.

2.  En el **proyecto** menú, haga clic en **configurar referencia de servicio**.

3.  En el **configurar referencia de servicio** cuadro de diálogo, seleccione **volver a usar tipos en ensamblados especificados**.

4.  Active la casilla de verificación para cada ensamblado en el que desea habilitar el uso compartido de tipos. Para deshabilitar el uso compartido de un ensamblado de tipos, deje desactivada la casilla de verificación.

#### <a name="to-disable-type-sharing-in-all-assemblies"></a>Para deshabilitar el uso compartido de todos los ensamblados de tipos

1.  En **el Explorador de soluciones**, seleccione la referencia de servicio.

2.  En el **proyecto** menú, haga clic en **configurar referencia de servicio**.

3.  En el **configurar referencia de servicio** cuadro de diálogo, desactive la **volver a usar tipos en los ensamblados** casilla de verificación.

## <a name="related-topics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Tutorial: Crear un servicio WCF sencillo en Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Proporciona una demostración paso a paso de creación y uso de servicios de WCF en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|
|[Tutorial: Crear un servicio de datos de WCF con WPF y Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Proporciona una demostración paso a paso de cómo crear y usar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|
|[Utilización de las herramientas de desarrollo de WCF](/dotnet/framework/wcf/using-the-wcf-development-tools)|Describe cómo crear y probar los servicios WCF en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|
||[Cómo: Agregar, actualizar o quitar una referencia de servicio de datos de WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Describe cómo hacer referencia y utilizar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|
|[Solucionar problemas de referencias de servicio](../data-tools/troubleshooting-service-references.md)|Presenta algunos errores comunes que pueden producirse con referencias de servicio y cómo evitarlos.|
|[Depurar servicios WCF](../debugger/debugging-wcf-services.md)|Describe problemas de depuración comunes y técnicas que pueden surgir al depurar los servicios WCF.|
|[Tutorial: Crear una aplicación de datos con n niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Contiene instrucciones paso a paso para crear un conjunto de datos con tipo y separar el código de TableAdapter y del conjunto de datos en varios proyectos.|
|[Cuadro de diálogo Configurar referencia de servicio](../data-tools/configure-service-reference-dialog-box.md)|Describe los elementos de interfaz de usuario de la **configurar referencia de servicio** cuadro de diálogo.|

## <a name="reference"></a>Referencia

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>Vea también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)