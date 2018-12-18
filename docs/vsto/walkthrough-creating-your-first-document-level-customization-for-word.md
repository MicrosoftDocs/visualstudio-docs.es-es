---
title: 'Tutorial: Crear la primera personalización de nivel de documento para Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1c5c25163a49e51b0759e57318d6119edec97983
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928820"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-word"></a>Tutorial: Crear la primera personalización de nivel de documento para Word
  En este tutorial introductorio se muestra cómo crear una personalización de nivel de documento para Microsoft Office Word. Las características que se crean en este tipo de solución solo están disponibles cuando se abre un documento concreto. No puede usar una personalización de nivel de documento para efectuar cambios en toda la aplicación, por ejemplo, para mostrar una nueva pestaña de la cinta de opciones cuando se abre un documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
- Crear un proyecto de documento de Word.  
  
- Agregar texto al documento hospedado en el diseñador de Visual Studio.  
  
- Escribir código que usa el modelo de objetos de Word para agregar texto al documento personalizado cuando se abre.  
  
- Compilar y ejecutar el proyecto para probarlo.  
  
- Limpiar el proyecto para quitar los archivos de compilación innecesarios y la configuración de seguridad del equipo de desarrollo.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-the-project"></a>Crear el proyecto  
  
### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>Para crear un nuevo proyecto de documento de Word en Visual Studio  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.  
  
3.  En el panel de plantillas, expanda **Visual C#** o **Visual Basic**y luego expanda **Office/SharePoint**.  
  
4.  En el nodo **Office/SharePoint** expandido, seleccione el nodo **Complementos de Office** .  
  
5.  En la lista de plantillas de proyecto, seleccione un proyecto de documento de VSTO de Word.  
  
6.  En el **nombre** , escriba **FirstDocumentCustomization**.  
  
7.  Haga clic en **Aceptar**.  
  
     Se abre el **Asistente para proyectos de Visual Studio Tools para Office** .  
  
8.  Seleccione **crear un nuevo documento**y haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el **FirstDocumentCustomization** del proyecto y agrega el **FirstDocumentCustomization** documento y el archivo de código ThisDocument al proyecto. El **FirstDocumentCustomization** documento se abre automáticamente en el diseñador.  
  
## <a name="close-and-reopen-the-document-in-the-designer"></a>Cierre y vuelva a abrir el documento en el diseñador  
 Puede volver a abrir el documento si lo cierra deliberada o accidentalmente en el diseñador mientras está desarrollando el proyecto.  
  
### <a name="to-close-and-reopen-the-document-in-the-designer"></a>Para cerrar y volver a abrir el documento en el diseñador  
  
1.  Cierre el documento, haga clic en el **cerrar** botón (X) de la ventana del diseñador.  
  
2.  En **el Explorador de soluciones**, haga clic en el **ThisDocument** archivo de código y haga clic en **Diseñador de vistas**.  
  
     \- o -  
  
     En **el Explorador de soluciones**, haga doble clic en el **ThisDocument** archivo de código.  
  
