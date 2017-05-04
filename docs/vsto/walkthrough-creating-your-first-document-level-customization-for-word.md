---
title: "Tutorial: Crear la primera personalizaci&#243;n en el nivel del documento para Word | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "personalizaciones de nivel de documento [desarrollo de Office en Visual Studio], crear el primer proyecto"
  - "desarrollo de Office en Visual Studio, crear el primer proyecto"
  - "Word [desarrollo de Office en Visual Studio], crear el primer proyecto"
ms.assetid: ec9f5173-0923-4aee-985a-e760e80eaae3
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Tutorial: Crear la primera personalizaci&#243;n en el nivel del documento para Word
  En este tutorial introductorio se muestra cómo crear una personalización de nivel de documento para Microsoft Office Word.  Las características que se crean en este tipo de solución solo están disponibles cuando se abre un documento concreto.  No puede usar una personalización de nivel de documento para efectuar cambios en toda la aplicación, por ejemplo, para mostrar una nueva pestaña de la cinta de opciones cuando se abre un documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un proyecto de documento de Word.  
  
-   Agregar texto al documento hospedado en el diseñador de Visual Studio.  
  
-   Escribir código que usa el modelo de objetos de Word para agregar texto al documento personalizado cuando se abre.  
  
-   Compilar y ejecutar el proyecto para probarlo.  
  
-   Limpiar el proyecto para quitar los archivos de compilación innecesarios y la configuración de seguridad del equipo de desarrollo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## Crear el proyecto  
  
#### Para crear un nuevo proyecto de documento de Word en Visual Studio  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En el menú **Archivo**, elija **Nuevo** y haga clic en **Proyecto**.  
  
3.  En el panel de plantillas, expanda **Visual C\#** o  **Visual Basic** y luego expanda **Office\/SharePoint**.  
  
4.  En el nodo **Office\/SharePoint** expandido, seleccione el nodo **Complementos de Office**.  
  
5.  En la lista de plantillas de proyecto, seleccione un proyecto de documento de VSTO de Word.  
  
6.  En el cuadro **Nombre**, escriba **FirstDocumentCustomization**.  
  
7.  Haga clic en **Aceptar**.  
  
     Se abre el **Asistente para proyectos de Visual Studio Tools para Office**.  
  
8.  Seleccione **Crear un nuevo documento** y haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el proyecto **FirstDocumentCustomization** y agrega el documento **FirstDocumentCustomization** y el archivo de código ThisDocument al proyecto.  El documento **FirstDocumentCustomization** se abre automáticamente en el diseñador.  
  
## Cerrar y volver a abrir el documento en el diseñador  
 Puede volver a abrir el documento si lo cierra deliberada o accidentalmente en el diseñador mientras está desarrollando el proyecto.  
  
#### Para cerrar y volver a abrir el documento en el diseñador  
  
1.  Cierre el documento haciendo clic en el botón **Cerrar** \(X\) de la ventana del diseñador.  
  
2.  En el **Explorador de soluciones**, haga clic con el botón derecho en el archivo de código **ThisDocument** y haga clic en **Ver diseñador**.  
  
     o bien  
  
     En el **Explorador de soluciones**, haga doble clic en el archivo de código **ThisDocument**.  
  
