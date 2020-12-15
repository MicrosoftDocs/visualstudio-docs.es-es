---
title: 'Tutorial: crear menús contextuales para marcadores'
description: Obtenga información sobre cómo crear menús contextuales para los controles Bookmark en una personalización de nivel de documento para Microsoft Word.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8b018687ec10eb725ece7d776277ea1c699dbbec
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524213"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>Tutorial: crear menús contextuales para marcadores
  En este tutorial se muestra cómo crear menús contextuales para <xref:Microsoft.Office.Tools.Word.Bookmark> los controles de una personalización de nivel de documento para Word. Cuando un usuario hace clic con el botón secundario en el texto de un marcador, aparece un menú contextual que proporciona las opciones de usuario para dar formato al texto.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- [Cree el proyecto](#BKMK_CreateProject).

- [Agregue texto y marcadores al documento](#BKMK_addtextandbookmarks).

- [Agregar comandos a un menú contextual](#BKMK_AddCmndsShortMenu).

- [Dé formato al texto del marcador](#BKMK_formattextbkmk).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

## <a name="create-the-project"></a><a name="BKMK_CreateProject"></a> Crear el proyecto
 El primer paso es crear un proyecto de documento de Word en Visual Studio.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

- Cree un proyecto de documento de Word que tenga el nombre del **menú contextual mi marcador**. En el asistente, seleccione **crear un nuevo documento**. Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo documento de Word en el diseñador y agrega el proyecto de **menú contextual mi marcador** a **Explorador de soluciones**.

## <a name="add-text-and-bookmarks-to-the-document"></a><a name="BKMK_addtextandbookmarks"></a> Agregar texto y marcadores al documento
 Agregue texto al documento y, a continuación, agregue dos marcadores superpuestos.

### <a name="to-add-text-to-your-document"></a>Para agregar texto al documento

- En el documento que aparece en el diseñador del proyecto, escriba el texto siguiente.

     **Este es un ejemplo de cómo crear un menú contextual al hacer clic con el botón secundario en el texto de un marcador.**

### <a name="to-add-a-bookmark-control-to-your-document"></a>Para agregar un control Bookmark a un documento

1. En el **cuadro de herramientas**, en la pestaña **controles de Word** , arrastre un <xref:Microsoft.Office.Tools.Word.Bookmark> control hasta el documento.

    Aparece el cuadro de diálogo **Agregar control de marcador** .

2. Seleccione las palabras "crear un menú contextual al hacer clic con el botón secundario en el texto" y, a continuación, haga clic en **Aceptar**.

    `bookmark1` se agrega al documento.

3. Agregue otro <xref:Microsoft.Office.Tools.Word.Bookmark> control a las palabras "haga clic con el botón derecho en el texto de un marcador".

    `bookmark2` se agrega al documento.

   > [!NOTE]
   > Las palabras "hacer clic con el botón secundario en el texto" están en `bookmark1` y `bookmark2` .

   Al agregar un marcador a un documento en tiempo de diseño, <xref:Microsoft.Office.Tools.Word.Bookmark> se crea un control. Puede programar con varios eventos del marcador. Puede escribir código en el <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> evento del marcador para que, cuando el usuario haga clic con el botón secundario en el texto del marcador, aparezca un menú contextual.

## <a name="add-commands-to-a-shortcut-menu"></a><a name="BKMK_AddCmndsShortMenu"></a> Agregar comandos a un menú contextual
 Agregue botones al menú contextual que aparece cuando hace clic con el botón secundario en el documento.

### <a name="to-add-commands-to-a-shortcut-menu"></a>Para agregar comandos a un menú contextual

1. Agregue un elemento XML de la **cinta** de opciones al proyecto. Para obtener más información, vea [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. En **Explorador de soluciones**, seleccione **ThisDocument.CS** o **ThisDocument. VB**.

3. En la barra de menús, elija **Ver** > **Código**.

     El archivo de clase **ThisDocument** se abre en el editor de código.

4. Agregue el código siguiente a la clase **ThisDocument** . Este código invalida el método CreateRibbonExtensibilityObject y devuelve la clase XML Ribbon a la aplicación de Office.

     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]

5. En el **Explorador de soluciones**, seleccione el archivo XML de cinta. De forma predeterminada, el archivo XML de cinta se denomina Ribbon1.xml.

6. En la barra de menús, elija **Ver** > **Código**.

     Se abrirá el archivo de código XML de cinta de opciones en el Editor de código.

7. En el editor de código, reemplace el contenido del archivo XML de la cinta de opciones por el código siguiente.

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

     Este código agrega dos botones al menú contextual que aparece al hacer clic con el botón secundario en el documento.

8. En **Explorador de soluciones**, haga clic con el botón secundario `ThisDocument` y, a continuación, haga clic en **Ver código**.

9. Declare las siguientes variables y una variable de marcador en el nivel de clase.

     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]

10. En **Explorador de soluciones**, seleccione el archivo de código de la cinta de opciones. De forma predeterminada, el archivo de código de la cinta de opciones se denomina **Ribbon1.CS** o **Ribbon1. VB**.

11. En la barra de menús, elija **Ver** > **Código**.

     Se abre el archivo de código de la cinta de opciones en el editor de código.

12. En el archivo de código de la cinta de opciones, agregue el siguiente método. Se trata de un método de devolución de llamada para los dos botones que ha agregado al menú contextual del documento. Este método determina si estos botones aparecen en el menú contextual. Los botones de negrita y cursiva solo aparecen si hace clic con el botón secundario en texto dentro del marcador.

     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]

## <a name="format-the-text-in-the-bookmark"></a><a name="BKMK_formattextbkmk"></a> Dar formato al texto del marcador

### <a name="to-format-the-text-in-the-bookmark"></a>Para dar formato al texto del marcador

1. En el archivo de código de la cinta de opciones, agregue un `ButtonClick` controlador de eventos para aplicar formato al marcador.

     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]

2. **Explorador de soluciones**, seleccione **ThisDocument.CS** o **ThisDocument. VB**.

3. En la barra de menús, elija **Ver** > **Código**.

     El archivo de clase **ThisDocument** se abre en el editor de código.

4. Agregue el código siguiente a la clase **ThisDocument** .

     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]

    > [!NOTE]
    > Debe escribir código para controlar el caso en el que los marcadores se superponen. Si no lo hace, de forma predeterminada, se llamará al código para todos los marcadores de la selección.

