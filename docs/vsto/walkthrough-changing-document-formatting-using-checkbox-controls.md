---
title: "Tutorial: Cambiar el formato de un documento utilizando controles CheckBox | Microsoft Docs"
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
  - "casillas, documentos de Word"
  - "controles [desarrollo de Office en Visual Studio], agregar a documentos"
  - "documentos [desarrollo de Office en Visual Studio], controles de casilla"
  - "documentos [desarrollo de Office en Visual Studio], aplicar formato"
  - "documentos de Word, cambiar el formato utilizando controles"
ms.assetid: 3740e41d-a57e-43bb-87e7-6e5481ef290b
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Tutorial: Cambiar el formato de un documento utilizando controles CheckBox
  En este tutorial se muestra cómo utilizar controles de formularios Windows Forms en una personalización en el nivel del documento para que Microsoft Office Word cambie el formato de texto.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Agregar texto y un control al documento de un proyecto en el nivel del documento en tiempo de diseño.  
  
-   Aplicar formato al texto al seleccionar una opción.  
  
 Para consultar el resultado como ejemplo completo, vea el Ejemplo Word Controls en [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Crear el proyecto  
 El primer paso es crear el proyecto de documento de Word.  
  
#### Para crear un nuevo proyecto  
  
1.  Cree un proyecto de documento de Word con el nombre Mi formato de Word.  En el asistente, seleccione **Crear un nuevo documento**.  
  
     Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo documento de Word en el diseñador y agrega el proyecto **Mi formato de Word** al **Explorador de soluciones**.  
  
## Agregar texto y controles al documento de Word  
 Para este tutorial, agregue tres casillas y algo de texto en un control <xref:Microsoft.Office.Tools.Word.Bookmark> al documento de Word.  Las casillas presentarán al usuario las opciones para dar formato al texto.  
  
#### Para agregar tres casillas  
  
1.  Compruebe que el documento está abierto en el diseñador de Visual Studio.  
  
2.  En la ficha **Controles comunes** del **Cuadro de herramientas**, arrastre el primer control <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> hasta el documento.  
  
3.  En la ventana **Propiedades**, cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**applyBoldFont**|  
    |**Texto**|Negrita|  
  
4.  Presione **Entrar** para colocar el punto de inserción debajo de la primera casilla.  
  
5.  Agregue una segunda casilla al documento debajo de la casilla `ApplyBoldFont` y cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**applyItalicFont**|  
    |**Texto**|Cursiva|  
  
6.  Presione **Entrar** para colocar el punto de inserción debajo de la segunda casilla.  
  
7.  Agregue una tercera casilla al documento debajo de la casilla `ApplyItalicFont` y cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**applyUnderlineFont**|  
    |**Texto**|Subrayado|  
  
#### Para agregar texto y un control Bookmark  
  
1.  Coloque el punto de inserción debajo de los controles de casilla y escriba el siguiente texto:  
  
     Haga clic en una casilla para cambiar el formato de este texto.  
  
2.  Desde la ficha **Controles de Word** del **Cuadro de herramientas**, arrastre un control <xref:Microsoft.Office.Tools.Word.Bookmark> hasta el documento.  
  
     Aparece el cuadro de diálogo **Agregar control de marcador**.  
  
3.  Seleccione el texto que agregó al documento y haga clic en **Aceptar**.  
  
     Se agrega al texto seleccionado en el documento un control <xref:Microsoft.Office.Tools.Word.Bookmark> llamado **Bookmark1**.  
  
4.  En la ventana **Propiedades**, cambie el valor de la propiedad **\(Name\)** a **fontText.**  
  
 A continuación, escriba el código para dar formato al texto cuando se active o desactive una de las casillas.  
  
## Dar formato al texto cuando se activa o desactiva una casilla  
 Cuando el usuario selecciona una opción de formato, se ha de cambiar el formato del texto en el documento.  
  
#### Para cambiar el formato cuando se activa una casilla  
  
1.  Haga clic con el botón secundario del mouse en `ThisDocument` en el **Explorador de soluciones** y, a continuación, haga clic en la opción **Ver código** del menú contextual.  
  
2.  Para C\# únicamente, agregue las siguientes constantes a la clase **ThisDocument**.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#2)]  
  
3.  Agregue el código siguiente al controlador de eventos <xref:System.Windows.Forms.Control.Click> de la casilla `applyBoldFont`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#3)]  
  
4.  Agregue el código siguiente al controlador de eventos <xref:System.Windows.Forms.Control.Click> de la casilla `applyItalicFont`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#4)]  
  
5.  Agregue el código siguiente al controlador de eventos <xref:System.Windows.Forms.Control.Click> de la casilla `applyUnderlineFont`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#5)]  
  
6.  En C\#, debe agregar controladores de eventos para los cuadros de texto al evento <xref:Microsoft.Office.Tools.Word.Document.Startup>.  Para obtener información acerca de cómo crear controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#6)]  
  
## Probar la aplicación  
 Ahora puede probar el documento para comprobar que se aplica el formato correcto al texto cuando se activa o desactiva cada casilla.  
  
#### Para probar el documento  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Active o desactive una casilla.  
  
3.  Confirme que el texto tiene el formato correcto.  
  
## Pasos siguientes  
 En este tutorial se muestran los aspectos básicos del uso de las casillas y del cambio del formato de texto de los documentos de Word mediante programación.  Éstas son algunas de las tareas que pueden venir a continuación:  
  
-   Usar un botón para rellenar un cuadro de texto.  Para obtener más información, vea [Tutorial: Mostrar texto en un cuadro de texto en un documento utilizando un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Utilizar los botones de radio para seleccionar estilos de gráfico.  Para obtener más información, vea [Tutorial: Actualizar un gráfico en un documento utilizando botones de radio](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## Vea también  
 [Tutoriales para Word](../vsto/walkthroughs-using-word.md)   
 [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md)   
 [Limitaciones de los controles de formularios Windows Forms en los documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  