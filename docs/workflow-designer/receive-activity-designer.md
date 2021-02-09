---
title: Diseñador de actividad Diseñador de flujo de trabajo-Receive
description: Obtenga información sobre la actividad Receive y cómo usar el diseñador de actividad Receive para crear y configurar una actividad Receive.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ceff7d40ffd0d7c961f07dd65a8070a8f11a1b4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899384"
---
# <a name="receive-activity-designer"></a>Diseñador de actividades Receive

El diseñador de actividades **Receive** se usa para crear y configurar una <xref:System.ServiceModel.Activities.Receive> actividad. Una actividad <xref:System.ServiceModel.Activities.Receive> es una actividad que recibe un mensaje que puede ser de tipo integrado como <xref:System.ServiceModel.Channels.Message>, <xref:System.IO.Stream> o <xref:System.Xml.Linq.XElement> o bien, un contrato de datos definido por la aplicación, contrato de mensaje o clase XML que se pueden serializar.

## <a name="the-receive-activity"></a>Actividad Receive

La actividad <xref:System.ServiceModel.Activities.Receive> puede recibir un elemento único o varios elementos, en función del tipo de contenido de Receive que se utilice. Una actividad <xref:System.ServiceModel.Activities.SendReply> se puede enlazar a una actividad <xref:System.ServiceModel.Activities.Receive> que reciba un mensaje como parte de un patrón de intercambio de mensajes solicitud/respuesta en el servicio.

### <a name="using-the-receive-activity-designer"></a>Utilizar el diseñador de actividades Receive

Obtenga acceso al diseñador de actividad **Receive** en la categoría **Mensajería** del **cuadro de herramientas**. El diseñador de actividades **Receive** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo, donde se coloquen normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.Receive> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Receive. <xref:System.Activities.Activity.DisplayName%2A>Se puede editar en el encabezado del diseñador de actividad **Receive** o en el cuadro **displayName** de la cuadrícula de propiedades.

Para crear una <xref:System.ServiceModel.Activities.SendReply> actividad y enlazarla a la <xref:System.ServiceModel.Activities.Receive> actividad seleccionada, haga clic con el botón secundario en el diseñador de actividad **Receive** , haga clic en el elemento **crear SendReply** en el menú contextual y el diseñador **SendReplyToReceive** aparecerá debajo del diseñador **Receive** . La actividad <xref:System.ServiceModel.Activities.SendReply> es una actividad que envía el mensaje de respuesta como parte de un patrón de intercambio de mensajes solicitud/respuesta en el servicio. Se puede configurar con el diseñador **SendReplyToReceive** .

Como alternativa, el diseñador de plantillas **ReceiveAndSendReply** en la categoría **Mensajería** del **cuadro de herramientas** se puede usar para crear un par de actividades y configuradas previamente <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> . Para obtener más información sobre el uso de la plantilla **ReceiveAndSendReply** y **SendReplyToReceive** , vea el tema [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) .

### <a name="the-receive-activity-properties"></a>Propiedades de la actividad Receive

En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.Receive> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie de Diseñador de flujo de trabajo. La única propiedad obligatoria es <xref:System.ServiceModel.Activities.Receive.OperationName%2A>.

