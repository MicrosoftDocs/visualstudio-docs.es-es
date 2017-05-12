---
title: "Tutorial: Crear la primera personalizaci&#243;n en el nivel del documento para Excel"
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
  - "Excel [desarrollo de Office en Visual Studio], crear el primer proyecto"
  - "desarrollo de Office en Visual Studio, crear el primer proyecto"
ms.assetid: 785d3b86-5ed5-4e0d-b5ee-896b6b1330ac
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Tutorial: Crear la primera personalizaci&#243;n en el nivel del documento para Excel
  Este tutorial introductorio muestra cómo crear una personalización de nivel de documento para Microsoft Office Excel.  Las características que se crean en este tipo de solución solo están disponibles cuando se abre un libro concreto.  No se puede usar una personalización de nivel de documento para realizar cambios en toda la aplicación, por ejemplo para mostrar una nueva pestaña de la cinta de opciones cuando se abre un libro.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un proyecto de libro de Excel.  
  
-   Agregar texto a una hoja de cálculo que se hospeda en el diseñador de Visual Studio.  
  
-   Escribir código que usa el modelo de objetos de Excel para agregar texto a la hoja de cálculo personalizada cuando se abre.  
  
-   Compilar y ejecutar el proyecto para probarlo.  
  
-   Limpiar el proyecto completado para quitar los archivos de compilación innecesarios y la configuración de seguridad del equipo de desarrollo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Crear el proyecto  
  
#### Para crear un nuevo proyecto de libro de Excel en Visual Studio  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En el menú **Archivo**, elija **Nuevo** y haga clic en **Proyecto**.  
  
3.  En el panel de plantillas, expanda **Visual C\#** o  **Visual Basic** y luego expanda **Office\/SharePoint**.  
  
4.  En el nodo **Office\/SharePoint** expandido, seleccione el nodo **Complementos de Office**.  
  
5.  En la lista de plantillas de proyecto, elija un proyecto de complemento de VSTO de Excel.  
  
6.  En el cuadro **Nombre**, escriba **FirstWorkbookCustomization**.  
  
7.  Haga clic en **Aceptar**.  
  
     Se abre el **Asistente para proyectos de Visual Studio Tools para Office**.  
  
