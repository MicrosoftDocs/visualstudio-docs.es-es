---
title: Diseñador de flujo de trabajo - Diseñador de actividades Receive
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7573c126ce8e11143d3b39a637c44649d15acf95
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979521"
---
# <a name="receive-activity-designer"></a>Diseñador de actividades Receive

El **recepción** Diseñador de actividades se usa para crear y configurar un <xref:System.ServiceModel.Activities.Receive> actividad. Una actividad <xref:System.ServiceModel.Activities.Receive> es una actividad que recibe un mensaje que puede ser de tipo integrado como <xref:System.ServiceModel.Channels.Message>, <xref:System.IO.Stream> o <xref:System.Xml.Linq.XElement> o bien, un contrato de datos definido por la aplicación, contrato de mensaje o clase XML que se pueden serializar.

## <a name="the-receive-activity"></a>Actividad Receive

La actividad <xref:System.ServiceModel.Activities.Receive> puede recibir un elemento único o varios elementos, en función del tipo de contenido de Receive que se utilice. Una actividad <xref:System.ServiceModel.Activities.SendReply> se puede enlazar a una actividad <xref:System.ServiceModel.Activities.Receive> que reciba un mensaje como parte de un patrón de intercambio de mensajes solicitud/respuesta en el servicio.

### <a name="using-the-receive-activity-designer"></a>Utilizar el diseñador de actividades Receive
 El **recepción** Diseñador de actividad puede encontrarse en el **mensajería** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas**ficha en el Diseñador de flujo de trabajo (como alternativa, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)

 El **recepción** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.Receive> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Receive. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **recepción** Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades.

 Para crear un <xref:System.ServiceModel.Activities.SendReply> actividad y enlazarla a seleccionado <xref:System.ServiceModel.Activities.Receive> actividad, haga clic en el **recepción** haga clic en Diseñador de actividad el **crear SendReply** elemento en el menú contextual y la **SendReplyToReceive** diseñador aparece debajo de la **recepción** diseñador. La actividad <xref:System.ServiceModel.Activities.SendReply> es una actividad que envía el mensaje de respuesta como parte de un patrón de intercambio de mensajes solicitud/respuesta en el servicio. Se puede configurar con el **SendReplyToReceive** diseñador.

 Como alternativa, el **ReceiveAndSendReply** Diseñador de plantilla en el **mensajería** categoría de la **cuadro de herramientas** puede usarse para crear un par de preconfigurada<xref:System.ServiceModel.Activities.Receive>y <xref:System.ServiceModel.Activities.SendReply> actividad. Para obtener más información sobre el uso de la **ReceiveAndSendReply** y **SendReplyToReceive** plantilla, consulte el [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) tema.