## Agregar texto al documento en el diseñador  
 Puede diseñar la interfaz de usuario de la personalización modificando el documento que está abierto en el diseñador.  Por ejemplo, puede agregar texto, tablas o controles de Word.  Para obtener más información sobre cómo usar el diseñador, consulte [Proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
#### Para agregar texto al documento mediante el diseñador  
  
1.  En el documento que está abierto en el diseñador, escriba el siguiente texto.  
  
     **Este texto se agregó mediante el diseñador.**  
  
## Agregar texto al documento mediante programación  
 Luego, agregue código al archivo de código ThisDocument.  El nuevo código usa el modelo de objetos de Word para agregar un segundo párrafo de texto al documento.  De forma predeterminada, el archivo de código ThisDocument contiene el siguiente código generado:  
  
-   Una definición parcial de la clase `ThisDocument`, que representa el modelo de programación del documento y proporciona acceso al modelo de objetos de Word.  Para obtener más información, consulte [Elemento host Document](../vsto/document-host-item.md) e [Información general acerca del modelo de objetos de Word](../vsto/word-object-model-overview.md).  El resto de la clase `ThisDocument` se define en un archivo de código oculto que no se debe modificar.  
  
-   Los controladores de eventos `ThisDocument_Startup` y `ThisDocument_Shutdown`.  Se llama a estos controladores de eventos cuando se abre y se cierra el documento.  Use estos controladores de eventos para inicializar la personalización cuando se abre el documento y para limpiar los recursos que usa la personalización cuando se cierra el documento.  Para obtener más información, consulte [Eventos de los proyectos de Office](../vsto/events-in-office-projects.md).  
  
#### Para agregar un segundo párrafo de texto al documento mediante código  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en **ThisDocument** y haga clic en **Ver código**.  
  
     El archivo de código se abre en Visual Studio.  
  
2.  Reemplace el controlador de eventos `ThisDocument_Startup` por el siguiente código.  Cuando se abre el documento, este código agrega un segundo párrafo de texto al documento.  
  
     [!code-csharp[Trin_WordDocumentTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordDocumentTutorial/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_WordDocumentTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordDocumentTutorial/VB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  Este código usa el valor de índice 1 para tener acceso al primer párrafo de la propiedad <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A>.  Aunque Visual Basic y Visual C\# usan matrices basadas en 0, el límite de matriz inferior de la mayoría de las colecciones del modelo de objetos de Word es 1.  Para obtener más información, consulte [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md).  
  
## Probar el proyecto  
  
#### Para probar el documento  
  
1.  Presione **F5** para compilar y ejecutar el proyecto.  
  
     Al compilar el proyecto, el código se compila en un ensamblado que está asociado al documento.  Visual Studio coloca una copia del documento y el ensamblado en la carpeta de resultados de compilación del proyecto y establece la configuración de seguridad en el equipo de desarrollo para permitir que se ejecute la personalización.  Para obtener más información, consulte [Compilar soluciones de Office](../vsto/building-office-solutions.md).  
  
2.  En el documento, compruebe que ve el texto siguiente.  
  
     **Este texto se agregó mediante el diseñador.**  
  
     **Este texto se agregó mediante código.**  
  
3.  Cierre el documento.  
  
## Limpiar el proyecto  
 Cuando termine de desarrollar un proyecto, debe quitar los archivos de la carpeta de resultados de compilación y la configuración de seguridad creada por el proceso de compilación.  
  
#### Para limpiar el proyecto completado en el equipo de desarrollo  
  
1.  En el menú **Compilar** de Visual Studio, haga clic en **Limpiar solución**.  
  
## Pasos siguientes  
 Ahora que ha creado una personalización de nivel de documento básico para Word, en los siguientes temas obtendrá más información sobre cómo desarrollar personalizaciones:  
  
-   Tareas de programación generales que puede efectuar en personalizaciones de nivel de documento: [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md).  
  
-   Tareas de programación específicas de las personalizaciones de nivel de documento para Word: [Soluciones de Word](../vsto/word-solutions.md).  
  
-   Usar el modelo de objetos de Word: [Información general acerca del modelo de objetos de Word](../vsto/word-object-model-overview.md).  
  
-   Personalizar la interfaz de usuario de Word, por ejemplo, agregando una pestaña personalizada a la cinta de opciones o creando su propio panel de acciones: [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
-   Usar objetos de Word extendidos proporcionados por las soluciones de Office en Visual Studio para llevar a cabo tareas que no son posibles con el modelo de objetos de Word \(por ejemplo, hospedar controles administrados en documentos y enlazar controles de Word a datos mediante el modelo de enlace de datos de Windows Forms\): [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md).  
  
-   Compilar y depurar personalizaciones de nivel de documento para Word: [Compilar soluciones de Office](../vsto/building-office-solutions.md).  
  
-   Implementar personalizaciones de nivel de documento para Word: [Implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
## Vea también  
 [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Soluciones de Word](../vsto/word-solutions.md)   
 [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)   
 [Información general acerca del modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md)  
  
  