## <a name="add-text-to-the-document-in-the-designer"></a>Agregar texto al documento en el diseñador  
 Puede diseñar la interfaz de usuario de la personalización modificando el documento que está abierto en el diseñador. Por ejemplo, puede agregar texto, tablas o controles de Word. Para obtener más información sobre cómo usar el diseñador, vea [proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
### <a name="to-add-text-to-your-document-by-using-the-designer"></a>Para agregar texto al documento mediante el diseñador  
  
1.  En el documento que está abierto en el diseñador, escriba el siguiente texto.  
  
     **Este texto se agregó mediante el diseñador.**  
  
## <a name="add-text-to-the-document-programmatically"></a>Agregar texto al documento mediante programación  
 Luego, agregue código al archivo de código ThisDocument. El nuevo código usa el modelo de objetos de Word para agregar un segundo párrafo de texto al documento. De forma predeterminada, el archivo de código ThisDocument contiene el siguiente código generado:  
  
-   Una definición parcial de la clase `ThisDocument`, que representa el modelo de programación del documento y proporciona acceso al modelo de objetos de Word. Para obtener más información, consulte [elemento host Document](../vsto/document-host-item.md) y [información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md). El resto de la clase `ThisDocument` se define en un archivo de código oculto que no se debe modificar.  
  
-   Los controladores de eventos `ThisDocument_Startup` y `ThisDocument_Shutdown` . Se llama a estos controladores de eventos cuando se abre y se cierra el documento. Use estos controladores de eventos para inicializar la personalización cuando se abre el documento y para limpiar los recursos que usa la personalización cuando se cierra el documento. Para obtener más información, consulte [eventos en proyectos de Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>Para agregar un segundo párrafo de texto al documento mediante código  
  
1.  En **el Explorador de soluciones**, haga clic en **ThisDocument**y, a continuación, haga clic en **ver código**.  
  
     El archivo de código se abre en Visual Studio.  
  
2.  Reemplace el controlador de eventos `ThisDocument_Startup` por el siguiente código: Cuando se abre el documento, este código agrega un segundo párrafo de texto al documento.  
  
     [!code-vb[Trin_WordDocumentTutorial#1](../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb#1)]
     [!code-csharp[Trin_WordDocumentTutorial#1](../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs#1)]  
  
    > [!NOTE]  
    >  Este código usa el valor de índice 1 para tener acceso al primer párrafo de la propiedad <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A>. Aunque Visual Basic y Visual C# usan matrices basadas en 0, el límite de matriz inferior de la mayoría de las colecciones del modelo de objetos de Word es 1. Para obtener más información, consulte [escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="test-the-project"></a>El proyecto de prueba  
  
### <a name="to-test-your-document"></a>Para probar el documento  
  
1.  Presione **F5** para compilar y ejecutar el proyecto.  
  
     Al compilar el proyecto, el código se compila en un ensamblado que está asociado al documento. Visual Studio coloca una copia del documento y el ensamblado en la carpeta de resultados de compilación del proyecto y establece la configuración de seguridad en el equipo de desarrollo para permitir que se ejecute la personalización. Para obtener más información, consulte [soluciones de Office de compilación](../vsto/building-office-solutions.md).  
  
2.  En el documento, compruebe que ve el texto siguiente.  
  
     **Este texto se agregó mediante el diseñador.**  
  
     **Este texto se agregó mediante código.**  
  
3.  Cierre el documento.  
  
## <a name="clean-up-the-project"></a>Limpiar el proyecto  
 Cuando termine de desarrollar un proyecto, debe quitar los archivos de la carpeta de resultados de compilación y la configuración de seguridad creada por el proceso de compilación.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Para limpiar el proyecto completado en el equipo de desarrollo  
  
1.  En el menú **Crear** de Visual Studio, haga clic en **Limpiar solución**.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Ahora que ha creado una personalización de nivel de documento básico para Word, en los siguientes temas obtendrá más información sobre cómo desarrollar personalizaciones:  
  
-   Tareas de programación generales que puede realizar en las personalizaciones de nivel de documento: [programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md).  
  
-   Tareas de programación que son específicas de las personalizaciones de nivel de documento para Word: [soluciones de Word](../vsto/word-solutions.md).  
  
-   Mediante el modelo de objetos de Word: [información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md).  
  
-   Personalizar la interfaz de usuario de Word, por ejemplo, agregando una pestaña personalizada a la cinta de opciones o creando su propio panel de acciones: [personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
-   Usar objetos de Word extendidos proporcionados por las soluciones de Office en Visual Studio para realizar tareas que no son posibles con el modelo de objetos de Word (por ejemplo, hospedar controles administrados en documentos y enlazar controles de Word a datos mediante el uso de los datos de Windows Forms modelo de enlace): [automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md).  
  
-   Compilar y depurar personalizaciones de nivel de documento para Word: [soluciones de Office de compilación](../vsto/building-office-solutions.md).  
  
-   Implementar personalizaciones de nivel de documento para Word: [implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Soluciones de Word](../vsto/word-solutions.md)   
 [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)   
 [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Introducción a las plantillas de proyecto de Office](../vsto/office-project-templates-overview.md)  
  
  