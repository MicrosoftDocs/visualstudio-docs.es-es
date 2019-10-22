---
title: Diseñador de actividad Diseñador de flujo de trabajo-Send
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86eab31b2d268475f4ae6c9fe91c9ee5b6a4e4bc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649972"
---
# <a name="send-activity-designer"></a>Diseñador de actividad Sent

El diseñador de actividades **send** se usa para crear y configurar una actividad <xref:System.ServiceModel.Activities.Send>.

## <a name="the-send-activity"></a>Actividad Send

 Una actividad <xref:System.ServiceModel.Activities.Send> se utiliza para enviar un mensaje a un servicio. Una actividad <xref:System.ServiceModel.Activities.ReceiveReply> se puede enlazar a una actividad <xref:System.ServiceModel.Activities.Send> que reciba un mensaje como parte de un patrón de intercambio de mensajes solicitud/respuesta en el cliente.

### <a name="using-the-send-activity-designer"></a>Utilizar el diseñador de actividades Send

Obtenga acceso al diseñador de actividad **send** en la categoría **Mensajería** del **cuadro de herramientas**. El diseñador de actividades **send** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de diseñador de flujo de trabajo siempre que se coloquen normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.Send> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Send. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividad **send** o en el cuadro **displayName** de la cuadrícula de propiedades.

Para crear una actividad <xref:System.ServiceModel.Activities.ReceiveReply> y enlazarla a la actividad <xref:System.ServiceModel.Activities.Send> seleccionada, haga clic con el botón secundario en el diseñador de actividades **send** , haga clic en el elemento **crear ReceiveReply** en el menú contextual y el diseñador **ReceiveReplyForSend** aparecerá debajo de la  **Diseñador de envíos** . La actividad <xref:System.ServiceModel.Activities.ReceiveReply> es una actividad que recibe un mensaje como parte de un patrón de intercambio de mensajes solicitud/respuesta en el cliente. Se puede configurar con el diseñador **ReceiveReplyForSend** .

