---
title: Diseñador de flujo de trabajo - Diseñador de actividad de envío
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
ms.openlocfilehash: 8690d5ccf18c752aacb37a71243d9f591fb9ee30
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395219"
---
# <a name="send-activity-designer"></a>Diseñador de actividad Sent

El diseñador de actividades **Send** se <xref:System.ServiceModel.Activities.Send> usa para crear y configurar una actividad.

## <a name="the-send-activity"></a>Actividad Send

 Una actividad <xref:System.ServiceModel.Activities.Send> se utiliza para enviar un mensaje a un servicio. Una actividad <xref:System.ServiceModel.Activities.ReceiveReply> se puede enlazar a una actividad <xref:System.ServiceModel.Activities.Send> que reciba un mensaje como parte de un patrón de intercambio de mensajes solicitud/respuesta en el cliente.

### <a name="using-the-send-activity-designer"></a>Utilizar el diseñador de actividades Send

Acceda al diseñador de actividades **Enviar** en la categoría **Mensajería** del Cuadro de **herramientas**. El Diseñador de actividades de **envío** se puede arrastrar desde el cuadro de **herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se colocan normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.Send> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Send. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividad **Send** o en el **displayName** cuadro de la cuadrícula de propiedades.

Para crear <xref:System.ServiceModel.Activities.ReceiveReply> una actividad y <xref:System.ServiceModel.Activities.Send> enlazarla a la actividad seleccionada, haga clic con el botón secundario en el Diseñador de actividades **de envío,** haga clic en el elemento **Crear RecepciónReply** en el menú contextual y el diseñador **ReceiveReplyForSend** aparece debajo del diseñador **Enviar.** La actividad <xref:System.ServiceModel.Activities.ReceiveReply> es una actividad que recibe un mensaje como parte de un patrón de intercambio de mensajes solicitud/respuesta en el cliente. Se puede configurar con el **ReceiveReplyForSend** diseñador.

Como alternativa, el Diseñador de plantillas **SendAndReceiveReply** en la categoría **Mensajería** del <xref:System.ServiceModel.Activities.Send> cuadro <xref:System.ServiceModel.Activities.ReceiveReply> de **herramientas** se puede usar para crear un par de actividades y preconfigurados. Para obtener más información sobre el uso de las plantillas **SendAndReceiveReply** y **ReceiveReplyForSend,** vea el tema [SendAndReceiveReply.](../workflow-designer/sendandreceivereply-template-designer.md)

### <a name="the-send-activity-properties"></a>Propiedades de la actividad Send

En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.Send> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del Diseñador de flujo de trabajo.

