---
title: Ribbon XML
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.Ribbon.RibbonXMLItem
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- callback methods
- custom Ribbon, displaying
- custom Ribbon, defining behavior
- XML [Office development in Visual Studio], Ribbon
- customizing the Ribbon, defining behavior
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, displaying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e9ce2388dbf61ef3af524f0debc776891dca004f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842554"
---
# <a name="ribbon-xml"></a>Ribbon XML
  El elemento cinta (XML) le permite personalizar una cinta de opciones mediante XML. Use el elemento cinta (XML) Si desea personalizar la cinta de modo que no sea compatible con el elemento cinta (diseñador visual). Para obtener una comparación de lo que puede hacer con cada elemento, consulte [información general de la cinta](../vsto/Ribbon-overview.md)de opciones.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="add-a-ribbon-xml-item-to-a-project"></a>Agregar un elemento cinta (XML) a un proyecto
 Puede agregar un elemento **Cinta (XML)** a cualquier proyecto de Office desde el cuadro de diálogo **Agregar nuevo elemento** . Visual Studio agrega automáticamente los siguientes archivos al proyecto:

- Un archivo XML de la cinta de opciones. Este archivo define la interfaz de usuario de la cinta de opciones. Use este archivo para agregar elementos de la interfaz de usuario, como pestañas, grupos y controles. Para obtener más información, vea [referencia de archivo XML de la cinta](#RibbonDescriptorFile) de opciones más adelante en este tema.

- Un archivo de código de la cinta de opciones. Este archivo contiene la *clase Ribbon*. Esta clase tiene el nombre que especificó para el elemento **Cinta (XML)** en el cuadro de diálogo **Agregar nuevo elemento** . Microsoft Office aplicaciones usan una instancia de esta clase para cargar la cinta de opciones personalizada. Para obtener más información, vea [referencia de la clase Ribbon](#RibbonExtensionClass) más adelante en este tema.

  De forma predeterminada, estos archivos agregan un grupo personalizado a la pestaña **Complementos** de la cinta de opciones.

## <a name="display-the-custom-ribbon-in-a-microsoft-office-application"></a>Mostrar la cinta de opciones personalizada en una aplicación Microsoft Office
 Después de agregar un elemento **cinta (XML)** al proyecto, debe agregar código a la clase **ThisAddIn**, **ThisWorkbook**o **ThisDocument** que reemplaza el `CreateRibbonExtensibilityObject` método y devuelve la clase XML de la cinta de opciones a la aplicación de Office.

 En el siguiente código de ejemplo se reemplaza el método `CreateRibbonExtensibilityObject` y devuelve una clase XML Ribbon llamada MyRibbon.

 [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
 [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

## <a name="define-the-behavior-of-the-custom-ribbon"></a>Definir el comportamiento de la cinta de opciones personalizada
 Puede responder a las acciones del usuario, como hacer clic en un botón de la cinta de opciones, creando *métodos de devolución de llamada*. Los métodos de devolución de llamada son similares a los eventos de los controles de Windows Forms, pero se identifican con un atributo en el código XML del elemento de la interfaz de usuario. Cuando escribe métodos en la clase Ribbon, un control llama al método que tiene el mismo nombre que el valor del atributo. Por ejemplo, puede crear un método de devolución de llamada al que se llama cuando un usuario hace clic en un botón de la cinta de opciones. Es necesario llevar a cabo dos pasos para crear un método de devolución de llamada:

- Asigne a un control del archivo XML de la cinta de opciones un atributo que identifique un método de devolución de llamada en el código.

- Defina el método de devolución de llamada en la clase Ribbon.

> [!NOTE]
> Outlook requiere un paso adicional. Para obtener más información, consulte [personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

 Para ver un tutorial que muestra cómo automatizar una aplicación desde la cinta de opciones, consulte [Tutorial: crear una pestaña personalizada usando XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)de la cinta.

### <a name="assign-callback-methods-to-controls"></a>Asignar métodos de devolución de llamada a controles
 Para asignar un método de devolución de llamada a un control en el archivo XML de la cinta de opciones, agregue un atributo que especifique el tipo del método de devolución de llamada y el nombre del método. Por ejemplo, el siguiente elemento define un botón de alternancia que tiene un método de devolución de llamada **onAction** llamado `OnToggleButton1`.

```xml
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />
```

 Se llama a**onAction** cuando el usuario efectúa la tarea principal asociada a un control determinado. Por ejemplo, se llama al método de devolución de llamada **onAction** de un botón de alternancia cuando el usuario hace clic en el botón.

 El método que especifique en el atributo puede tener cualquier nombre. Sin embargo, debe coincidir con el nombre del método que defina en el archivo de código de la cinta de opciones.

 Hay muchos tipos diferentes de métodos de devolución de llamada que se pueden asignar a los controles de la cinta de opciones. Para obtener una lista completa de los métodos de devolución de llamada disponibles para cada control, consulte el artículo técnico personalización de la interfaz de usuario de la [cinta de opciones de Office (2007) para desarrolladores (parte 3 de 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12)).

### <a name="define-callback-methods"></a><a name="CallBackMethods"></a> Definir métodos de devolución de llamada
 Defina los métodos de devolución de llamada en la clase Ribbon en el archivo de código de la cinta de opciones. Un método de devolución de llamada tiene varios requisitos:

- Debe declararse como público.

- Su nombre debe coincidir con el nombre de un método de devolución de llamada asignado a un control en el archivo XML de la cinta de opciones.

- Su firma debe coincidir con la de un tipo de método de devolución de llamada que esté disponible para el control de cinta de opciones asociado.

  Para obtener una lista completa de las firmas del método de devolución de llamada para los controles de la cinta de opciones, consulte el artículo técnico [personalizar la interfaz de usuario de la cinta de opciones de Office (2007) para desarrolladores (parte 3 de 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12)). Visual Studio no proporciona compatibilidad con IntelliSense para los métodos de devolución de llamada que se crean en el archivo de código de la cinta de opciones. Si crea un método de devolución de llamada que no coincide con una firma válida, se compilará el código, pero no ocurrirá nada cuando el usuario haga clic en el control.

  Todos los métodos de devolución de llamada tienen un parámetro <xref:Microsoft.Office.Core.IRibbonControl> que representa el control que llamó al método. Puede usar este parámetro para reutilizar el mismo método de devolución de llamada en varios controles. En el siguiente ejemplo de código se muestra un método de devolución de llamada **onAction** que efectúa diferentes tareas según el control en el que el usuario hace clic.

  [!code-csharp[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#2)]
  [!code-vb[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#2)]

## <a name="ribbon-xml-file-reference"></a><a name="RibbonDescriptorFile"></a> Referencia de archivo XML de la cinta
 Puede definir la cinta de opciones personalizada agregando elementos y atributos al archivo XML de la cinta de opciones. De forma predeterminada, el archivo XML de la cinta de opciones contiene el siguiente código XML.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<customUI xmlns="http://schemas.microsoft.com/office/2006/01/customui" onLoad="OnLoad">
  <ribbon>
    <tabs>
      <tab idMso="TabAddIns">
        <group id="MyGroup"
               label="My Group">
        </group>
      </tab>
    </tabs>
  </ribbon>
</customUI>
```

 En la siguiente tabla se describen los elementos predeterminados del archivo XML de la cinta de opciones.

|Elemento|Descripción|
|-------------|-----------------|
|**customUI**|Representa la cinta de opciones personalizada en el proyecto de complemento de VSTO.|
|**cable**|Representa la cinta de opciones.|
|**columnas**|Representa un conjunto de pestañas de la cinta de opciones.|
|**ficha**|Representa una sola pestaña de la cinta de opciones.|
|**group**|Representa un grupo de controles en la pestaña de la cinta de opciones.|

 Estos elementos tienen atributos que especifican la apariencia y el comportamiento de la cinta de opciones personalizada. En la siguiente tabla se describen los atributos predeterminados del archivo XML de la cinta de opciones.

|Atributo|Elemento primario|Descripción|
|---------------|--------------------|-----------------|
|**Carga**|**customUI**|Identifica un método al que se llama cuando la aplicación carga la cinta de opciones.|
|**idMso**|**ficha**|Identifica una pestaña integrada que se va a mostrar en la cinta de opciones.|
|**id**|**group**|Identifica el grupo.|
|**label**|**group**|Especifica el texto que aparece en el grupo.|

 Los elementos y atributos predeterminados del archivo XML de la cinta de opciones son un subconjunto pequeño de los elementos y atributos disponibles. Para obtener una lista completa de los elementos y atributos disponibles, consulte el artículo técnico [Personalización de la interfaz de usuario de la cinta de opciones de Office (2007) para desarrolladores (parte 2 de 3)](/previous-versions/office/developer/office-2007/aa338199(v=office.12)).

## <a name="ribbon-class-reference"></a><a name="RibbonExtensionClass"></a> Referencia de clase Ribbon
 Visual Studio genera la clase Ribbon en el archivo de código de la cinta de opciones. Agregue los métodos de devolución de llamada para los controles de la cinta de opciones a esta clase. Esta clase implementa la interfaz <xref:Microsoft.Office.Core.IRibbonExtensibility>.

 En la siguiente tabla se describen los métodos predeterminados de esta clase.

|Método|Descripción|
|------------|-----------------|
|`GetCustomUI`|Devuelve el contenido del archivo XML de la cinta de opciones. Microsoft Office aplicaciones llaman a este método para obtener una cadena XML que define la interfaz de usuario de la cinta de opciones personalizada. Este método implementa el método <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> . **Nota:** `GetCustomUI` solo se debe implementar para devolver el contenido del archivo XML de la cinta de opciones; no debe usarse para inicializar el complemento de VSTO.   En particular, no debe intentar mostrar cuadros de diálogo u otras ventanas en la implementación `GetCustomUI` . De lo contrario, es posible que la cinta de opciones personalizada no se comporte correctamente. Si tiene que ejecutar código que inicialice el complemento de VSTO, agréguelo al controlador de eventos `ThisAddIn_Startup` .|
|`OnLoad`|Asigne el parámetro <xref:Microsoft.Office.Core.IRibbonControl> al campo `Ribbon` . Microsoft Office aplicaciones llaman a este método cuando cargan la cinta de opciones personalizada. Puede usar este campo para actualizar dinámicamente la cinta de opciones personalizada. Para obtener más información, consulte el artículo técnico [Personalización de la interfaz de usuario de la cinta de opciones de Office (2007) para desarrolladores (parte 1 de 3)](/previous-versions/office/developer/office-2007/aa338202(v=office.12)).|
|`GetResourceText`|Lo llama el método `GetCustomUI` para obtener el contenido del archivo XML de la cinta de opciones.|

## <a name="see-also"></a>Vea también
- [Información general sobre la cinta](../vsto/ribbon-overview.md)
- [Tutorial: crear una pestaña personalizada usando XML de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
