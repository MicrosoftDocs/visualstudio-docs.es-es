---
title: Diseñador de flujo de trabajo - Diseñador de actividades Send
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d27bd9be1b769215dd77d1e906a5698e17bd18b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59659948"
---
# <a name="send-activity-designer"></a>Diseñador de actividad Sent

El **enviar** Diseñador de actividad se usa para crear y configurar un <xref:System.ServiceModel.Activities.Send> actividad.

## <a name="the-send-activity"></a>Actividad Send

 Una actividad <xref:System.ServiceModel.Activities.Send> se utiliza para enviar un mensaje a un servicio. Una actividad <xref:System.ServiceModel.Activities.ReceiveReply> se puede enlazar a una actividad <xref:System.ServiceModel.Activities.Send> que reciba un mensaje como parte de un patrón de intercambio de mensajes solicitud/respuesta en el cliente.

### <a name="using-the-send-activity-designer"></a>Utilizar el diseñador de actividades Send

Acceso a la **enviar** Diseñador de actividad en el **mensajería** categoría de la **cuadro de herramientas**. El **enviar** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.Send> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Send. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **enviar** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades.

Para crear un <xref:System.ServiceModel.Activities.ReceiveReply> actividad y enlazarlo a la seleccionada <xref:System.ServiceModel.Activities.Send> actividad, haga clic en el **enviar** haga clic en Diseñador de actividad el **crear ReceiveReply** elemento en el menú contextual y el **ReceiveReplyForSend** diseñador aparece debajo de la **enviar** diseñador. La actividad <xref:System.ServiceModel.Activities.ReceiveReply> es una actividad que recibe un mensaje como parte de un patrón de intercambio de mensajes solicitud/respuesta en el cliente. Se puede configurar con el **ReceiveReplyForSend** diseñador.

Como alternativa, el **SendAndReceiveReply** Diseñador de plantilla en el **mensajería** categoría de la **cuadro de herramientas** puede usarse para crear una pareja configurada previamente <xref:System.ServiceModel.Activities.Send>y <xref:System.ServiceModel.Activities.ReceiveReply> actividades. Para obtener más información sobre el uso de la **SendAndReceiveReply** y **ReceiveReplyForSend** plantillas, consulte el [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) tema.

### <a name="the-send-activity-properties"></a>Propiedades de la actividad Send

En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.Send> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en cuadrícula de propiedades o en la superficie del Diseñador de flujo de trabajo.

