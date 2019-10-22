---
title: 'Tutorial: Crear el primer complemento de VSTO para Outlook'
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Outlook [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: baedd24b7eba14b3f2fa6496a7a681773b81cb9b
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547981"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-outlook"></a>Tutorial: Crear el primer complemento de VSTO para Outlook
  Este tutorial muestra cómo crear un complemento de VSTO para Microsoft Office Outlook. Las características que cree en este tipo de solución estarán disponibles para la propia aplicación, con independencia del elemento de Outlook que se abra. Para obtener más información, vea [información general sobre &#40;el&#41;desarrollo de soluciones de Office VSTO](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 En este tutorial se muestran las tareas siguientes:

- Crear un proyecto de complemento VSTO de Outlook para Outlook.

- Escribir código que use el modelo de objetos de Outlook para agregar texto al asunto y al cuerpo de un nuevo mensaje de correo.

- Compilar y ejecutar el proyecto para probarlo.

- Limpiar el proyecto completado para que el complemento de VSTO deje de ejecutarse automáticamente en el equipo de desarrollo.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesita los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-the-project"></a>Crear el proyecto

### <a name="to-create-a-new-outlook-project-in-visual-studio"></a>Para crear un nuevo proyecto de Outlook en Visual Studio

1. Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.

3. En el panel de plantillas, expanda **Visual C#** o **Visual Basic**y luego expanda **Office/SharePoint**.

4. En el nodo **Office/SharePoint** expandido, seleccione el nodo **Complementos de Office** .

5. En la lista de plantillas de proyecto, elija un proyecto de complemento VSTO de Outlook.

6. En el cuadro **Nombre** , escriba **FirstOutlookAddIn**.

7. Haga clic en **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el proyecto **FirstOutlookAddIn** y abre el archivo de código **ThisAddIn** en el editor.

## <a name="write-code-that-adds-text-to-each-new-mail-message"></a>Escribir código que agregue texto a cada nuevo mensaje de correo
 A continuación, agregue código al archivo de código ThisAddIn. El nuevo código usa el modelo de objetos de Outlook para agregar texto a cada nuevo mensaje de correo. De forma predeterminada, el archivo de código ThisAddIn contiene el siguiente código generado:

- Una definición parcial de la clase `ThisAddIn` . Esta clase proporciona un punto de entrada para el código y proporciona acceso al modelo de objetos de Outlook. Para obtener más información, vea complementos de [VSTO de programas](../vsto/programming-vsto-add-ins.md). El resto de la clase `ThisAddIn` se define en un archivo de código oculto que no se debe modificar.

- Los controladores de eventos `ThisAddIn_Startup` y `ThisAddIn_Shutdown` . Se llama a estos controladores de eventos cuando Outlook carga y descarga el complemento VSTO. Use estos controladores de eventos para inicializar el complemento de VSTO cuando se cargue y para limpiar los recursos que usa el complemento de VSTO cuando se descargue. Para obtener más información, vea [eventos en proyectos de Office](../vsto/events-in-office-projects.md).

### <a name="to-add-text-to-the-subject-and-body-of-each-new-mail-message"></a>Para agregar texto al asunto y al cuerpo de cada nuevo mensaje de correo

1. En el archivo de código ThisAddIn, declare un campo denominado `inspectors` en la clase `ThisAddIn` . El campo `inspectors` mantiene una referencia a la colección de ventanas de Inspector en la instancia actual de Outlook. Esta referencia impide que el recolector de elementos no usados libere la memoria que contiene el controlador de eventos para el evento <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> .

    [!code-vb[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#1)]

2. Reemplace el método `ThisAddIn_Startup` por el código siguiente. Este código asocia un controlador de eventos al evento <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> .

    [!code-vb[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#2)]
    [!code-csharp[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#2)]

3. En el archivo de código ThisAddIn, agregue el código siguiente a la clase `ThisAddIn` . Este código define un controlador de eventos para el evento <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> .

    Cuando el usuario crea un nuevo mensaje de correo, este controlador de eventos agrega texto a la línea de asunto y al cuerpo del mensaje.

    [!code-vb[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#3)]
    [!code-csharp[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#3)]

   Para modificar cada nuevo mensaje de correo, los ejemplos de código anteriores usan los siguientes objetos:

- El campo `Application` de la clase `ThisAddIn` . El campo `Application` devuelve un objeto <xref:Microsoft.Office.Interop.Outlook.Application> que representa la instancia actual de Outlook.

- El parámetro `Inspector` del controlador de eventos para el evento <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> . El parámetro `Inspector` es un objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> , que representa la ventana del Inspector del nuevo mensaje de correo. Para obtener más información, vea [soluciones de Outlook](../vsto/outlook-solutions.md).

## <a name="test-the-project"></a>Probar el proyecto
 Al compilar y ejecutar el proyecto, compruebe que el texto aparece en la línea de asunto y en el cuerpo de un nuevo mensaje de correo.

### <a name="to-test-the-project"></a>Para probar el proyecto

1. Presione **F5** para compilar y ejecutar el proyecto.

     Al compilar el proyecto, el código se compila en un ensamblado que se incluye en la carpeta de salida de compilación del proyecto. Visual Studio crea también un conjunto de entradas del registro que permiten que Outlook detecte y cargue el complemento de VSTO, y establece la configuración de seguridad en el equipo de desarrollo para permitir la ejecución del complemento de VSTO. Para obtener más información, vea [información general del proceso de compilación de soluciones de Office](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md).

2. En Outlook, cree un nuevo mensaje de correo.

3. Compruebe que el siguiente texto se agrega a la línea de asunto y al cuerpo del mensaje.

     **Este texto se agregó mediante código.**

4. Cierre Outlook.

## <a name="clean-up-the-project"></a>Limpiar el proyecto
 Cuando termine de desarrollar un proyecto, quite el ensamblado del complemento de VSTO, las entradas del registro y la configuración de seguridad del equipo de desarrollo. De lo contrario, el complemento VSTO se ejecutará cada vez que abra Outlook en el equipo de desarrollo.

### <a name="to-clean-up-your-project"></a>Para limpiar el proyecto

1. En el menú **Crear** de Visual Studio, haga clic en **Limpiar solución**.

## <a name="next-steps"></a>Pasos siguientes
 Ahora que ha creado un complemento básico de VSTO para Outlook, puede obtener más información sobre cómo desarrollar complementos VSTO en estos temas:

- Tareas de programación generales que puede realizar mediante el uso de complementos VSTO para Outlook. Para obtener más información, vea complementos de [VSTO de programas](../vsto/programming-vsto-add-ins.md).

- Usar el modelo de objetos de Outlook. Para obtener más información, vea [soluciones de Outlook](../vsto/outlook-solutions.md).

- Personalizar la interfaz de usuario (UI) de Outlook, por ejemplo, agregando una pestaña personalizada a la cinta o creando su propio panel de tareas personalizado. Para obtener más información, consulte Personalización de la [interfaz de usuario de Office](../vsto/office-ui-customization.md).

- Compilar y depurar los complementos de VSTO para Outlook. Para obtener más información, vea compilar [soluciones de Office](../vsto/building-office-solutions.md).

- Implementar complementos de VSTO para Outlook. Para obtener más información, vea [implementar una solución de Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Vea también
- [Complementos de VSTO de programa](../vsto/programming-vsto-add-ins.md)
- [Soluciones de Outlook](../vsto/outlook-solutions.md)
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [Compilar soluciones de Office](../vsto/building-office-solutions.md)
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
- [Información general de plantillas de proyecto de Office](../vsto/office-project-templates-overview.md)
