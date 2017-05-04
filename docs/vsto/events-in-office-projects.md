---
title: "Eventos de los proyectos de Office | Microsoft Docs"
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
  - "Sheet1_Startup"
  - "ThisDocument_Shutdown"
  - "ThisDocument_Startup"
  - "complementos de nivel de aplicación [desarrollo de Office en Visual Studio], eventos"
  - "controladores de eventos [desarrollo de Office en Visual Studio]"
  - "ThisWorkbook_Startup"
  - "Sheet2_Startup"
  - "ThisWorkbook_Shutdown"
  - "personalizaciones de nivel de documento [desarrollo de Office en Visual Studio], eventos"
  - "Sheet2_Shutdown"
  - "Startup (evento)"
  - "Sheet3_Shutdown"
  - "complementos [desarrollo de Office en Visual Studio], eventos"
  - "Shutdown (evento)"
  - "ThisAddIn_Startup"
  - "Sheet3_Startup"
  - "Startup (método) [desarrollo de Office en Visual Studio]"
  - "Shutdown (método) [desarrollo de Office en Visual Studio]"
  - "Sheet1_Shutdown"
  - "eventos [desarrollo de Office en Visual Studio]"
  - "ThisAddIn_Shutdown"
ms.assetid: 666d7f23-ef85-4f2e-9cd3-258df5bdc6fd
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Eventos de los proyectos de Office
  Cada plantilla de proyecto de Office genera automáticamente varios controladores de eventos. Los controladores de eventos de las personalizaciones de nivel de documento son ligeramente diferentes de los controladores de eventos de los complementos de VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Proyectos de nivel del documento  
 Visual Studio proporciona código generado subyacente en documentos nuevos o existentes o en hojas de cálculo para las personalizaciones de nivel de documento. Este código genera dos eventos diferentes: **Startup** y **Shutdown**.  
  
### Evento Startup  
 El evento **Startup** se desencadena para cada uno de los elementos host \(documento, libro u hoja de cálculo\) cuando el documento está en ejecución y ya se ha ejecutado todo el código de inicialización del ensamblado. Es lo último que se ejecuta en el constructor de la clase en la que se ejecuta el código. Para más información sobre los elementos host, vea [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md).  
  
 Cuando se crea un proyecto de nivel de documento, Visual Studio crea controladores de eventos para el evento **Startup** en los archivos de código generado:  
  
-   En los proyectos de Microsoft Office Word, el controlador de eventos se denomina `ThisDocument_Startup`.  
  
-   En los proyectos de Microsoft Office Excel, los controladores de eventos tienen los nombres siguientes:  
  
    -   `Sheet1_Startup`  
  
    -   `Sheet2_Startup`  
  
    -   `Sheet3_Startup`  
  
    -   `ThisWorkbook_Startup`  
  
### Evento Shutdown  
 El evento  **Shutdown**  se desencadena para cada uno de los elementos host \(documento u hoja de cálculo\) cuando el dominio de aplicación en el que se ha cargado el código está a punto de descargarse. Es lo último a lo que se llama en la clase cuando se descarga.  
  
 Cuando se crea un proyecto de nivel de documento, Visual Studio crea controladores de eventos para el evento  **Shutdown**  en los archivos de código generado:  
  
-   En los proyectos de Microsoft Office Word, el controlador de eventos se denomina `ThisDocument_Shutdown`.  
  
-   En los proyectos de Microsoft Office Excel, los controladores de eventos tienen los nombres siguientes:  
  
    -   `Sheet1_Shutdown`  
  
    -   `Sheet2_Shutdown`  
  
    -   `Sheet3_Shutdown`  
  
    -   `ThisWorkbook_Shutdown`  
  
> [!NOTE]  
>  No quite controles mediante programación durante el controlador de eventos **Shutdown** del documento. Los elementos de la interfaz de usuario del documento ya no están disponibles cuando se produce el evento **Shutdown**. Si desea quitar controles antes de que se cierre la aplicación, agregue el código a otro controlador de eventos, como **BeforeClose** o **BeforeSave**.  
  