5. En C#, debe agregar controladores de eventos para los controles Bookmark al <xref:Microsoft.Office.Tools.Word.Document.Startup> evento. Para obtener información sobre cómo crear controladores de eventos, consulte [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]

## <a name="test-the-application"></a>Prueba de la aplicación
 Pruebe el documento para comprobar que los elementos de menú en negrita y cursiva aparecen en el menú contextual al hacer clic con el botón secundario en el texto de un marcador y que el texto tiene el formato correcto.

### <a name="to-test-your-document"></a>Para probar el documento

1. Presione **F5** para ejecutar el proyecto.

2. Haga clic con el botón secundario en el primer marcador y, a continuación, haga clic en **negrita**.

3. Compruebe que todo el texto de `bookmark1` tiene el formato de negrita.

4. Haga clic con el botón secundario en el texto donde se superponen los marcadores y, a continuación, haga clic en **cursiva**.

5. Compruebe que todo el texto de `bookmark2` está en cursiva y solo la parte del texto de `bookmark1` que se superpone está en `bookmark2` cursiva.

## <a name="next-steps"></a>Pasos siguientes
 A continuación, podría realizar las siguientes tareas:

- Escribir código para responder a los eventos de los controles host en Excel. Para obtener más información, vea [Tutorial: programar contra eventos de un control NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

- Use una casilla para cambiar el formato de un marcador. Para obtener más información, vea [Tutorial: cambiar el formato de un documento mediante controles de casilla](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Consulte también
- [Tutoriales de uso de Word](../vsto/walkthroughs-using-word.md)
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Bookmark (control)](../vsto/bookmark-control.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