| Nombre de propiedad | Obligatorio | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nombre descriptivo de la actividad <xref:System.ServiceModel.Activities.Send>. El valor predeterminado es Send. Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | True | El nombre de la operación de servicio llamada por esta actividad <xref:System.ServiceModel.Activities.Send>. Esta propiedad se utiliza para construir el valor predeterminado para el **Action** propiedad si el **Action** propiedad no se establece explícitamente. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | True | El nombre del contrato de servicios que implementa el servicio al que se va a llamar. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | False | Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Edite esta propiedad seleccionando el botón de puntos suspensivos junto al campo **Contenido** de la cuadrícula de propiedades o haciendo clic en el botón **Definir...** junto a la etiqueta **Contenido** en la superficie del diseñador de actividades **de recepción.** Ambos muestran el cuadro de diálogo **Definición de contenido.** Para obtener más información acerca de cómo usar este cuadro, vea el cuadro de [diálogo Definición](../workflow-designer/content-definition-dialog-box.md) de contenido tema. |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | False | Especifica la clase <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para enrutar el mensaje hacia la instancia de flujo de trabajo adecuada.<br /><br /> Haga clic en el <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> botón de puntos suspensivos situado junto a la propiedad en la cuadrícula de propiedades para abrir el cuadro de diálogo **Editor de** expresiones. Para obtener más información sobre el uso de este cuadro de diálogo, vea el tema [Cómo: usar el Editor](../workflow-designer/how-to-use-the-expression-editor.md) de expresiones. |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | False | Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Send> en el flujo de trabajo. Haga clic en el <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> botón de puntos suspensivos situado junto a la propiedad en la cuadrícula de propiedades para abrir el cuadro de diálogo Agregar inicializadores de **correlación.** Para obtener más información sobre el uso de este cuadro, vea el [tema Agregar correlationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) cuadro de diálogo. |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | False | Una colección de tipos conocidos para la operación de servicio que va llamar esta actividad <xref:System.ServiceModel.Activities.Send>. Esta propiedad se puede utilizar junto con el conjunto de propiedades <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> para <xref:System.Runtime.Serialization.DataContractSerializer>. Se ignorará si se usa <xref:System.Xml.Serialization.XmlSerializer>.<br /><br /> Seleccione el botón de puntos suspensivos junto al campo **KnownTypes** en la cuadrícula de propiedades para mostrar el cuadro de diálogo Editor de **colección** de tipos con el que puede agregar tipos relevantes.<br /><br /> Seleccione el botón de puntos suspensivos junto al campo **KnownTypes** en la cuadrícula de propiedades para mostrar el cuadro de diálogo Editor de **colección** de tipos con el que puede agregar tipos relevantes. Para obtener más información sobre el uso de este cuadro, vea el cuadro de diálogo Editor de [colección](../workflow-designer/type-collection-editor-dialog-box.md) de tipos tema. |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | True | Especifica la enumeración <xref:System.Net.Security.ProtectionLevel> para el mensaje.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> Significa sólo autenticación.<br />2. <xref:System.Net.Security.ProtectionLevel> significa firmar datos para ayudar a garantizar la integridad de los datos transmitidos.<br />3. <xref:System.Net.Security.ProtectionLevel> significa cifrar y firmar datos para ayudar a garantizar la confidencialidad e integridad de los datos transmitidos. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | True | El serializador que va a utilizar en la operación de servicio que va a llamar la actividad <xref:System.ServiceModel.Activities.Send>. El valor predeterminado es <xref:System.Runtime.Serialization.DataContractSerializer>, que serializa y deserializa una instancia de un tipo en una secuencia o en un documento XML mediante un contrato de datos que se haya proporcionado. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | False | Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, su `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`valor predeterminado es: . Si se especifica en una actividad <xref:System.ServiceModel.Activities.Send>, la actividad <xref:System.ServiceModel.Activities.Receive> que recibe el mensaje debe tener el mismo valor para que el mensaje se entregue correctamente. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | La enumeración <xref:System.Security.Principal.TokenImpersonationLevel> permitida para el receptor del mensaje. Define los niveles de suplantación de seguridad, que rigen el grado en que un proceso de servidor puede actuar en nombre de un proceso de cliente.<xref:System.Security.Principal.TokenImpersonationLevel>  indica que no se ha asignado un nivel de suplantación. <xref:System.Security.Principal.TokenImpersonationLevel>indica que el proceso del servidor no puede obtener información de identificación sobre el cliente y no puede suplantar al cliente. <xref:System.Security.Principal.TokenImpersonationLevel>indica que el proceso de servidor puede obtener información sobre el cliente, como identificadores de seguridad y privilegios, pero que no puede suplantar al cliente. Esto es útil para los servidores que exportan sus propios objetos, por ejemplo, los productos de base de datos que exportan tablas y vistas. Con la información de seguridad del cliente recuperada, el servidor puede tomar decisiones de validación de acceso sin poder usar otros servicios que están usando el contexto de seguridad del cliente. <xref:System.Security.Principal.TokenImpersonationLevel>indica que el proceso del servidor puede suplantar el contexto de seguridad del cliente en su sistema local. El servidor no puede suplantar al cliente en sistemas remotos. <xref:System.Security.Principal.TokenImpersonationLevel>indica que el proceso del servidor puede suplantar el contexto de seguridad del cliente en sistemas remotos. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | La clase <xref:System.ServiceModel.Endpoint> a la que la actividad <xref:System.ServiceModel.Activities.Send> envía el mensaje. Si se establece <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> esta propiedad, la propiedad debe ser **null**. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | La clase <xref:System.ServiceModel.EndpointAddress> a la que se envía el mensaje. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Nombre de la configuración del extremo. Se establece esta propiedad cuando se está configurando un punto de conexión en un archivo de configuración. Esta propiedad debe establecerse en ** \<** el nombre especificado en el punto de conexión>elemento en el archivo de configuración. Si se establece esta <xref:System.ServiceModel.Activities.Send.Endpoint%2A> propiedad, la propiedad debe ser **null**. |

## <a name="see-also"></a>Vea también

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Recibir](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)