Como alternativa, el diseñador de plantillas **SendAndReceiveReply** en la categoría **Mensajería** del **cuadro de herramientas** se puede usar para crear un par de actividades preconfiguradas <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.ReceiveReply>. Para obtener más información sobre el uso de las plantillas **SendAndReceiveReply** y **ReceiveReplyForSend** , vea el tema [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

### <a name="the-send-activity-properties"></a>Propiedades de la actividad Send

En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.Send> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en Diseñador de flujo de trabajo superficie.

| Nombre de la propiedad | Requerido | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nombre descriptivo de la actividad <xref:System.ServiceModel.Activities.Send>. El valor predeterminado es Send. Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | True | El nombre de la operación de servicio llamada por esta actividad <xref:System.ServiceModel.Activities.Send>. Esta propiedad se utiliza para construir el valor predeterminado de la propiedad **Action** si la propiedad **Action** no se establece explícitamente. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | True | El nombre del contrato de servicios que implementa el servicio al que se va a llamar. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | False | Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Edite esta propiedad seleccionando el botón de puntos suspensivos junto al campo de **contenido** en la cuadrícula de propiedades o haciendo clic en el botón **definir..** . situado junto a la etiqueta de **contenido** en la superficie del diseñador de actividad **Receive** . Ambos muestran el cuadro de diálogo **definición de contenido** . Para obtener más información acerca de cómo usar este cuadro, vea el tema del [cuadro de diálogo Definición de contenido](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | False | Especifica la clase <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para enrutar el mensaje hacia la instancia de flujo de trabajo adecuada.<br /><br /> Haga clic en el botón de puntos suspensivos junto a la propiedad <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> de la cuadrícula de propiedades para abrir el cuadro de diálogo **Editor de expresiones** . Para obtener más información sobre el uso de este cuadro de diálogo, vea el tema [Cómo: usar el editor de expresiones](../workflow-designer/how-to-use-the-expression-editor.md) . |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | False | Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Send> en el flujo de trabajo. Haga clic en el botón de puntos suspensivos junto a la propiedad <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> de la cuadrícula de propiedades para abrir el cuadro de diálogo **Agregar inicializadores de correlación** . Para obtener más información sobre el uso de este cuadro, vea el tema del [cuadro de diálogo Agregar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | False | Una colección de tipos conocidos para la operación de servicio que va llamar esta actividad <xref:System.ServiceModel.Activities.Send>. Esta propiedad se puede utilizar junto con el conjunto de propiedades <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> para <xref:System.Runtime.Serialization.DataContractSerializer>. Se ignorará si se usa <xref:System.Xml.Serialization.XmlSerializer>.<br /><br /> Seleccione el botón de puntos suspensivos junto al campo **KnownTypes** en la cuadrícula de propiedades para mostrar el cuadro de diálogo Editor de la **colección de tipos** con el que puede Agregar los tipos pertinentes.<br /><br /> Seleccione el botón de puntos suspensivos junto al campo **KnownTypes** en la cuadrícula de propiedades para mostrar el cuadro de diálogo Editor de la **colección de tipos** con el que puede Agregar los tipos pertinentes. Para obtener más información sobre el uso de este cuadro, vea el tema del [cuadro de diálogo Editor de colección de tipos](../workflow-designer/type-collection-editor-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | True | Especifica la enumeración <xref:System.Net.Security.ProtectionLevel> para el mensaje.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> significa solo autenticación.<br />2. <xref:System.Net.Security.ProtectionLevel> significa firmar los datos para ayudar a garantizar la integridad de los datos transmitidos.<br />3. <xref:System.Net.Security.ProtectionLevel> significa cifrar y firmar los datos para ayudar a garantizar la confidencialidad y la integridad de los datos transmitidos. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | True | El serializador que va a utilizar en la operación de servicio que va a llamar la actividad <xref:System.ServiceModel.Activities.Send>. El valor predeterminado es <xref:System.Runtime.Serialization.DataContractSerializer>, que serializa y deserializa una instancia de un tipo en una secuencia o en un documento XML mediante un contrato de datos que se haya proporcionado. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | False | Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, su valor predeterminado es: https://tempuri.org/{service contrato espacio de nombres} nombre del contrato/{nombre del} operación nombre}. Si se especifica en una actividad <xref:System.ServiceModel.Activities.Send>, la actividad <xref:System.ServiceModel.Activities.Receive> que recibe el mensaje debe tener el mismo valor para que el mensaje se entregue correctamente. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | La enumeración <xref:System.Security.Principal.TokenImpersonationLevel> permitida para el receptor del mensaje. Define los niveles de suplantación de seguridad, que rigen el grado en el que un proceso de servidor puede actuar en nombre de un proceso de cliente. <xref:System.Security.Principal.TokenImpersonationLevel> indica que no se ha asignado un nivel de suplantación. <xref:System.Security.Principal.TokenImpersonationLevel> indica que el proceso de servidor no puede obtener información de identificación del cliente y no puede suplantarlo. <xref:System.Security.Principal.TokenImpersonationLevel> indica que el proceso de servidor puede obtener información sobre el cliente, como identificadores de seguridad y privilegios, pero no puede suplantarlo. Esto es útil para los servidores que exportan sus propios objetos, por ejemplo, los productos de base de datos que exportan tablas y vistas. Con la información de seguridad del cliente recuperada, el servidor puede tomar decisiones de validación de acceso sin poder usar otros servicios que están usando el contexto de seguridad del cliente. <xref:System.Security.Principal.TokenImpersonationLevel> indica que el proceso de servidor puede suplantar el contexto de seguridad del cliente en su sistema local. El servidor no puede suplantar al cliente en sistemas remotos. <xref:System.Security.Principal.TokenImpersonationLevel> indica que el proceso de servidor puede suplantar el contexto de seguridad del cliente en sistemas remotos. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | La clase <xref:System.ServiceModel.Endpoint> a la que la actividad <xref:System.ServiceModel.Activities.Send> envía el mensaje. Si se establece esta propiedad, la propiedad <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> debe ser **null**. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | La clase <xref:System.ServiceModel.EndpointAddress> a la que se envía el mensaje. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | El nombre de la configuración del extremo. Se establece esta propiedad cuando se está configurando un punto de conexión en un archivo de configuración. Esta propiedad debe establecerse en el nombre especificado en el elemento **\<endpoint >** del archivo de configuración. Si se establece esta propiedad, la propiedad <xref:System.ServiceModel.Activities.Send.Endpoint%2A> debe ser **null**. |

## <a name="see-also"></a>Vea también

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)