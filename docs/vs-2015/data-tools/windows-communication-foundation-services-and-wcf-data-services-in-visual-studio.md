---
title: Servicios de Windows Communication Foundation y WCF Data Services
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e988c8818cdee756310b73d0d214deda43226f2b
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850214"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Servicios de Windows Communication Foundation y servicios de datos WCF en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio proporciona herramientas para trabajar con Windows Communication Foundation (WCF) y [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], tecnologías de Microsoft para crear aplicaciones distribuidas. En este tema se proporciona una introducción a los servicios desde una perspectiva [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obtener la documentación completa, consulte [WCF Data Services 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a).

## <a name="what-is-wcf"></a>¿Qué es WCF?
 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] es un marco unificado para la creación de aplicaciones distribuidas seguras, de confianza, de transacciones e interoperables. Reemplaza tecnologías de comunicación entre procesos anteriores, como los servicios web ASMX, .NET Remoting, Enterprise Services (DCOM) y MSMQ. WCF reúne la funcionalidad de todas esas tecnologías en un modelo de programación unificado. Esto simplifica la experiencia de desarrollo de aplicaciones distribuidas.

#### <a name="what-are-wcf-data-services"></a>Qué son WCF Data Services
 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] es una implementación del estándar del protocolo Open Data (OData).  WCF Data Services le permite exponer datos tabulares como un conjunto de API de REST, lo que le permite devolver datos mediante verbos HTTP estándar como GET, POST, PUT o DELETE. En el lado del servidor, WCF Data Services se reemplazan por [ASP.net web API](https://dotnet.microsoft.com/apps/aspnet/apis) para crear nuevos servicios de oData. La biblioteca de cliente de WCF Data Services sigue siendo una buena opción para consumir servicios OData en una aplicación .NET desde Visual Studio (**Project &#124; Agregar referencia de servicio**). Para obtener más información, vea [WCF Data Services 4.5](https://msdn.microsoft.com/library/cc668792.aspx).

### <a name="wcf-programming-model"></a>Modelo de programación de WCF
 El modelo de programación de WCF se basa en la comunicación entre dos entidades: un servicio WCF y un cliente WCF. El modelo de programación se encapsula en el espacio de nombres <xref:System.ServiceModel> en el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

#### <a name="wcf-service"></a>Servicio WCF
 Un servicio WCF se basa en una interfaz que define un contrato entre el servicio y el cliente. Se marca con un atributo <xref:System.ServiceModel.ServiceContractAttribute>, como se muestra en el código siguiente:

 [!code-csharp[WCFWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#6)]
 [!code-vb[WCFWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#6)]

 [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
 [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

 Defina las funciones o los métodos que expone un servicio WCF marcándolos con un <xref:System.ServiceModel.OperationContractAttribute> atributo. Además, puede exponer datos serializados marcando un tipo compuesto con un atributo <xref:System.Runtime.Serialization.DataContractAttribute>. Esto habilita el enlace de datos en un cliente.

 Después de definir una interfaz y sus métodos, se encapsulan en una clase que implementa la interfaz. Una sola clase de servicio WCF puede implementar varios contratos de servicio.

 Un servicio WCF se expone para su consumo a través de lo que se conoce como *punto de conexión*. El punto de conexión proporciona la única manera de comunicarse con el servicio; no se puede tener acceso al servicio a través de una referencia directa como haría con otras clases.

 Un punto de conexión consta de una dirección, un enlace y un contrato. La dirección define dónde se encuentra el servicio; puede ser una dirección URL, una dirección FTP o una ruta de acceso local o de red. Un enlace define la forma en que se comunica con el servicio. Los enlaces de WCF proporcionan un modelo versátil para especificar un protocolo como HTTP o FTP, un mecanismo de seguridad como la autenticación de Windows o los nombres de usuario y contraseñas, y mucho más. Un contrato incluye las operaciones expuestas por la clase de servicio WCF.

 Se pueden exponer varios puntos de conexión para un solo servicio WCF. Esto permite a los distintos clientes comunicarse con el mismo servicio de maneras diferentes. Por ejemplo, un servicio bancario podría proporcionar un punto de conexión para los empleados y otro para los clientes externos, cada uno con una dirección, un enlace o un contrato diferente.

#### <a name="wcf-client"></a>Cliente WCF
 Un cliente de WCF consta de un *proxy* que permite a una aplicación comunicarse con un servicio WCF y un punto de conexión que coincide con un punto de conexión definido para el servicio. El proxy se genera en el lado cliente en el archivo app. config e incluye información sobre los tipos y métodos que expone el servicio. En el caso de los servicios que exponen varios puntos de conexión, el cliente puede seleccionar el que mejor se adapte a sus necesidades, por ejemplo, para comunicarse a través de HTTP y usar la autenticación de Windows.

 Una vez creado un cliente de WCF, se hace referencia al servicio en el código tal como lo haría con cualquier otro objeto. Por ejemplo, para llamar al método `GetData` mostrado anteriormente, escribiría código similar al siguiente:

 [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
 [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

## <a name="wcf-tools-in-visual-studio"></a>Herramientas de WCF en Visual Studio
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proporciona herramientas para ayudarle a crear servicios WCF y clientes WCF. Para ver un tutorial que muestra las herramientas, vea [Tutorial: crear un servicio WCF simple en Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="creating-and-testing-wcf-services"></a>Crear y probar servicios WCF
 Puede usar las plantillas de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] de WCF como base para crear rápidamente su propio servicio. Después, puede usar el host automático del servicio WCF y el cliente de prueba WCF para depurar y probar el servicio. Estas herramientas juntas proporcionan un ciclo de depuración y pruebas rápido y práctico, y eliminan el requisito de confirmar un modelo de hospedaje en una fase temprana.

#### <a name="wcf-templates"></a>Plantillas WCF
 Las plantillas de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] de WCF proporcionan una estructura de clase básica para el desarrollo del servicio. En el cuadro de diálogo **Agregar nuevo proyecto** están disponibles varias plantillas WCF. Entre ellos se incluyen los proyectos de biblioteca de servicios WCF, los sitios web de servicio WCF y las plantillas de elementos de servicio WCF.

 Al seleccionar una plantilla, se agregan archivos para un contrato de servicio, una implementación de servicio y una configuración de servicio. Ya se han agregado todos los atributos necesarios, con lo que se crea un tipo de servicio "Hola mundo" simple y no es necesario escribir ningún código. Por supuesto, querrá agregar código para proporcionar funciones y métodos para su servicio en el mundo real, pero las plantillas proporcionan la base básica.

 Para obtener más información acerca de las plantillas WCF, consulte [WCF Visual Studio templates](https://msdn.microsoft.com/library/6a608575-3535-4190-89da-911e24c8374f).

#### <a name="wcf-service-host"></a>Host de servicio de WCF
 Al iniciar el depurador de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (presionando F5) para un proyecto de servicio WCF, la herramienta host de servicio WCF se inicia automáticamente para hospedar el servicio localmente. El host de servicio WCF enumera los servicios de un proyecto de servicio WCF, carga la configuración del proyecto y crea una instancia de un host para cada servicio que encuentra.

 Mediante el uso del host de servicio WCF, puede probar un servicio WCF sin escribir código adicional ni confirmar a un host concreto durante el desarrollo.

 Para obtener más información sobre el host de servicio WCF, vea [host de servicio WCF (WcfSvcHost. exe)](https://msdn.microsoft.com/library/8643a63d-a357-4c39-bd6c-cdfdf71e370e).

#### <a name="wcf-test-client"></a>Cliente de prueba de WCF
 La herramienta cliente de prueba de WCF le permite introducir parámetros de prueba, enviar esa entrada a un servicio WCF y ver la respuesta que devuelve el servicio. Proporciona una experiencia de pruebas de servicio cómoda al combinarla con el host de servicio de WCF. La herramienta se puede encontrar en la carpeta \Common7\IDE, que para Visual Studio 2015 instalada en la unidad C: está aquí: **c:\Archivos de programa (x86) \Microsoft Visual Studio 14.0 \ Common7\IDE\\** .

 Al presionar F5 para depurar un proyecto de servicio WCF, se abre el cliente de prueba de WCF y se muestra una lista de puntos de conexión de servicio definidos en el archivo de configuración. Puede probar los parámetros e iniciar el servicio y repetir este proceso para probar y validar continuamente el servicio.

 Para obtener más información acerca del cliente de prueba de WCF, consulte el artículo sobre el [cliente de prueba de WCF (WcfTestClient. exe)](https://msdn.microsoft.com/library/d4302855-677f-4640-aa90-c5d785d72fb7).

### <a name="accessing-wcf-services-in-visual-studio"></a>Obtener acceso a los servicios WCF en Visual Studio
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] simplifica la tarea de creación de clientes WCF, la generación automática de un proxy y un punto de conexión para los servicios que se agregan mediante el cuadro de diálogo **Agregar referencia de servicio** . Toda la información de configuración necesaria se agrega al archivo app. config. La mayoría de las veces, lo único que tiene que hacer es crear una instancia del servicio para poder usarlo.

 El cuadro de diálogo **Agregar referencia de servicio** le permite escribir la dirección de un servicio o buscar un servicio que se define en la solución. El cuadro de diálogo devuelve una lista de servicios y las operaciones proporcionadas por esos servicios. También permite definir el espacio de nombres por el que hará referencia a los servicios en el código.

 El cuadro de diálogo **Configurar referencias de servicio** permite personalizar la configuración de un servicio. Puede cambiar la dirección de un servicio, especificar el nivel de acceso, el comportamiento asincrónico y los tipos de contrato de mensaje, y configurar la reutilización de tipos.

## <a name="how-to-select-a-service-endpoint"></a>Cómo: seleccionar un punto de conexión de servicio
 Algunos servicios de Windows Communication Foundation (WCF) exponen varios puntos de conexión a través de los cuales un cliente puede comunicarse con el servicio. Por ejemplo, un servicio podría exponer un punto de conexión que utiliza un enlace HTTP y la seguridad de nombre de usuario/contraseña y un segundo punto de conexión que usa la autenticación de Windows y FTP. El primer punto de conexión podría ser utilizado por aplicaciones que acceden al servicio desde fuera de un firewall, mientras que el segundo podría usarse en una intranet.

 En tal caso, puede especificar el `endpointConfigurationName` como un parámetro para el constructor de una referencia de servicio.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-select-a-service-endpoint"></a>Para seleccionar un punto de conexión de servicio

1. Para agregar una referencia a un servicio WCF, haga clic con el botón secundario en el nodo del proyecto en Explorador de soluciones y elija **Agregar referencia de servicio** .

2. En el editor de código, agregue un constructor para la referencia de servicio:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Reemplace *ServiceReference* por el espacio de nombres para la referencia de servicio y reemplace *Service1Client* por el nombre del servicio.

3. Se mostrará una lista de IntelliSense con las sobrecargas del constructor. Seleccione la sobrecarga de `endpointConfigurationName As String`.

4. Después de la sobrecarga, escriba `=` *ConfigurationName*, donde *ConfigurationName* es el nombre del punto de conexión que desea utilizar.

    > [!NOTE]
    > Si no conoce los nombres de los puntos de conexión disponibles, puede encontrarlos en el archivo app. config.

#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Para buscar los puntos de conexión disponibles para un servicio WCF

1. En **Explorador de soluciones**, haga clic con el botón secundario en el archivo app. config del proyecto que contiene la referencia de servicio y, a continuación, haga clic en **abrir**. El archivo aparecerá en el editor de código.

2. Busque la etiqueta `<Client>` en el archivo.

3. Busque debajo de la etiqueta `<Client>` para obtener una etiqueta que empiece por `<Endpoint>`.

     Si la referencia de servicio proporciona varios puntos de conexión, habrá dos o más etiquetas de `<Endpoint`.

4. Dentro de la etiqueta `<EndPoint>` encontrará un parámetro `name="`*SomeService*`"` (donde *SomeService* representa un nombre de punto de conexión). Es el nombre del punto de conexión que se puede pasar a la `endpointConfigurationName As String` sobrecarga de un constructor para una referencia de servicio.

## <a name="how-to-call-a-service-method-asynchronously"></a>Cómo: llamar a un método de servicio de forma asincrónica
 La mayoría de los métodos de los servicios Windows Communication Foundation (WCF) se pueden llamar de forma sincrónica o asincrónica. Llamar a un método de forma asincrónica permite que la aplicación siga funcionando mientras se llama al método cuando funciona a través de una conexión lenta.

 De forma predeterminada, cuando se agrega una referencia de servicio a un proyecto, se configura para llamar a métodos sincrónicamente. Puede cambiar el comportamiento para llamar a métodos de forma asincrónica cambiando un valor en el cuadro de diálogo **configurar referencia de servicio** .

> [!NOTE]
> Esta opción se establece por servicio. Si se llama a un método para un servicio de forma asincrónica, se debe llamar a todos los métodos de forma asincrónica.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-call-a-service-method-asynchronously"></a>Para llamar a un método de servicio de forma asincrónica

1. En **Explorador de soluciones**, seleccione la referencia de servicio.

2. En el menú **proyecto** , haga clic en **configurar referencia de servicio**.

3. En el cuadro de diálogo **configurar referencia de servicio** , active la casilla **generar operaciones asincrónicas** .

## <a name="how-to-bind-data-returned-by-a-service"></a>Cómo: enlazar datos devueltos por un servicio
 Puede enlazar los datos devueltos por un servicio de Windows Communication Foundation (WCF) a un control del mismo modo que puede enlazar cualquier otro origen de datos a un control. Cuando se agrega una referencia a un servicio WCF, si el servicio contiene tipos compuestos que devuelven datos, se agregan automáticamente a la ventana **orígenes de datos** .

#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Para enlazar un control a un solo campo de datos devuelto por un servicio WCF

1. En el menú **Datos** , haga clic en **Mostrar orígenes de datos**. Aparecerá la ventana **orígenes de datos** .

2. En la ventana **orígenes de datos** , expanda el nodo de la referencia de servicio. Se mostrarán los tipos compuestos devueltos por el servicio.

3. Expanda un nodo para un tipo. Se mostrarán los campos de datos de ese tipo.

4. Seleccione un campo y haga clic en la flecha desplegable para mostrar una lista de los controles que están disponibles para el tipo de datos.

5. Haga clic en el tipo de control al que desea enlazar.

6. Arrastre el campo hasta un formulario. El control se agregará al formulario junto con un componente de <xref:System.Windows.Forms.BindingSource> y un componente de <xref:System.Windows.Forms.BindingNavigator>.

7. Repita los pasos del 4 al 6 para cualquier otro campo que desee enlazar.

#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Para enlazar un control a un tipo compuesto devuelto por un servicio WCF

1. En el menú **datos** , seleccione **Mostrar orígenes de datos**. Aparecerá la ventana **orígenes de datos** .

2. En la ventana **orígenes de datos** , expanda el nodo de la referencia de servicio. Se mostrarán los tipos compuestos devueltos por el servicio.

3. Seleccione un nodo para un tipo y haga clic en la flecha desplegable para mostrar una lista de opciones disponibles.

4. Haga clic en **DataGridView** para mostrar los datos en una cuadrícula o en **detalles** para mostrar los datos en controles individuales.

5. Arrastre el nodo al formulario. Los controles se agregarán al formulario junto con un componente de <xref:System.Windows.Forms.BindingSource> y un componente de <xref:System.Windows.Forms.BindingNavigator>.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Cómo: configurar un servicio para reutilizar tipos existentes
 Cuando se agrega una referencia de servicio a un proyecto, se generan todos los tipos definidos en el servicio en el proyecto local. En muchos casos, esto crea tipos duplicados cuando un servicio utiliza tipos de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] comunes o cuando los tipos se definen en una biblioteca compartida.

 Para evitar este problema, los tipos de los ensamblados a los que se hace referencia se comparten de forma predeterminada. Si desea deshabilitar el uso compartido de tipos en uno o varios ensamblados, puede hacerlo en el cuadro de diálogo **Configurar referencias de servicio** .

#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Para deshabilitar el uso compartido de tipos en un solo ensamblado

1. En **Explorador de soluciones**, seleccione la referencia de servicio.

2. En el menú **proyecto** , haga clic en **configurar referencia de servicio**.

3. En el cuadro de diálogo **Configurar referencias de servicio** , seleccione **volver a usar tipos en ensamblados a los que se hace referencia especificados**.

4. Active la casilla de cada ensamblado en el que desea habilitar el uso compartido de tipos. Para deshabilitar el uso compartido de tipos para un ensamblado, deje la casilla desactivada.

#### <a name="to-disable-type-sharing-in-all-assemblies"></a>Para deshabilitar el uso compartido de tipos en todos los ensamblados

1. En **Explorador de soluciones**, seleccione la referencia de servicio.

2. En el menú **proyecto** , haga clic en **configurar referencia de servicio**.

3. En el cuadro de diálogo **Configurar referencias de servicio** , desactive la casilla **volver a usar tipos en ensamblados a los que se hace referencia** .

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Tutorial: Crear un servicio WCF sencillo en Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Proporciona una demostración paso a paso de la creación y el uso de servicios WCF en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Tutorial: Crear un servicio de datos de WCF con WPF y Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Proporciona una demostración paso a paso de cómo crear y usar [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Utilización de las herramientas de desarrollo de WCF](https://msdn.microsoft.com/library/054adb87-c244-4d5a-83d1-0b2b44bd454b)|Describe cómo crear y probar servicios WCF en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Cómo: agregar, actualizar o quitar una referencia de servicio](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)|Describe cómo agregar, actualizar o quitar servicios WCF de un proyecto de.|
|[Cómo: Agregar, actualizar o quitar una referencia de servicio de datos de WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Describe cómo hacer referencia y usar [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Solucionar problemas de referencias de servicio](../data-tools/troubleshooting-service-references.md)|Presenta algunos errores comunes que pueden producirse con las referencias de servicio y cómo evitarlos.|
|[Depurar servicios WCF](../debugger/debugging-wcf-services.md)|Describe problemas y técnicas de depuración comunes que pueden producirse al depurar servicios WCF.|
|[Información general del servicio de autenticación de Windows Communication Foundation](https://msdn.microsoft.com/library/6e121a28-89e8-4974-88a8-70aaa6a7d52b)|Describe cómo usar WCF para proporcionar un servicio de rol para un sitio Web.|
|[Tutorial: Crear una aplicación de datos con n niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Contiene instrucciones paso a paso para crear un conjunto de datos con tipo y separar el código de TableAdapter y del conjunto de datos en varios proyectos.|
|[Cuadro de diálogo Configurar referencia de servicio](../data-tools/configure-service-reference-dialog-box.md)|Describe los elementos de la interfaz de usuario del cuadro de diálogo **configurar referencia de servicio** .|

## <a name="reference"></a>Referencia
 <xref:System.ServiceModel>

 <xref:System.Data.Services>

## <a name="see-also"></a>Vea también
 [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
