---
title: Windows Communication Foundation y Servicios de datos de WCF
description: Explore los servicios de Windows Communication Foundation (WCF) y los Servicios de datos de WCF en Visual Studio para crear aplicaciones distribuidas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: fb5ace269d7770d0e7d360734268d3e7adfda319
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866130"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Servicios de Windows Communication Foundation y servicios de datos WCF en Visual Studio

Visual Studio proporciona herramientas para trabajar con Windows Communication Foundation (WCF) y Servicios de datos de WCF, tecnologías de Microsoft para crear aplicaciones distribuidas. En este tema se proporciona una introducción a los servicios desde una perspectiva de Visual Studio. Para obtener la documentación completa, vea [Servicios de datos de WCF 4.5](/dotnet/framework/data/wcf/index).

## <a name="what-is-wcf"></a>¿Qué es WCF?

Windows Communication Foundation (WCF) es un marco unificado para crear aplicaciones distribuidas con transacciones que sean seguras, interoperables y de confianza. Reemplaza a tecnologías anteriores de comunicación entre procesos, como los servicios web ASMX, .NET Remoting, Enterprise Services (DCOM) y MSMQ. WCF reúne la funcionalidad de todas esas tecnologías en un modelo de programación unificado. Esto simplifica la experiencia de desarrollo de aplicaciones distribuidas.

### <a name="what-are-wcf-data-services"></a>Qué son los Servicios de datos de WCF

