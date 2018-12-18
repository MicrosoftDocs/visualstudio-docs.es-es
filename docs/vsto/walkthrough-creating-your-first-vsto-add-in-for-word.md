---
title: 'Tutorial: Crear el primer complemento VSTO para Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Word [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cf20b3f742bfc5ff6de6af080f3651f9d9027234
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940975"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-word"></a>Tutorial: Crear el primer complemento VSTO para Word
  Este tutorial introductorio muestra cómo crear un complemento de VSTO para Microsoft Office Word. Las características que cree en este tipo de solución estarán disponibles para la propia aplicación, con independencia de los documentos que estén abiertos.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
- Crear un proyecto de complemento de VSTO de Word.  
  
- Escribir código que usa el modelo de objetos de Word para agregar texto a un documento cuando se guarda.  
  
- Compilar y ejecutar el proyecto para probarlo.  
  
- Limpiar el proyecto completado para que el complemento de VSTO deje de ejecutarse automáticamente en el equipo de desarrollo.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-the-project"></a>Crear el proyecto  
  
### <a name="to-create-a-new-word-vsto-add-in-project-in-visual-studio"></a>Para crear un nuevo proyecto de complemento de VSTO de Word en Visual Studio  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.  
  
3.  En el panel de plantillas, expanda **Visual C#** o **Visual Basic**y luego expanda **Office/SharePoint**.  
  
4.  En el nodo **Office/SharePoint** expandido, seleccione el nodo **Complementos de Office** .  
  
5.  En la lista de plantillas de proyecto, seleccione un proyecto de complemento de VSTO de Word.  
  
6.  En el **nombre** , escriba **FirstWordAddIn**.  
  
7.  Haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el **FirstWordAddIn** del proyecto y abre el archivo de código ThisAddIn en el editor.  
  
## <a name="write-code-to-add-text-to-the-saved-document"></a>Escribir código para agregar texto al documento guardado  
 A continuación, agregue código al archivo de código ThisAddIn. El nuevo código usa el modelo de objetos de Word para agregar texto reutilizable a cada documento guardado. De forma predeterminada, el archivo de código ThisAddIn contiene el siguiente código generado:  
  
-   Una definición parcial de la clase `ThisAddIn` . Esta clase proporciona un punto de entrada para el código y proporciona acceso al modelo de objetos de Word. Para obtener más información, consulte [complementos VSTO de programa](../vsto/programming-vsto-add-ins.md). El resto de la clase `ThisAddIn` se define en un archivo de código oculto que no se debe modificar.  
  
-   Los controladores de eventos `ThisAddIn_Startup` y `ThisAddIn_Shutdown` . Se llama a estos controladores de eventos cuando Word carga y descarga el complemento de VSTO. Use estos controladores de eventos para inicializar el complemento de VSTO cuando se cargue y para limpiar los recursos que usa el complemento de VSTO cuando se descargue. Para obtener más información, consulte [eventos en proyectos de Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-paragraph-of-text-to-the-saved-document"></a>Para agregar un párrafo de texto al documento guardado  
  
1. En el archivo de código ThisAddIn, agregue el código siguiente a la clase `ThisAddIn` . El nuevo código define un controlador de eventos para el evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>, que se desencadena cuando se guarda un documento.  
  
    Cuando el usuario guarda un documento, el controlador de eventos agrega el nuevo texto al principio del documento.  
  
    [!code-vb[Trin_WordAddInTutorial#1](../vsto/codesnippet/VisualBasic/FirstWordAddIn/ThisAddIn.vb#1)]
    [!code-csharp[Trin_WordAddInTutorial#1](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#1)]  
  
   > [!NOTE]  
   >  Este código usa un valor de índice 1 para acceder al primer párrafo de la colección <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A>. Aunque Visual Basic y Visual C# usan matrices basadas en 0, el límite de matriz inferior de la mayoría de las colecciones del modelo de objetos de Word es 1. Para obtener más información, consulte [escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md).  
  
2. Si está utilizando C#, agregue el siguiente código necesario para el controlador de eventos `ThisAddIn_Startup` . Este código se utiliza para conectar el controlador de eventos `Application_DocumentBeforeSave` con el evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> .  
  
    [!code-csharp[Trin_WordAddInTutorial#2](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#2)]  
  
   Para modificar el documento cuando se guarda, los ejemplos de código anteriores usan los siguientes objetos:  
  
-   El campo `Application` de la clase `ThisAddIn`. El campo `Application` devuelve un objeto <xref:Microsoft.Office.Interop.Word.Application> que representa la instancia actual de Word.  
  
-   El parámetro `Doc` del controlador de eventos para el evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> . El parámetro `Doc` es un objeto <xref:Microsoft.Office.Interop.Word.Document> que representa el documento guardado. Para obtener más información, consulte [información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md).  
  
## <a name="test-the-project"></a>El proyecto de prueba  
  
### <a name="to-test-the-project"></a>Para probar el proyecto  
  
1.  Presione **F5** para compilar y ejecutar el proyecto.  
  
     Al compilar el proyecto, el código se compila en un ensamblado que se incluye en la carpeta de salida de compilación del proyecto. Visual Studio crea también un conjunto de entradas del Registro que permiten que Word detecte y cargue el complemento de VSTO, y establece la configuración de seguridad en el equipo de desarrollo para permitir la ejecución del complemento de VSTO. Para obtener más información, consulte [soluciones de Office de compilación](../vsto/building-office-solutions.md).  
  
2.  En Word, guarde el documento activo.  
  
3.  Compruebe que el texto siguiente se agrega al documento.  
  
     **Este texto se agregó mediante código.**  
  
4.  Cierre Word.  
  
## <a name="clean-up-the-project"></a>Limpiar el proyecto  
 Cuando termine de desarrollar un proyecto, quite el ensamblado del complemento de VSTO, las entradas del registro y la configuración de seguridad del equipo de desarrollo. De lo contrario, el complemento de VSTO se ejecutará cada vez que abra Word en el equipo de desarrollo.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Para limpiar el proyecto completado en el equipo de desarrollo  
  
1.  En el menú **Crear** de Visual Studio, haga clic en **Limpiar solución**.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Ahora que ya creó creado un complemento básico de VSTO para Word, puede obtener más información sobre cómo desarrollar complementos de VSTO en estos temas:  
  
-   Tareas de programación generales que puede realizar en complementos VSTO: [complementos VSTO de programa](../vsto/programming-vsto-add-ins.md).  
  
-   Tareas de programación que son específicas de los complementos de VSTO de Word: [soluciones de Word](../vsto/word-solutions.md).  
  
-   Mediante el modelo de objetos de Word: [información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md).  
  
-   Personalizar la interfaz de usuario de Word, por ejemplo, agregando una pestaña personalizada a la cinta de opciones o creando su propio panel de tareas personalizado: [personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
-   Compilar y depurar complementos de VSTO para Word: [soluciones de Office de compilación](../vsto/building-office-solutions.md).  
  
-   Implementar complementos de VSTO para Word: [implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Soluciones de Word](../vsto/word-solutions.md)   
 [Programar complementos VSTO](../vsto/programming-vsto-add-ins.md)   
 [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Introducción a las plantillas de proyecto de Office](../vsto/office-project-templates-overview.md)  
  
  