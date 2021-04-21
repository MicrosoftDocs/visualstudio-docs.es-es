---
title: 'Cómo: Administrar el diseño del control en los paneles de acciones'
description: Aprenda a administrar el diseño del control en los paneles de acciones escribiendo código para apilar correctamente los controles de usuario.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 182dee248f161f3dde721c50ee996d6f621dd9af
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827455"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Cómo: Administrar el diseño del control en los paneles de acciones
  Un panel de acciones está acoplado a la derecha de un documento o una hoja de cálculo de forma predeterminada; sin embargo, se puede acoplar a la izquierda, la parte superior o la parte inferior. Si usa varios controles de usuario, puede escribir código para apilar correctamente los controles de usuario en el panel de acciones. Para obtener más información, vea Información [general del panel Acciones.](../vsto/actions-pane-overview.md)

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 El orden de pila de los controles depende de si el panel de acciones está acoplado vertical u horizontalmente.

> [!NOTE]
> Si el usuario cambia el tamaño del panel de acciones en tiempo de ejecución, puede establecer los controles para que cambien de tamaño con el panel de acciones. Puede utilizar la propiedad <xref:System.Windows.Forms.Control.Anchor%2A> de un control de Windows Forms para anclar los controles al panel de acciones. Para obtener más información, [vea Cómo: Delimitar controles en Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Para establecer el orden de pila de los controles del panel de acciones

1. Abra un proyecto de nivel de documento para Microsoft Office Word que incluya un panel de acciones con varios controles de usuario o controles de panel de acciones anidados. Para obtener más información, vea Cómo: Agregar un panel de acciones a documentos [de Word o libros de Excel.](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)

2. Haga clic con el **botón derecho en ThisDocument.cs** **o ThisDocument.vb** **en Explorador de soluciones,** a continuación, haga clic **en Ver código**.

3. En el <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> controlador de eventos del panel de acciones, compruebe si la orientación del panel de acciones es horizontal.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet30":::

4. Si la orientación es horizontal, apile los controles del panel de acciones de la izquierda; De lo contrario, apile desde la parte superior.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet31":::

5. En C#, debe agregar un controlador de eventos para al `ActionsPane` controlador <xref:Microsoft.Office.Tools.Word.Document.Startup> de eventos. Para obtener información sobre cómo crear controladores de eventos, [vea Cómo: Crear controladores de eventos en proyectos de Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet32":::

6. Ejecute el proyecto y compruebe que los controles del panel de acciones se apilan de izquierda a derecha cuando el panel de acciones está acoplado en la parte superior del documento y que los controles se apilan de arriba abajo cuando el panel de acciones está acoplado en el lado derecho del documento.

## <a name="example"></a>Ejemplo
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet29":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet29":::

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo se necesita:

- Un proyecto de nivel de documento de Word con un panel de acciones que contiene varios controles de usuario o controles de panel de acciones anidadas.

## <a name="see-also"></a>Consulte también
- [Información general del panel Acciones](../vsto/actions-pane-overview.md)
- [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Tutorial: Insertar texto en un documento desde un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Tutorial: Insertar texto en un documento desde un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