Servicios de datos de WCF es una implementación del estándar del protocolo Open Data (OData).  Servicios de datos de WCF le permite exponer datos tabulares como un conjunto de API de REST, para que pueda devolver datos mediante verbos HTTP estándar como GET, POST, PUT o DELETE. En el lado del servidor, Servicios de datos de WCF se reemplazan por [ASP.NET Web API](https://dotnet.microsoft.com/apps/aspnet/apis) para crear servicios de OData. La biblioteca de cliente de Servicios de datos de WCF sigue siendo una buena opción para consumir servicios de OData en una aplicación .NET desde Visual Studio (**Proyecto** > **Agregar referencia de servicio**). Para obtener más información, vea [WCF Data Services 4.5](/dotnet/framework/data/wcf).

### <a name="wcf-programming-model"></a>Modelo de programación de WCF

El modelo de programación de WCF se basa en la comunicación entre dos entidades: un servicio WCF y un cliente WCF. El modelo de programación se encapsula en el espacio de nombres <xref:System.ServiceModel> de .NET.

### <a name="wcf-service"></a>Servicio WCF

Un servicio WCF se basa en una interfaz que define un contrato entre el servicio y el cliente. Se marca con un atributo <xref:System.ServiceModel.ServiceContractAttribute>, como se muestra en el código siguiente:

[!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
[!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]

Para definir las funciones o los métodos que expone un servicio WCF, debe marcarlos con un atributo <xref:System.ServiceModel.OperationContractAttribute>.

[!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
[!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]

Además, puede exponer datos serializados si marca un tipo compuesto con un atributo <xref:System.Runtime.Serialization.DataContractAttribute>. Esto habilita el enlace de datos en un cliente.

Después de definir una interfaz y sus métodos, se encapsulan en una clase que implementa la interfaz. Una sola clase de servicio WCF puede implementar varios contratos de servicio.

Un servicio WCF se expone para su consumo a través de lo que se conoce como *punto de conexión*. El punto de conexión proporciona la única manera de comunicarse con el servicio; no se puede acceder al servicio a través de una referencia directa como haría con otras clases.

Un punto de conexión está compuesto por una dirección, un enlace y un contrato. La dirección define dónde se encuentra el servicio; puede ser una dirección URL, una dirección FTP o una ruta de acceso local o de red. Un enlace define la forma en que se comunica con el servicio. Los enlaces de WCF proporcionan un modelo versátil para especificar un protocolo como HTTP o FTP, un mecanismo de seguridad como la autenticación de Windows, o nombres de usuario y contraseñas, y mucho más. Un contrato incluye las operaciones expuestas por la clase de servicio WCF.

Se pueden exponer varios puntos de conexión para un solo servicio WCF. Esto permite a los distintos clientes comunicarse con el mismo servicio de diversas formas. Por ejemplo, un servicio bancario podría proporcionar un punto de conexión para los empleados y otro para los clientes externos, cada uno con una dirección, un enlace o un contrato diferentes.

### <a name="wcf-client"></a>cliente de WCF

Un cliente de WCF consta de un *proxy* que permite que una aplicación se comunique con un servicio WCF y un punto de conexión que coincide con un punto de conexión definido para el servicio. El proxy se genera en el lado cliente en el archivo *app.config* e incluye información sobre los tipos y métodos que expone el servicio. En el caso de los servicios que exponen varios puntos de conexión, el cliente puede seleccionar el que mejor se adapte a sus necesidades, por ejemplo, para comunicarse a través de HTTP y usar la autenticación de Windows.

Una vez que se ha creado un cliente de WCF, se hace referencia al servicio en el código como se haría con cualquier otro objeto. Por ejemplo, para llamar al método `GetData` mostrado antes, tendría que escribir código similar al siguiente:

[!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
[!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]

## <a name="wcf-tools-in-visual-studio"></a>Herramientas de WCF en Visual Studio

Visual Studio proporciona herramientas para ayudarle a crear servicios y clientes WCF. Para obtener un tutorial en el que se muestran las herramientas, vea [Tutorial: Creación de un servicio WCF sencillo en Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="create-and-test-wcf-services"></a>Creación y prueba de servicios WCF

Puede usar las plantillas de Visual Studio de WCF como base para crear rápidamente un servicio propio. Después, puede usar el Host automático del servicio WCF y el Cliente de prueba WCF para depurar y probar el servicio. Todas estas herramientas proporcionan un ciclo de depuración y pruebas rápido y estable, y eliminan el requisito de confirmar en un modelo de hospedaje en una fase temprana.

#### <a name="wcf-templates"></a>Plantillas de WCF

Las plantillas para WCF de Visual Studio proporcionan una estructura de clases básica para el desarrollo de servicios. Hay varias plantillas de WCF disponibles en el cuadro de diálogo **Agregar nuevo proyecto**. Incluyen proyectos lLibrary de servicio WCF, sitios web de servicio WCF y plantillas de elementos de servicio WCF.

Al seleccionar una plantilla, se agregan archivos para un contrato de servicio, una implementación de servicio y una configuración de servicio. Todos los atributos necesarios ya están agregados, se crea un servicio simple de tipo "Hola mundo" y no es necesario escribir ningún código. Por supuesto, querrá agregar código para proporcionar funciones y métodos para el servicio en el mundo real, pero las plantillas proporcionan la base mínima.

Para obtener más información sobre las plantillas de WCF, vea [Plantillas de Visual Studio para WCF](/dotnet/framework/wcf/wcf-vs-templates).

#### <a name="wcf-service-host"></a>Host de servicio de WCF

Al iniciar el depurador de Visual Studio (al presionar **F5**) para un proyecto de servicio WCF, la herramienta Host de servicio WCF se inicia de forma automática para hospedar el servicio localmente. Host de servicio WCF enumera los servicios de un proyecto de servicio WCF, carga la configuración del proyecto y crea una instancia de un host por cada servicio que encuentra.

Mediante Host de servicio WCF, puede probar un servicio WCF sin escribir código adicional ni confirmar en un host concreto durante el desarrollo.

Para obtener más información sobre Host de servicio WCF, vea [Host de servicio WCF (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).

#### <a name="wcf-test-client"></a>Cliente de prueba WCF

La herramienta Cliente de prueba WCF le permite especificar parámetros de prueba, enviar esa entrada a un servicio WCF y ver la respuesta que se devuelve. Proporciona una experiencia de pruebas de servicio cómoda cuando se combina con Host de servicio WCF. Puede encontrar la herramienta en la carpeta *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

Al presionar **F5** para depurar un proyecto de servicio WCF, se abre el cliente de prueba de WCF y se muestra una lista de puntos de conexión de servicio definidos en el archivo de configuración. Puede probar los parámetros e iniciar el servicio, y repetir este proceso para probar y validar el servicio de forma continuada.

Para obtener más información sobre Cliente de prueba WCF, vea [Cliente de prueba WCF (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).

### <a name="accessing-wcf-services-in-visual-studio"></a>Acceso a servicios WCF en Visual Studio

Visual Studio simplifica la tarea de creación de clientes WCF, mediante la generación automática de un proxy y un punto de conexión para los servicios que se agregan mediante el cuadro de diálogo **Agregar referencia de servicio**. Toda la información de configuración necesaria se agrega al archivo *app.config*. La mayoría de las veces, lo único que tiene que hacer es crear una instancia del servicio para poder usarlo.

El cuadro de diálogo **Agregar referencia de servicio** le permite escribir la dirección de un servicio o buscar un servicio definido en la solución. El cuadro de diálogo devuelve una lista de servicios y las operaciones que proporcionan. También permite definir el espacio de nombres por el que se hará referencia a los servicios en el código.

El cuadro de diálogo **Configurar referencias de servicio** permite personalizar la configuración de un servicio. Puede cambiar la dirección de un servicio, especificar el nivel de acceso, el comportamiento asincrónico y los tipos de contrato de mensaje, y configurar la reutilización de tipos.

## <a name="how-to-select-a-service-endpoint"></a>Procedimiento para seleccionar un punto de conexión de servicio

Algunos servicios de Windows Communication Foundation (WCF) exponen varios puntos de conexión a través de los cuales un cliente puede comunicarse con el servicio. Por ejemplo, es posible que un servicio exponga un punto de conexión que usa un enlace HTTP y seguridad de nombre de usuario y contraseña, y un segundo punto de conexión en el que se use FTP y la autenticación de Windows. El primer punto de conexión se podría usar en aplicaciones que acceden al servicio desde fuera de un firewall, mientras que el segundo se podría usar en una intranet.

En ese caso, puede especificar `endpointConfigurationName` como un parámetro para el constructor de una referencia de servicio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>Para seleccionar un punto de conexión de servicio

1. Agregue una referencia a un servicio WCF; para ello, haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** y seleccione **Agregar referencia de servicio**.

2. En el Editor de código, agregue un constructor para la referencia de servicio:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Reemplace *ServiceReference* por el espacio de nombres de la referencia de servicio y *Service1Client* por el nombre del servicio.

3. Se muestra una lista de IntelliSense en la que se incluyen las sobrecargas para el constructor. Seleccione la sobrecarga `endpointConfigurationName As String`.

4. Después de la sobrecarga, escriba `=` *ConfigurationName*, donde *ConfigurationName* es el nombre del punto de conexión que quiere usar.

    > [!NOTE]
    > Si no conoce los nombres de los puntos de conexión disponibles, puede encontrarlos en el archivo *app.config*.

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Para buscar los puntos de conexión disponibles para un servicio WCF

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el archivo **app.config** del proyecto que contiene la referencia de servicio y, después, haga clic en **Abrir**. El archivo aparece en el editor de código.

2. Busque la etiqueta `<Client>` en el archivo.

3. Debajo de la etiqueta `<Client>`, busque una etiqueta que empiece por `<Endpoint>`.

     Si la referencia de servicio proporciona varios puntos de conexión, habrá dos o más etiquetas `<Endpoint`.

4. Dentro de la etiqueta `<EndPoint>`, encontrará un parámetro `name="`*SomeService*`"` (donde *SomeService* representa el nombre de un punto de conexión). Es el nombre del punto de conexión que se puede pasar a la sobrecarga de `endpointConfigurationName As String` de un constructor para una referencia de servicio.

## <a name="how-to-call-a-service-method-asynchronously"></a>Procedimiento para llamar a un método de servicio de forma asincrónica

La mayoría de los métodos de los servicios Windows Communication Foundation (WCF) se pueden llamar de forma sincrónica o asincrónica. La llamada a un método de forma asincrónica permite que la aplicación siga funcionando mientras se llama al método cuando funciona a través de una conexión lenta.

De forma predeterminada, cuando se agrega una referencia de servicio a un proyecto, se configura para llamar de forma sincrónica a los métodos. Puede cambiar el comportamiento para llamar a los métodos de forma asincrónica si modifica un valor en el cuadro de diálogo **Configurar referencia de servicio**.

> [!NOTE]
> Esta opción se establece por cada servicio. Si se llama a un método para un servicio de forma asincrónica, se debe llamar a todos los métodos de la misma forma.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>Para llamar a un método de servicio de forma asincrónica

1. En el **Explorador de soluciones**, seleccione la referencia de servicio.

2. En el menú **Proyecto**, haga clic en **Configurar referencia de servicio**.

3. En el cuadro de diálogo **Configurar referencia de servicio**, active la casilla **Generar operaciones asincrónicas**.

## <a name="how-to-bind-data-returned-by-a-service"></a>Procedimiento para enlazar datos devueltos por un servicio

Puede enlazar los datos devueltos por un servicio de Windows Communication Foundation (WCF) a un control del mismo modo que se enlaza cualquier otro origen de datos a un control. Cuando se agrega una referencia a un servicio WCF, si el servicio contiene tipos compuestos que devuelven datos, se agregan de forma automática a la ventana **Orígenes de datos**.

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Para enlazar un control a un solo campo de datos devuelto por un servicio WCF

1. En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.

   Aparecerá la ventana **Orígenes de datos**.

2. En la ventana **Orígenes de datos**, expanda el nodo de la referencia de servicio. Se mostrarán todos los tipos compuestos devueltos por el servicio.

3. Expanda un nodo para un tipo. Aparecen los campos de datos de ese tipo.

4. Seleccione un campo y haga clic en la flecha desplegable para mostrar una lista de los controles que están disponibles para el tipo de datos.

5. Haga clic en el tipo de control al que quiera enlazar.

6. Arrastre el campo hasta un formulario. El control se agregará al formulario, junto con un componente <xref:System.Windows.Forms.BindingSource> y un componente <xref:System.Windows.Forms.BindingNavigator>.

7. Repita los pasos del 4 al 6 para cualquier otro campo que quiera enlazar.

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Para enlazar un control a un tipo compuesto devuelto por un servicio WCF

1. En el menú **Datos**, seleccione **Mostrar orígenes de datos**. Aparecerá la ventana **Orígenes de datos**.

2. En la ventana **Orígenes de datos**, expanda el nodo de la referencia de servicio. Se mostrarán todos los tipos compuestos devueltos por el servicio.

3. Seleccione un nodo para un tipo y haga clic en la flecha desplegable para mostrar una lista de opciones disponibles.

4. Haga clic en **DataGridView** para mostrar los datos en una cuadrícula, o bien en **Detalles** para mostrar los datos en controles individuales.

5. Arrastre el nodo al formulario. Los controles se agregarán al formulario, junto con un componente <xref:System.Windows.Forms.BindingSource> y un componente <xref:System.Windows.Forms.BindingNavigator>.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Procedimiento para configurar un servicio para reutilizar tipos existentes

Cuando se agrega una referencia de servicio a un proyecto, en el proyecto local se generan todos los tipos definidos en el servicio. En muchos casos, esto crea tipos duplicados cuando un servicio usa tipos comunes de .NET o cuando los tipos se definen en una biblioteca compartida.

Para evitar este problema, los tipos de los ensamblados a los que se hace referencia se comparten de forma predeterminada. Si quiere deshabilitar el uso compartido de tipos en uno o varios ensamblados, puede hacerlo en el cuadro de diálogo **Configurar referencias de servicio**.

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Para deshabilitar el uso compartido de tipos en un solo ensamblado

1. En el **Explorador de soluciones**, seleccione la referencia de servicio.

2. En el menú **Proyecto**, haga clic en **Configurar referencia de servicio**.

3. En el cuadro de diálogo **Configurar referencias de servicio**, seleccione **Reutilizar tipos en los ensamblados especificados**.

4. Active la casilla de cada ensamblado en el que quiera habilitar el uso compartido de tipos. Para deshabilitar el uso compartido de tipos para un ensamblado, deje la casilla desactivada.

### <a name="to-disable-type-sharing-in-all-assemblies"></a>Para deshabilitar el uso compartido de tipos en todos los ensamblados

1. En el **Explorador de soluciones**, seleccione la referencia de servicio.

2. En el menú **Proyecto**, haga clic en **Configurar referencia de servicio**.

3. En el cuadro de diálogo **Configurar referencias de servicio**, desactive la casilla **Reutilizar tipos en los ensamblados especificados**.

## <a name="related-topics"></a>Temas relacionados

| Title | Descripción |
| - | - |
| [Tutorial: Crear un servicio WCF sencillo en Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | Se proporciona una demostración paso a paso de la creación y el uso de servicios WCF en Visual Studio. |
| [Tutorial: Crear un servicio de datos de WCF con WPF y Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | Se proporciona una demostración paso a paso de cómo crear y usar Servicios de datos de WCF en Visual Studio. |
| [Utilización de las herramientas de desarrollo de WCF](/dotnet/framework/wcf/using-the-wcf-development-tools) | Se describe cómo crear y probar servicios WCF en Visual Studio. |
| | [Cómo: Adición, actualización o eliminación de una referencia de servicio de datos de WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [Solucionar problemas de referencias de servicio](../data-tools/troubleshooting-service-references.md) | Se presentan algunos errores comunes que se pueden producir con las referencias de servicio y cómo evitarlos. |
| [Depurar servicios WCF](../debugger/debugging-wcf-services.md) | Se describen los problemas y técnicas de depuración comunes que pueden aparecer al depurar servicios WCF. |
| [Tutorial: Creación de una aplicación de datos de n niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | Contiene instrucciones paso a paso para crear un conjunto de datos con tipo y separar el código de TableAdapter y del conjunto de datos en varios proyectos. |
| [Configurar referencia de servicio (cuadro de diálogo)](../data-tools/configure-service-reference-dialog-box.md) | Se describen los elementos de la interfaz de usuario del cuadro de diálogo **Configurar referencia de servicio**. |

## <a name="reference"></a>Referencia

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>Vea también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
