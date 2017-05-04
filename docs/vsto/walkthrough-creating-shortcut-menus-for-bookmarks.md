---
title: "Tutorial: Crear men&#250;s de acceso directo para marcadores | Microsoft Docs"
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
  - "Bookmark (control), eventos"
  - "menús contextuales, Word"
  - "menús, crear en aplicaciones de Office"
  - "menús contextuales, Word"
ms.assetid: 86dbf3ff-ba75-42f9-8df6-abfc19b3cf6b
caps.latest.revision: 57
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Tutorial: Crear men&#250;s de acceso directo para marcadores
  En este tutorial se muestra cómo crear menús contextuales para los controles <xref:Microsoft.Office.Tools.Word.Bookmark> de una personalización en el nivel del documento para Word.  Cuando un usuario hace clic con el botón secundario en el texto de un marcador, aparece un menú contextual que proporciona las opciones de usuario para dar formato al texto.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   [Crear el proyecto](#BKMK_CreateProject).  
  
-   [Agregar texto y marcadores al documento](#BKMK_addtextandbookmarks).  
  
-   [Comandos para agregar un menú contextual](#BKMK_AddCmndsShortMenu).  
  
-   [Dar formato al texto del marcador](#BKMK_formattextbkmk).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a> Crear el proyecto  
 El primer paso es crear un proyecto de documento de Word en Visual Studio.  
  
#### Para crear un nuevo proyecto  
  
-   Cree un proyecto de documento de Word con el nombre Mi menú contextual de marcador.  En el asistente, seleccione **Crear un nuevo documento**.  Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abrirá el nuevo documento de Word en el diseñador y agregará el proyecto **Mi menú contextual de marcador** al **Explorador de soluciones**.  
  
##  <a name="BKMK_addtextandbookmarks"></a> Agregar texto y marcadores al documento  
 Agregue texto al documento y, a continuación, agregue dos marcadores superpuestos.  
  
#### Para agregar texto al documento  
  
-   En el documento que aparece en el diseñador del proyecto, escriba el texto siguiente.  
  
     Éste es un ejemplo de cómo crear un menú contextual al hacer clic con el botón secundario del mouse en el texto de un marcador.  
  
#### Para agregar un control para marcador al documento  
  
1.  En el **Cuadro de herramientas**, en la pestaña **Controles de Word** , arrastre un control <xref:Microsoft.Office.Tools.Word.Bookmark> al documento.  
  
     Aparece el cuadro de diálogo **Agregar control de marcador**.  
  
2.  Seleccione las palabras “que creen un menú contextual al hacer clic con el texto”, y haga clic en **Aceptar**.  
  
     `bookmark1` se agregará al documento.  
  
3.  Agregue otro control <xref:Microsoft.Office.Tools.Word.Bookmark> a las palabras “clic con el botón secundario en el texto de un marcador”.  
  
     `bookmark2` se agregará al documento.  
  
    > [!NOTE]  
    >  Las palabras “clic con el botón secundario en el texto” están en `bookmark1` y `bookmark2`.  
  
 Al agregar un marcador a un documento en tiempo de diseño, se crea un control <xref:Microsoft.Office.Tools.Word.Bookmark>.  Puede programar en respuesta a varios eventos del marcador.  Se puede escribir código en el evento <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> del marcador para que aparezca un menú contextual cuando el usuario haga clic con el botón secundario en el texto del marcador.  
  
##  <a name="BKMK_AddCmndsShortMenu"></a> Comandos para agregar un menú contextual  
 Agregue botones al menú contextual que aparece al hacer clic con el botón secundario en el documento.  
  
#### Para agregar comandos a un menú contextual  
  
1.  Agregue un elemento **Cinta XML** al proyecto.  Para obtener más información, vea [Cómo: Iniciarse en la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  En **Explorador de soluciones**, seleccione **ThisDocument.cs** o **ThisDocument.vb**.  
  
3.  En la barra de menú, elija **Ver**, **Código**.  
  
     El archivo de clase **Este documento** abre en el Editor de código.  
  
4.  Agregue el código siguiente a la clase **Este documento** .  Este código invalida el método CreateRibbonExtensibilityObject y devuelve la clase XML de la cinta de opciones a la aplicación de Office.  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#1)]  
  
5.  En el **Explorador de soluciones**, seleccione el archivo XML de cinta.  De forma predeterminada, el archivo XML de cinta se denomina Ribbon1.xml.  
  
6.  En la barra de menú, elija **Ver**, **Código**.  
  
     El archivo de XML Ribbon abre en el Editor de código.  
  
7.  En el editor de código, reemplace el contenido del archivo XML de cinta con el código siguiente.  
  
    ```  
  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="BoldButton" label="Bold" onAction="ButtonClick"          
               getVisible="GetVisible" />  
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"   
              getVisible="GetVisible"/>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
     Este código agrega dos botones al menú contextual que aparece al hacer clic con el botón secundario en el documento.  
  
8.  En el **Explorador de soluciones**, haga clic con el botón secundario en `ThisDocument` y, después, haga clic en **Ver código**.  
  
9. Declare las siguientes variables y una variable de marcador en el nivel de clase.  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#2)]  
  
10. En **Explorador de soluciones**, seleccione el archivo de código de la cinta de opciones.  De forma predeterminada, el archivo de código de la cinta de opciones se denomina **Ribbon1.cs** o **Ribbon1.vb**.  
  
11. En la barra de menú, elija **Ver**, **Código**.  
  
     Se abre el archivo de código de la cinta de opciones en el editor de código.  
  
12. En el archivo de código de la cinta de opciones, agregue el siguiente método.  Éste es un método de devolución de llamada para los dos botones agregados al menú contextual del documento.  Este método determina si estos botones aparecen en el menú contextual.  Los botones negrita y cursiva aparecen sólo si hace clic con el texto del marcador.  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a> Dar formato al texto del marcador  
  
#### Para aplicar formato al texto del marcador  
  
1.  En el archivo de código de la cinta de opciones, agregue un controlador de eventos `ButtonClick` para aplicar formato al marcador.  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/ribbon1.vb#6)]  
  
2.  **Explorador de soluciones**, seleccione **ThisDocument.cs** o **ThisDocument.vb**.  
  
3.  En la barra de menú, elija **Ver**, **Código**.  
  
     El archivo de clase **Este documento** abre en el Editor de código.  
  
4.  Agregue el código siguiente a la clase **Este documento** .  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  Deberá escribir código para controlar las situaciones en que se superpongan los marcadores.  De lo contrario, se llamará de forma predeterminada al código de todos los marcadores de la selección.  
  
5.  En C\#, debe agregar controladores de eventos para los controles de marcadores al evento <xref:Microsoft.Office.Tools.Word.Document.Startup>.  Para obtener más información sobre cómo crear controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#4)]  
  
## Probar la aplicación  
 Pruebe el documento para comprobar que los elementos de menú en negrita y cursiva aparecen en el menú contextual al hacer clic con el texto de un marcador y que el texto tiene el formato correcto.  
  
#### Para probar el documento  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Haga clic con el botón secundario en el primer marcador y, a continuación, haga clic en **Negrita**.  
  
3.  Compruebe que todo el texto de `bookmark1` aparece en negrita.  
  
4.  Haga clic con el botón secundario en el texto donde los marcadores se superponen, y, a continuación, haga clic en **Cursiva**.  
  
5.  Compruebe que todo el texto de `bookmark2` está en cursiva y que únicamente la parte de texto de `bookmark1` que se superpone a `bookmark2` está en cursiva.  
  
## Pasos siguientes  
 Éstas son algunas de las tareas que pueden venir a continuación:  
  
-   Escribir código de respuesta a los eventos de controles host en Excel.  Para obtener más información, vea [Tutorial: Programar basándose en los eventos de un control NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
-   Utilizar una casilla para cambiar el formato de un marcador.  Para obtener más información, vea [Tutorial: Cambiar el formato de un documento utilizando controles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## Vea también  
 [Tutoriales para Word](../vsto/walkthroughs-using-word.md)   
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Bookmark &#40;Control&#41;](../vsto/bookmark-control.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  