| Nombre de propiedad | Obligatorio | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Especifica el nombre descriptivo de la actividad <xref:System.ServiceModel.Activities.Receive>. El valor predeterminado es Receive.<br /><br /> Aunque no es obligatorio utilizar un valor no predeterminado para la propiedad <xref:System.Activities.Activity.DisplayName%2A> descriptiva, se recomienza utilizar uno. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | True | Especifica el nombre de la operación de servicio que implementa esta actividad <xref:System.ServiceModel.Activities.Receive>. Esta propiedad se utiliza para construir el valor predeterminado de la propiedad **Action** si la propiedad **Action** no se establece explícitamente. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | False | Especifica el nombre del contrato de servicios. Esta propiedad se utiliza para agrupar las operaciones de servicio en los contratos de servicios individuales. Todas las actividades <xref:System.ServiceModel.Activities.Receive> que tienen la misma propiedad <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> están agrupadas en el mismo contrato de servicios (tipo de puerto WSDL asociado). El valor predeterminado es el nombre CLR completo de la actividad de nivel superior (raíz). |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | False | Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Edite esta propiedad seleccionando el botón de puntos suspensivos junto al campo de **contenido** en la cuadrícula de propiedades o haciendo clic en el botón **definir..** . situado junto a la etiqueta de **contenido** en la superficie del diseñador de actividad **Receive** . Ambos muestran el cuadro de diálogo **definición de contenido** . Para obtener más información acerca de cómo usar este cuadro, vea el tema del [cuadro de diálogo Definición de contenido](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | False | Especifica las correlaciones entre las actividades <xref:System.ServiceModel.Activities.Receive> en operaciones de servicio de un flujo de trabajo con un objeto <xref:System.ServiceModel.MessageQuerySet>. Haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propiedad en la cuadrícula de propiedades para abrir el cuadro de diálogo **definición de CorrelatesOn** . Para obtener más información acerca del uso de este cuadro de diálogo, vea el tema del [cuadro de diálogo Definición de contenido](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | False | Especifica la clase <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para enrutar el mensaje hacia la instancia de flujo de trabajo adecuada.<br /><br /> Haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> propiedad en la cuadrícula de propiedades para abrir el cuadro de diálogo **Editor de expresiones** . Para obtener más información sobre el uso de este cuadro de diálogo, vea el tema [Cómo: usar el editor de expresiones](../workflow-designer/how-to-use-the-expression-editor.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | False | Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo. Haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propiedad en la cuadrícula de propiedades para abrir el cuadro de diálogo **Agregar inicializadores de correlación** . Para obtener más información sobre el uso de este cuadro, vea el tema del [cuadro de diálogo Agregar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | False | Especifica un valor que determina si una nueva instancia de flujo de trabajo se crea para procesar el mensaje en caso de que el mensaje no se correlacione con una instancia de flujo de trabajo existente. Si el valor se establece en **true**, se crea una nueva instancia de flujo de trabajo para procesar el mensaje cuando el mensaje no está correlacionado con una instancia de flujo de trabajo existente. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | False | Especifica una colección de tipos conocidos para la operación de servicio implementada por esta actividad <xref:System.ServiceModel.Activities.Receive>. Esta propiedad se puede utilizar junto con el conjunto de propiedades <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> para <xref:System.Runtime.Serialization.DataContractSerializer>. Se ignorará si se usa <xref:System.Xml.Serialization.XmlSerializer>.<br /><br /> Seleccione el botón de puntos suspensivos junto al campo **KnownTypes** en la cuadrícula de propiedades para mostrar el cuadro de diálogo Editor de la **colección de tipos** con el que puede Agregar los tipos pertinentes. Para obtener más información sobre el uso de este cuadro, vea el tema del [cuadro de diálogo Editor de colección de tipos](../workflow-designer/type-collection-editor-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | False | Especifica la enumeración <xref:System.Net.Security.ProtectionLevel> para el mensaje.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> significa solo autenticación.<br />2.  <xref:System.Net.Security.ProtectionLevel> significa firmar los datos para ayudar a garantizar la integridad de los datos transmitidos.<br />3.  <xref:System.Net.Security.ProtectionLevel> significa cifrar y firmar los datos para ayudar a garantizar la confidencialidad y la integridad de los datos transmitidos. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | False | Especifica el tipo de serializador que se va a utilizar para la operación de servicio que implementa la actividad <xref:System.ServiceModel.Activities.Receive>. El valor predeterminado es <xref:System.Runtime.Serialization.DataContractSerializer>, que serializa y deserializa una instancia de un tipo en una secuencia o en un documento XML que utilice un contrato de datos que se haya proporcionado. Se puede utilizar también <xref:System.Xml.Serialization.XmlSerializer> si se requiere un mayor control de XML. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | False | Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, su valor predeterminado es: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . |

## <a name="see-also"></a>Vea también

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Envío](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
