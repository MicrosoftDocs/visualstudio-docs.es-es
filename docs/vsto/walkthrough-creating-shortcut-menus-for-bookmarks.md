---
title: 'Tutorial: Crear menús contextuales para marcadores'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fb09bc2ee3f9278026be2046ff249fb2ca4c558f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863999"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>Tutorial: Crear menús contextuales para marcadores
  En este tutorial se muestra cómo crear menús contextuales para <xref:Microsoft.Office.Tools.Word.Bookmark> controles en una personalización de nivel de documento para Word. Cuando un usuario seleccione el texto de un marcador, un menú contextual aparece y proporciona las opciones de usuario para dar formato al texto.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
- [Crear el proyecto](#BKMK_CreateProject).  
  
- [Agregar texto y marcadores al documento](#BKMK_addtextandbookmarks).  
  
- [Agregar comandos a un menú contextual](#BKMK_AddCmndsShortMenu).  
  
- [Dar formato al texto del marcador](#BKMK_formattextbkmk).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a> Crear el proyecto  
 El primer paso es crear un proyecto de documento de Word en Visual Studio.  
  
### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
-   Crear un proyecto de documento de Word con el nombre **mi menú contextual de marcador**. En el asistente, seleccione **crear un nuevo documento**. Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo documento de Word en el diseñador y agrega el **mi menú contextual de marcador** proyecto a **el Explorador de soluciones**.  
  
##  <a name="BKMK_addtextandbookmarks"></a> Agregar texto y marcadores al documento  
 Agregue texto al documento y, a continuación, agregue dos marcadores superpuestos.  
  
### <a name="to-add-text-to-your-document"></a>Para agregar texto al documento  
  
-   En el documento que aparece en el diseñador del proyecto, escriba el texto siguiente.  
  
     **Esto es un ejemplo de creación de un menú contextual cuando hace clic en el texto de un marcador.**  
  
### <a name="to-add-a-bookmark-control-to-your-document"></a>Para agregar un control Bookmark al documento  
  
1. En el **cuadro de herramientas**, desde el **controles de Word** pestaña, arrastre un <xref:Microsoft.Office.Tools.Word.Bookmark> control al documento.  
  
    El **agregar Control de marcador** aparece el cuadro de diálogo.  
  
2. Seleccione las palabras "creación de un menú contextual cuando hace clic en el texto" y, a continuación, haga clic en **Aceptar**.  
  
    `bookmark1` se agrega al documento.  
  
3. Agregue otro <xref:Microsoft.Office.Tools.Word.Bookmark> el control a las palabras "haga clic en el texto de un marcador".  
  
    `bookmark2` se agrega al documento.  
  
   > [!NOTE]  
   >  Las palabras "haga clic en el texto" están en ambos `bookmark1` y `bookmark2`.  
  
   Cuando se agrega un marcador a un documento en tiempo de diseño, un <xref:Microsoft.Office.Tools.Word.Bookmark> se crea el control. Puede programar varios eventos del marcador. Puede escribir código en el <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> eventos del marcador para que cuando el usuario seleccione el texto del marcador, aparece un menú contextual.  
  
##  <a name="BKMK_AddCmndsShortMenu"></a> Agregar comandos a un menú contextual  
 Agregar botones al menú contextual que aparece cuando hace clic en el documento.  
  
### <a name="to-add-commands-to-a-shortcut-menu"></a>Para agregar comandos a un menú contextual  
  
1.  Agregar un **Ribbon XML** al proyecto. Para obtener más información, vea [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  En **el Explorador de soluciones**, seleccione **ThisDocument.cs** o **ThisDocument.vb**.  
  
3.  En la barra de menús, elija **Ver** > **Código**.  
  
     El **ThisDocument** en el Editor de código se abre el archivo de clase.  
  
4.  Agregue el código siguiente a la **ThisDocument** clase. Este código invalida el método CreateRibbonExtensibilityObject y devuelve la clase XML Ribbon a la aplicación de Office.  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]  
  
5.  En el **Explorador de soluciones**, seleccione el archivo XML de cinta. De forma predeterminada, el archivo XML de cinta se denomina Ribbon1.xml.  
  
6.  En la barra de menús, elija **Ver** > **Código**.  
  
     Se abrirá el archivo de código XML de cinta de opciones en el Editor de código.  
  
7.  En el Editor de código, reemplace el contenido del archivo XML de cinta de opciones con el código siguiente.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8"?>  
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
  
     Este código agrega dos botones en el menú contextual que aparece cuando hace clic en el documento.  
  
8.  En **el Explorador de soluciones**, haga clic en `ThisDocument`y, a continuación, haga clic en **ver código**.  
  
9. Declare una variable de marcador en el nivel de clase y de las siguientes variables.  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]  
  
10. En **el Explorador de soluciones**, seleccione el archivo de código de la cinta de opciones. De forma predeterminada, el archivo de código de cinta de opciones se denomina **Ribbon1.cs** o **Ribbon1.vb**.  
  
11. En la barra de menús, elija **Ver** > **Código**.  
  
     Se abre el archivo de código de la cinta de opciones en el editor de código.  
  
12. En el archivo de código de la cinta de opciones, agregue el siguiente método. Se trata de un método de devolución de llamada para los dos botones que agregó al menú contextual del documento. Este método determina si estos botones aparecen en el menú contextual. Los botones de negrita y cursiva solo aparecen si hace doble clic en el texto del marcador.  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a> Dar formato al texto del marcador  
  
### <a name="to-format-the-text-in-the-bookmark"></a>Para dar formato al texto del marcador  
  
1.  En el archivo de código de la cinta de opciones, agregue un `ButtonClick` controlador de eventos para aplicar formato al marcador.  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]  
  
2.  **El Explorador de soluciones**, seleccione **ThisDocument.cs** o **ThisDocument.vb**.  
  
3.  En la barra de menús, elija **Ver** > **Código**.  
  
     El **ThisDocument** en el Editor de código se abre el archivo de clase.  
  
4.  Agregue el código siguiente a la **ThisDocument** clase.  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  Debe escribir código para controlar el caso de que se superponen a marcadores. Si no lo hace, de forma predeterminada, el código se llamará para todos los marcadores de la selección.  
  
5.  En C#, debe agregar controladores de eventos para los controles de marcador para el <xref:Microsoft.Office.Tools.Word.Document.Startup> eventos. Para obtener información acerca de cómo crear controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]  
  
## <a name="test-the-application"></a>Probar la aplicación  
 Probar el documento para comprobar que los elementos de menú en negrita y cursiva aparecen en el menú contextual cuando hace clic en el texto de un marcador y que el texto es el formato correcto.  
  
### <a name="to-test-your-document"></a>Para probar el documento  
  
1.  Presione **F5** para ejecutar el proyecto.  
  
2.  Haga clic en el primer marcador y, a continuación, haga clic en **negrita**.  
  
3.  Compruebe que todo el texto en `bookmark1` está en negrita.  
  
4.  Haga clic en el texto que se superponen a los marcadores, y, a continuación, haga clic en **cursiva**.  
  
5.  Compruebe que todo el texto en `bookmark2` es cursiva y solo la parte del texto en `bookmark1` que se superpone `bookmark2` está en cursiva.  
  
## <a name="next-steps"></a>Pasos siguientes  
 A continuación, podría realizar las siguientes tareas:  
  
-   Escribir código para responder a eventos de los controles host en Excel. Para obtener más información, vea [Tutorial: Programar basándose en eventos de un control NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
-   Utilice una casilla de verificación para cambiar el formato de un marcador. Para obtener más información, vea [Tutorial: Cambiar formato de documento utilizando controles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales para Word](../vsto/walkthroughs-using-word.md)   
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Bookmark (control)](../vsto/bookmark-control.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
