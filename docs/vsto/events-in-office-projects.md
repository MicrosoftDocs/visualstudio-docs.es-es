---
title: Eventos en proyectos de Office
description: Obtenga información sobre cómo cada plantilla de proyecto de Office genera varios controladores de eventos y cómo esos controladores de eventos son ligeramente diferentes de los controladores de eventos de los complementos de VSTO.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Sheet1_Startup
- ThisDocument_Shutdown
- ThisDocument_Startup
- application-level add-ins [Office development in Visual Studio], events
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- Sheet2_Startup
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio], events
- Sheet2_Shutdown
- Startup event
- Sheet3_Shutdown
- add-ins [Office development in Visual Studio], events
- Shutdown event
- ThisAddIn_Startup
- Sheet3_Startup
- Startup method [Office development in Visual Studio]
- Shutdown method [Office development in Visual Studio]
- Sheet1_Shutdown
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7bf4da3f0b2dd9cbab960a779690aa752744cdae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910322"
---
# <a name="events-in-office-projects"></a>Eventos en proyectos de Office
  Cada plantilla de proyecto de Office genera automáticamente varios controladores de eventos. Los controladores de eventos de las personalizaciones de nivel de documento son ligeramente diferentes de los controladores de eventos de los complementos de VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="document-level-projects"></a>Proyectos de nivel de documento
 Visual Studio proporciona código generado subyacente en documentos nuevos o existentes o en hojas de cálculo para las personalizaciones de nivel de documento. Este código genera dos eventos diferentes: **Startup** y **Shutdown**.

### <a name="startup-event"></a>Startup (evento)
 El evento **Startup** se desencadena para cada uno de los elementos host (documento, libro u hoja de cálculo) cuando el documento está en ejecución y ya se ha ejecutado todo el código de inicialización del ensamblado. Es lo último que se ejecuta en el constructor de la clase en la que se ejecuta el código. Para obtener más información sobre los elementos host, vea [información general sobre elementos y controles](../vsto/host-items-and-host-controls-overview.md)host.

 Cuando se crea un proyecto de nivel de documento, Visual Studio crea controladores de eventos para el evento **Startup** en los archivos de código generado:

- En los proyectos de Microsoft Office Word, el controlador de eventos se denomina `ThisDocument_Startup`.

- En los proyectos de Microsoft Office Excel, los controladores de eventos tienen los nombres siguientes:

  - `Sheet1_Startup`

  - `Sheet2_Startup`

  - `Sheet3_Startup`

  - `ThisWorkbook_Startup`

### <a name="shutdown-event"></a>Shutdown (evento)
 El evento **Shutdown** se desencadena para cada uno de los elementos host (documento u hoja de cálculo) cuando el dominio de aplicación en el que se ha cargado el código está a punto de descargarse. Es lo último a lo que se llama en la clase cuando se descarga.

 Cuando se crea un proyecto de nivel de documento, Visual Studio crea controladores de eventos para el evento **Shutdown** en los archivos de código generado:

- En los proyectos de Microsoft Office Word, el controlador de eventos se denomina `ThisDocument_Shutdown`.

- En los proyectos de Microsoft Office Excel, los controladores de eventos tienen los nombres siguientes:

  - `Sheet1_Shutdown`

  - `Sheet2_Shutdown`

  - `Sheet3_Shutdown`

  - `ThisWorkbook_Shutdown`

> [!NOTE]
> No quite controles mediante programación durante el controlador de eventos **Shutdown** del documento. Los elementos de la interfaz de usuario del documento ya no están disponibles cuando se produce el evento **Shutdown** . Si desea quitar controles antes de que se cierre la aplicación, agregue el código a otro controlador de eventos, como **BeforeClose** o **BeforeSave**.