### <a name="the-receive-activity-properties"></a>Propiedades de la actividad Receive
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.Receive> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en cuadrícula de propiedades o en la superficie del Diseñador de flujo de trabajo. La única propiedad obligatoria es <xref:System.ServiceModel.Activities.Receive.OperationName%2A>.

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre descriptivo de la actividad <xref:System.ServiceModel.Activities.Receive>. El valor predeterminado es Receive.<br /><br /> Aunque no es obligatorio utilizar un valor no predeterminado para la propiedad <xref:System.Activities.Activity.DisplayName%2A> descriptiva, se recomienza utilizar uno.|
|<xref:System.ServiceModel.Activities.Receive.OperationName%2A>|True|Especifica el nombre de la operación de servicio que implementa esta actividad <xref:System.ServiceModel.Activities.Receive>. Esta propiedad se utiliza para construir el valor predeterminado para la **acción** propiedad si el **acción** propiedad no se establece explícitamente.|
|<xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>|False|Especifica el nombre del contrato de servicios. Esta propiedad se utiliza para agrupar las operaciones de servicio en los contratos de servicios individuales. Todas las actividades <xref:System.ServiceModel.Activities.Receive> que tienen la misma propiedad <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> están agrupadas en el mismo contrato de servicios (tipo de puerto WSDL asociado). El valor predeterminado es el nombre de CLR completo correspondiente a la actividad de nivel superior (raíz).|
|<xref:System.ServiceModel.Activities.Receive.Content%2A>|False|Especifica el mensaje o contenido del parámetro que se va a recibir. Puede ser una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Editar esta propiedad, haga clic en el botón de puntos suspensivos junto a la **contenido** campo en la cuadrícula de propiedades o haga clic en el **definir...**  situado junto a la **contenido** etiqueta en el **recepción** superficie del Diseñador de actividad. Ambos muestran el **definición de contenido** cuadro de diálogo. Para obtener más información acerca de cómo usar este cuadro, consulte la [cuadro de diálogo de definición de contenido](../workflow-designer/content-definition-dialog-box.md) tema.|
|<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>|False|Especifica las correlaciones entre las actividades <xref:System.ServiceModel.Activities.Receive> en operaciones de servicio de un flujo de trabajo con un objeto <xref:System.ServiceModel.MessageQuerySet>. Haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propiedad en la cuadrícula de propiedades para abrir el **definición de CorrelatesOn** cuadro de diálogo. Para obtener más información sobre el uso de este cuadro de diálogo, vea el [cuadro de diálogo de definición de contenido](../workflow-designer/content-definition-dialog-box.md) tema.|
|<xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A>|False|Especifica la clase <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para enrutar el mensaje hacia la instancia de flujo de trabajo adecuada.<br /><br /> Haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> propiedad en la cuadrícula de propiedades para abrir el **Editor de expresiones** cuadro de diálogo. Para obtener más información sobre el uso de este cuadro de diálogo, vea el [Cómo: usar el Editor de expresiones](../workflow-designer/how-to-use-the-expression-editor.md) tema.|
|<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>|False|Especifica la colección de objetos <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializan varios objetos <xref:System.ServiceModel.Activities.CorrelationHandle> que configuran esta actividad <xref:System.ServiceModel.Activities.Receive> en el flujo de trabajo. Haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propiedad en la cuadrícula de propiedades para abrir el **agregar inicializadores de correlación** cuadro de diálogo. Para obtener más información sobre el uso de este cuadro, consulte la [cuadro de diálogo Agregar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) tema.|
|<xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A>|False|Especifica un valor que determina si una nueva instancia de flujo de trabajo se crea para procesar el mensaje en caso de que el mensaje no se correlacione con una instancia de flujo de trabajo existente. Si el valor se establece en **true**, se crea una nueva instancia de flujo de trabajo para procesar el mensaje cuando el mensaje no está correlacionado con una instancia de flujo de trabajo existente.|
|<xref:System.ServiceModel.Activities.Receive.KnownTypes%2A>|False|Especifica una colección de tipos conocidos para la operación de servicio implementada por esta actividad <xref:System.ServiceModel.Activities.Receive>. Esta propiedad se puede utilizar junto con el conjunto de propiedades <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> para <xref:System.Runtime.Serialization.DataContractSerializer>. Se ignorará si se usa <xref:System.Xml.Serialization.XmlSerializer>.<br /><br /> Haga clic en el botón de puntos suspensivos junto a la **KnownTypes** campo en la cuadrícula de propiedades para mostrar la **Editor de la colección de tipo** cuadro de diálogo con el que puede agregar los tipos pertinentes. Para obtener más información sobre el uso de este cuadro, consulte la [cuadro de diálogo de Editor de colección de tipo](../workflow-designer/type-collection-editor-dialog-box.md) tema.|
|<xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A>|False|Especifica la enumeración <xref:System.Net.Security.ProtectionLevel> para el mensaje.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> significa únicamente la autenticación.<br />2. <xref:System.Net.Security.ProtectionLevel> significa firma datos para ayudar a garantizar la integridad de los datos transmitidos.<br />3. <xref:System.Net.Security.ProtectionLevel> significa cifrar y firmar datos para ayudar a garantizar la confidencialidad e integridad de los datos transmitidos.|
|<xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>|False|Especifica el tipo de serializador que se va a utilizar para la operación de servicio que implementa la actividad <xref:System.ServiceModel.Activities.Receive>. El valor predeterminado es <xref:System.Runtime.Serialization.DataContractSerializer>, que serializa y deserializa una instancia de un tipo en una secuencia o en un documento XML que utilice un contrato de datos que se haya proporcionado. Se puede utilizar también <xref:System.Xml.Serialization.XmlSerializer> si se requiere un mayor control de XML.|
|<xref:System.ServiceModel.Activities.Receive.Action%2A>|False|Especifica el encabezado de acción del mensaje. Si no se establece explícitamente, su valor predeterminado es: https://tempuri.org/{service espacio de nombres del contrato} / {nombre del contrato de servicio} / {nombre de la operación}.|

## <a name="see-also"></a>Vea también

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)