| Nombre de la propiedad | Obligatorio | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Nombre descriptivo de la actividad <xref:System.ServiceModel.Activities.Send>. El valor predeterminado es Send. Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | True | El nombre de la operación de servicio llamada por esta actividad <xref:System.ServiceModel.Activities.Send>. Esta propiedad se utiliza para construir el valor predeterminado para el **acción** propiedad si el **acción** propiedad no se establece explícitamente. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | True | El nombre del contrato de servicios que implementa el servicio al que se va a llamar. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | False | Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Editar esta propiedad seleccionando el botón de puntos suspensivos junto a la **contenido** campo en la cuadrícula de propiedades o haga clic en el **definir...**  situado junto a la **contenido** etiquetar en el **recepción** superficie del Diseñador de actividad. Ambos muestran el **definición de contenido** cuadro de diálogo. Para obtener más información sobre cómo usar este cuadro, vea el [cuadro de diálogo de definición de contenido](../workflow-designer/content-definition-dialog-box.md) tema. |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | False | Especifica la clase <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para enrutar el mensaje hacia la instancia de flujo de trabajo adecuada.<br /><br /> Haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> propiedad en la cuadrícula de propiedades para abrir el **Editor de expresiones** cuadro de diálogo. Para obtener más información sobre el uso de este cuadro de diálogo, vea el [Cómo: Utilice el Editor de expresiones](../workflow-designer/how-to-use-the-expression-editor.md) tema. |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | False | Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Send> en el flujo de trabajo. Haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> propiedad en la cuadrícula de propiedades para abrir el **agregar inicializadores de correlación** cuadro de diálogo. Para obtener más información sobre el uso de este cuadro, vea el [cuadro de diálogo Agregar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) tema. |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | False | Una colección de tipos conocidos para la operación de servicio que va llamar esta actividad <xref:System.ServiceModel.Activities.Send>. Esta propiedad se puede utilizar junto con el conjunto de propiedades <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> para <xref:System.Runtime.Serialization.DataContractSerializer>. Se ignorará si se usa <xref:System.Xml.Serialization.XmlSerializer>.<br /><br /> Seleccione el botón de puntos suspensivos junto a la **KnownTypes** campo en la cuadrícula de propiedades para mostrar el **Editor de la colección de tipo** cuadro de diálogo con el que puede agregar los tipos pertinentes.<br /><br /> Seleccione el botón de puntos suspensivos junto a la **KnownTypes** campo en la cuadrícula de propiedades para mostrar el **Editor de la colección de tipo** cuadro de diálogo con el que puede agregar los tipos pertinentes. Para obtener más información sobre el uso de este cuadro, vea el [cuadro de diálogo del Editor de colección de tipo](../workflow-designer/type-collection-editor-dialog-box.md) tema. |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | True | Especifica la enumeración <xref:System.Net.Security.ProtectionLevel> para el mensaje.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> significa que sólo la autenticación.<br />2. <xref:System.Net.Security.ProtectionLevel> significa firmar datos para ayudar a garantizar la integridad de los datos transmitidos.<br />3. <xref:System.Net.Security.ProtectionLevel> significa cifrar y firmar datos para ayudar a garantizar la confidencialidad e integridad de los datos transmitidos. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | True | El serializador que va a utilizar en la operación de servicio que va a llamar la actividad <xref:System.ServiceModel.Activities.Send>. El valor predeterminado es <xref:System.Runtime.Serialization.DataContractSerializer>, que serializa y deserializa una instancia de un tipo en una secuencia o en un documento XML mediante un contrato de datos que se haya proporcionado. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | False | Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, su valor predeterminado es: https://tempuri.org/{service espacio de nombres de contrato} / {nombre de contrato de servicio} / {nombre de la operación}. Si se especifica en una actividad <xref:System.ServiceModel.Activities.Send>, la actividad <xref:System.ServiceModel.Activities.Receive> que recibe el mensaje debe tener el mismo valor para que el mensaje se entregue correctamente. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | La enumeración <xref:System.Security.Principal.TokenImpersonationLevel> permitida para el receptor del mensaje. Define los niveles de suplantación de seguridad, que determinan el grado al que un proceso de servidor puede actuar en nombre de un proceso de cliente.<xref:System.Security.Principal.TokenImpersonationLevel> indica que no está asignado un nivel de suplantación. <xref:System.Security.Principal.TokenImpersonationLevel> indica que el proceso de servidor no puede obtener información de identificación del cliente y no puede suplantarlo. <xref:System.Security.Principal.TokenImpersonationLevel> indica que el proceso de servidor puede obtener información sobre el cliente, como identificadores de seguridad y privilegios, pero no puede suplantarlo. Esto es útil para los servidores que exportan sus propios objetos, por ejemplo, los productos de base de datos que exportan tablas y vistas. Con la información de seguridad del cliente recuperada, el servidor puede tomar decisiones de validación de acceso sin poder usar otros servicios que están usando el contexto de seguridad del cliente. <xref:System.Security.Principal.TokenImpersonationLevel> indica que el proceso de servidor puede suplantar el contexto de seguridad del cliente en su sistema local. El servidor no puede suplantar al cliente en sistemas remotos. <xref:System.Security.Principal.TokenImpersonationLevel> indica que el proceso de servidor puede suplantar el contexto de seguridad del cliente en sistemas remotos. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | La clase <xref:System.ServiceModel.Endpoint> a la que la actividad <xref:System.ServiceModel.Activities.Send> envía el mensaje. Si se establece esta propiedad la <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> propiedad debe ser **null**. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | La clase <xref:System.ServiceModel.EndpointAddress> a la que se envía el mensaje. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | El nombre de la configuración del extremo. Se establece esta propiedad cuando se está configurando un punto de conexión en un archivo de configuración. Esta propiedad debe establecerse en el nombre proporcionado en el  **\<punto de conexión >** elemento en el archivo de configuración. Si se establece esta propiedad, el <xref:System.ServiceModel.Activities.Send.Endpoint%2A> propiedad debe ser **null**. |

## <a name="see-also"></a>Vea también

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)