### Declaraciones de método de controlador de eventos  
 Todas las declaraciones del método de controlador de eventos reciben los mismos argumentos que se les pasan: *sender* y *e*. En Excel, el argumento *sender* hace referencia a la hoja, como `Sheet1` o `Sheet2`; en Word, el argumento *sender* hace referencia al documento. El argumento *e* hace referencia a los argumentos estándar de un evento, que no se usan en este caso.  
  
 El ejemplo de código siguiente muestra los controladores de eventos predeterminados en los proyectos de nivel de documento para Word.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#121](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#121)]
 [!code-vb[Trin_VstcoreWordAutomation#121](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#121)]  
  
 El ejemplo de código siguiente muestra los controladores de eventos predeterminados en los proyectos de nivel de documento para Excel.  
  
> [!NOTE]  
>  En el ejemplo de código siguiente se muestran los controladores de eventos de la clase `Sheet1`. Los nombres de los controladores de eventos de otras clases del elemento host corresponden al nombre de la clase. Por ejemplo, en la clase `Sheet2`, el controlador de eventos **Startup** se denomina `Sheet2_Startup`. En la clase `ThisWorkbook`, el controlador de eventos **Startup** se denomina `ThisWorkbook_Startup`.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#83](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#83)]  
  
### Orden de eventos en proyectos de Excel de nivel de documento  
 Los controladores de eventos **Startup** en proyectos de Excel se llaman en este orden:  
  
1.  `ThisWorkbook_Startup`.  
  
2.  `Sheet1_Startup`.  
  
3.  `Sheet2_Startup`.  
  
4.  `Sheet3_Startup`.  
  
5.  Otras hojas en orden.  
  
 Los controladores de eventos  **Shutdown** en una solución de libro se llaman en este orden:  
  
1.  `ThisWorkbook_Shutdown`.  
  
2.  `Sheet1_Shutdown`.  
  
3.  `Sheet2_Shutdown`.  
  
4.  `Sheet3_Shutdown`.  
  
5.  Otras hojas en orden.  
  
 El orden se determina cuando se compila el proyecto. Si el usuario reorganiza las hojas en tiempo de ejecución, no cambia el orden en que los eventos se desencadenan la siguiente vez que se abre o cierra el libro.  
  
## Proyectos de complementos de VSTO  
 Visual Studio ofrece código generado en los complementos de VSTO. Este código genera dos eventos diferentes: <xref:Microsoft.Office.Tools.AddInBase.Startup> y <xref:Microsoft.Office.Tools.AddInBase.Shutdown>.  
  
### Evento Startup  
 El evento <xref:Microsoft.Office.Tools.AddIn.Startup> se desencadena cuando se ha cargado el complemento de VSTO y se ha ejecutado todo el código de inicialización del ensamblado. Este evento está controlado por el método `ThisAddIn_Startup` en el archivo de código generado.  
  
 El código del controlador de eventos `ThisAddIn_Startup` es el primer código de usuario que se ejecuta, a menos que el complemento de VSTO invalide el método <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>. En ese caso, se llama al controlador de eventos `ThisAddIn_Startup` después de <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>.  
  
 No agregue código en el controlador de eventos `ThisAdd-In_Startup` si el código requiere que un documento esté abierto. En su lugar, agregue ese código a un evento que sea generado por la aplicación de Office cuando un usuario cree o abra un documento. Para obtener más información, consulta [Obtener acceso a un documento cuando se inicia la aplicación de Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Para más información sobre la secuencia de inicio de los complementos de VSTO, consulte [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
### Evento Shutdown  
 El evento <xref:Microsoft.Office.Tools.AddInBase.Shutdown> se desencadena cuando el dominio de aplicación en el que se ha cargado el código está a punto de descargarse. Este evento está controlado por el método `ThisAddIn_Shutdown` en el archivo de código generado. Este controlador de eventos es el último código de usuario que se ejecuta cuando se descarga el complemento de VSTO.  
  
#### El evento Shutdown en los complementos de VSTO de Outlook  
 El evento <xref:Microsoft.Office.Tools.AddInBase.Shutdown> solo se desencadena cuando el usuario deshabilita el complemento de VSTO mediante el cuadro de diálogo Complementos COM de Outlook. No se desencadena cuando se cierra Outlook. Si tiene código que se debe ejecutar cuando Outlook se cierra, controle uno de los siguientes eventos:  
  
-   El evento <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> del objeto <xref:Microsoft.Office.Interop.Outlook.Application>.  
  
-   El evento <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> del objeto <xref:Microsoft.Office.Interop.Outlook.Explorer>.  
  
> [!NOTE]  
>  Puede modificar el Registro para forzar a Outlook a desencadenar el evento <xref:Microsoft.Office.Tools.AddInBase.Shutdown> cuando salga. Sin embargo, si un administrador cambia esta configuración, cualquier código que agregue al método `ThisAddIn_Shutdown` dejará de ejecutarse al salir de Outlook. Para más información, vea [Cambios en Shutdown para Outlook 2010](http://go.microsoft.com/fwlink/?LinkID=184614).  
  
## Vea también  
 [Desarrollar soluciones de Office](../vsto/developing-office-solutions.md)   
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)   
 [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)   
 [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md)  
  
  