8.  Seleccione **Crear un nuevo documento** y haga clic en **Aceptar**.  
  
    -   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el proyecto **FirstWorkbookCustomization** y agrega los siguientes archivos al proyecto.  
  
    -   *FirstWorkbookCustomization*.xlsx: representa el libro de Excel en el proyecto.  Contiene todas las hojas de cálculo y los gráficos.  
  
    -   Sheet1 \(archivo .vb para Visual Basic o archivo .cs para Visual C\#\): hoja de cálculo que proporciona la superficie de diseño y el código de la primera hoja de cálculo del libro.  Para obtener más información, consulte [Elemento host Worksheet](../vsto/worksheet-host-item.md).  
  
    -   Sheet2 \(archivo .vb para Visual Basic o archivo .cs para Visual C\#\): hoja de cálculo que proporciona la superficie de diseño y el código de la segunda hoja de cálculo del libro.  
  
    -   Sheet3 \(archivo .vb para Visual Basic o archivo .cs para Visual C\#\): hoja de cálculo que proporciona la superficie de diseño y el código de la tercera hoja de cálculo del libro.  
  
    -   ThisWorkbook \(archivo .vb para Visual Basic o archivo .cs para Visual C\#\): contiene la superficie de diseño y el código para las personalizaciones de nivel de libro.  Para obtener más información, consulte [Elemento host Workbook](../vsto/workbook-host-item.md).  
  
     El archivo de código Sheet1 se abre automáticamente en el diseñador.  
  
## Cerrar y volver a abrir hojas de cálculo en el diseñador  
 Puede volver a abrir el libro o la hoja de cálculo si los cierra deliberada o accidentalmente en el diseñador mientras está desarrollando el proyecto.  
  
#### Para cerrar y volver a abrir una hoja de cálculo en el diseñador  
  
1.  Cierre el libro haciendo clic en el botón **Cerrar** \(X\) de la ventana del diseñador.  
  
2.  En el **Explorador de soluciones**, haga clic con el botón derecho en el archivo de código **Sheet1** y haga clic en **Diseñador de vistas**.  
  
     o bien  
  
     En el **Explorador de soluciones**, haga doble clic en el archivo de código **Sheet1**.  
  
## Agregar texto a la hoja de cálculo en el diseñador  
 Puede diseñar la interfaz de usuario de la personalización modificando la hoja de cálculo que está abierta en el diseñador.  Por ejemplo, puede agregar texto a las celdas, aplicar fórmulas o agregar controles de Excel.  Para obtener más información sobre cómo usar el diseñador, consulte [Proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
#### Para agregar texto a la hoja de cálculo mediante el diseñador  
  
1.  En la hoja de cálculo que está abierta en el diseñador, seleccione la celda **A1** y escriba el texto siguiente.  
  
     **Este texto se agregó mediante el diseñador.**  
  
> [!WARNING]  
>  Si agrega esta línea de texto a la celda **A2**, la sobrescribirá otro código de este ejemplo.  
  
## Agregar texto a una hoja de cálculo mediante programación  
 A continuación, agregue código al archivo de código Sheet1.  El nuevo código usa el modelo de objetos de Excel para agregar una segunda línea de texto al libro.  De forma predeterminada, el archivo de código Sheet1 contiene el siguiente código generado:  
  
-   Una definición parcial de la clase `Sheet1`, que representa el modelo de programación de la hoja de cálculo y proporciona acceso al modelo de objetos de Excel.  Para obtener más información, consulte [Elemento host Worksheet](../vsto/worksheet-host-item.md) e [Información general acerca del modelo de objetos de Word](../vsto/word-object-model-overview.md).  El resto de la clase `Sheet1` se define en un archivo de código oculto que no se debe modificar.  
  
-   Los controladores de eventos `Sheet1_Startup` y `Sheet1_Shutdown`.  Se llama a estos controladores de eventos cuando Excel carga y descarga la personalización.  Use estos controladores de eventos para inicializar la personalización cuando se cargue y para limpiar los recursos que usa la personalización cuando se descargue.  Para obtener más información, consulte [Eventos de los proyectos de Office](../vsto/events-in-office-projects.md).  
  
#### Para agregar una segunda línea de texto a la hoja de cálculo mediante código  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en **Sheet1** y, a continuación, haga clic en **Ver código**.  
  
     El archivo de código se abre en Visual Studio.  
  
2.  Reemplace el controlador de eventos `Sheet1_Startup` por el siguiente código:  Cuando se abre Sheet1, este código agrega una segunda línea de texto a la hoja de cálculo.  
  
     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelWorkbookTutorial/CS/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelWorkbookTutorial/VB/Sheet1.vb#1)]  
  
## Probar el proyecto  
  
#### Para probar el libro  
  
1.  Presione **F5** para compilar y ejecutar el proyecto.  
  
     Al compilar el proyecto, el código se compila en un ensamblado que está asociado al libro.  Visual Studio coloca una copia del libro y el ensamblado en la carpeta de resultados de compilación del proyecto y establece la configuración de seguridad en el equipo de desarrollo para permitir que se ejecute la personalización.  Para obtener más información, consulte [Compilar soluciones de Office](../vsto/building-office-solutions.md).  
  
2.  En el libro, compruebe que ve el texto siguiente.  
  
     **Este texto se agregó mediante el diseñador.**  
  
     **Este texto se agregó mediante código.**  
  
3.  Cierre el libro.  
  
## Limpiar el proyecto  
 Cuando termine de desarrollar un proyecto, debe quitar los archivos de la carpeta de resultados de compilación y la configuración de seguridad creada por el proceso de compilación.  
  
#### Para limpiar el proyecto completado en el equipo de desarrollo  
  
1.  En el menú **Compilar** de Visual Studio, haga clic en **Limpiar solución**.  
  
## Pasos siguientes  
 Ahora que ha creado una personalización de nivel de documento básico para Excel, en los siguientes temas obtendrá más información sobre cómo desarrollar personalizaciones:  
  
-   Tareas de programación generales que puede efectuar en personalizaciones de nivel de documento: [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md).  
  
-   Tareas de programación específicas de las personalizaciones de nivel de documento para Excel: [Soluciones de Excel](../vsto/excel-solutions.md).  
  
-   Usar el modelo de objetos de Excel: [Información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md).  
  
-   Personalizar la interfaz de usuario de Excel, por ejemplo, agregando una pestaña personalizada a la cinta de opciones o creando su propio panel de acciones: [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
-   Usar objetos de Excel extendidos proporcionados por las herramientas de desarrollo de Office en Visual Studio para llevar a cabo tareas que no son posibles con el modelo de objetos de Excel \(por ejemplo, hospedar controles administrados en documentos y enlazar controles de Excel a datos mediante el modelo de enlace de datos de Windows Forms\): [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md).  
  
-   Compilar y depurar personalizaciones de nivel de documento para Excel: [Compilar soluciones de Office](../vsto/building-office-solutions.md).  
  
-   Implementar personalizaciones de nivel de documento para Excel: [Implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
## Vea también  
 [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Soluciones de Excel](../vsto/excel-solutions.md)   
 [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)   
 [Información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md)  
  
  