### <a name="event-handler-method-declarations"></a>Declaraciones de método de controlador de eventos
 Todas las declaraciones del método de controlador de eventos reciben los mismos argumentos que se les pasan: *sender* y *e*. En Excel, el argumento *sender* hace referencia a la hoja, como `Sheet1` o `Sheet2`; en Word, el argumento *sender* hace referencia al documento. El argumento *e* hace referencia a los argumentos estándar de un evento, que no se usan en este caso.

 El ejemplo de código siguiente muestra los controladores de eventos predeterminados en los proyectos de nivel de documento para Word.

 [!code-vb[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#121)]
 [!code-csharp[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#121)]

 El ejemplo de código siguiente muestra los controladores de eventos predeterminados en los proyectos de nivel de documento para Excel.

> [!NOTE]
> En el ejemplo de código siguiente se muestran los controladores de eventos de la clase `Sheet1` . Los nombres de los controladores de eventos de otras clases del elemento host corresponden al nombre de la clase. Por ejemplo, en la clase `Sheet2` , el controlador de eventos **Startup** se denomina `Sheet2_Startup`. En la clase `ThisWorkbook` , el controlador de eventos **Startup** se denomina `ThisWorkbook_Startup`.

 [!code-csharp[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#83)]

### <a name="order-of-events-in-document-level-excel-projects"></a>Orden de eventos en proyectos de Excel de nivel de documento
 Los controladores de eventos **Startup** en proyectos de Excel se llaman en este orden:

1. `ThisWorkbook_Startup`.

2. `Sheet1_Startup`.

3. `Sheet2_Startup`.

4. `Sheet3_Startup`.

5. Otras hojas en orden.

   Los controladores de eventos **Shutdown** en una solución de libro se llaman en este orden:

6. `ThisWorkbook_Shutdown`.

7. `Sheet1_Shutdown`.

8. `Sheet2_Shutdown`.

9. `Sheet3_Shutdown`.

10. Otras hojas en orden.

    El orden se determina cuando se compila el proyecto. Si el usuario reorganiza las hojas en tiempo de ejecución, no cambia el orden en que los eventos se desencadenan la siguiente vez que se abre o cierra el libro.

## <a name="vsto-add-in-projects"></a>Proyectos de complemento de VSTO
 Visual Studio proporciona código generado en los complementos de VSTO. Este código genera dos eventos diferentes: <xref:Microsoft.Office.Tools.AddInBase.Startup> y <xref:Microsoft.Office.Tools.AddInBase.Shutdown> .

### <a name="startup-event"></a>Startup (evento)
 El evento <xref:Microsoft.Office.Tools.AddIn.Startup> se desencadena cuando se ha cargado el complemento de VSTO y se ha ejecutado todo el código de inicialización del ensamblado. Este evento está controlado por el método `ThisAddIn_Startup` en el archivo de código generado.

 El código del controlador de eventos `ThisAddIn_Startup` es el primer código de usuario que se ejecuta, a menos que el complemento de VSTO invalide el método <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . En ese caso, se llama al controlador de eventos `ThisAddIn_Startup` después de <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>.

 No agregue código en el `ThisAdd-In_Startup` controlador de eventos si el código requiere que un documento esté abierto. En su lugar, agregue ese código a un evento que sea generado por la aplicación de Office cuando un usuario cree o abra un documento. Para obtener más información, vea [acceso a un documento cuando se inicia la aplicación de Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 Para obtener más información sobre la secuencia de inicio de los complementos de VSTO, consulte arquitectura de los complementos [de VSTO](../vsto/architecture-of-vsto-add-ins.md).

### <a name="shutdown-event"></a>Shutdown (evento)
 El evento <xref:Microsoft.Office.Tools.AddInBase.Shutdown> se desencadena cuando el dominio de aplicación en el que se ha cargado el código está a punto de descargarse. Este evento está controlado por el método `ThisAddIn_Shutdown` en el archivo de código generado. Este controlador de eventos es el último código de usuario que se ejecuta cuando se descarga el complemento de VSTO.

#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Evento shutdown en los complementos de VSTO de Outlook
 El evento <xref:Microsoft.Office.Tools.AddInBase.Shutdown> solo se desencadena cuando el usuario deshabilita el complemento de VSTO mediante el cuadro de diálogo Complementos COM de Outlook. No se desencadena cuando se cierra Outlook. Si tiene código que se debe ejecutar cuando Outlook se cierra, controle uno de los siguientes eventos:

- El evento <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> del objeto <xref:Microsoft.Office.Interop.Outlook.Application> .

- El evento <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> del objeto <xref:Microsoft.Office.Interop.Outlook.Explorer> .

> [!NOTE]
> Puede modificar el Registro para forzar a Outlook a desencadenar el evento <xref:Microsoft.Office.Tools.AddInBase.Shutdown> cuando salga. Sin embargo, si un administrador cambia esta configuración, cualquier código que agregue al método `ThisAddIn_Shutdown` dejará de ejecutarse al salir de Outlook. Para obtener más información, consulte [cambios de apagado para Outlook 2010](/previous-versions/office/developer/office-2010/ee720183(v=office.14)).

## <a name="see-also"></a>Vea también
- [Desarrollo de soluciones de Office](../vsto/developing-office-solutions.md)
- [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Personalizaciones de nivel de documento de programa](../vsto/programming-document-level-customizations.md)
- [Complementos de VSTO de programa](../vsto/programming-vsto-add-ins.md)
- [Información general de plantillas de proyecto de Office](../vsto/office-project-templates-overview.md)
