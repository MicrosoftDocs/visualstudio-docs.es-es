---
title: 'Cómo: agregar controles XMLNode a documentos de Word'
description: Obtenga información sobre que al asignar un elemento de esquema XML que no se repite a un documento de Microsoft Office Word, Visual Studio agrega automáticamente un control XMLNode al documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8b9deb6732552a827cb89465f6521bc566e8c46f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846745"
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Cómo: agregar controles XMLNode a documentos de Word
  **Importante** La información configurada en este tema con respecto a Microsoft Word se presenta exclusivamente para la ventaja y el uso de las personas y organizaciones que se encuentran fuera del Estados Unidos y de sus territorios, o bien el desarrollo de programas que se ejecutan en, productos de Microsoft Word con licencia de Microsoft antes de la 2010 de enero, cuando Microsoft quitó una implementación de funcionalidad específica relacionada con XML personalizado de Es posible que la información relativa a Microsoft Word no sea leída ni utilizada por personas u organizaciones en el Estados Unidos ni en sus territorios que utilicen o desarrollen programas que se ejecutan en, productos de Microsoft Word con licencia de Microsoft a partir del 10 de enero de 2010; Estos productos no se comportarán igual que los productos con licencia antes de esa fecha o adquiridos y con licencia para usarlos fuera del Estados Unidos.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Cuando se asigna un elemento de esquema XML que no es de repetición a un documento de Microsoft Office Word, Visual Studio agrega automáticamente un <xref:Microsoft.Office.Tools.Word.XMLNode> control al documento. Para obtener información sobre la asignación de elementos de esquema XML repetidos, vea [Cómo: agregar controles XMLNodes a documentos de Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).

> [!NOTE]
> El <xref:Microsoft.Office.Tools.Word.XMLNode> control no está disponible en el **cuadro de herramientas** o en la ventana **orígenes de datos** , y no se puede crear mediante programación.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnode-control-to-a-document"></a>Para agregar un control XMLNode a un documento

1. En el documento del diseñador de Visual Studio, en la cinta de opciones, haga clic en la pestaña **desarrollador** .

    > [!NOTE]
    > Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, consulte [Cómo: Mostrar la pestaña programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

2. En el grupo **XML** , haga clic en **esquema**.

     Se abrirá el cuadro de diálogo **plantillas y complementos** .

3. Haga clic en la pestaña **esquema XML** .

4. Haga clic en **Agregar esquema**.

     Se abre el cuadro de diálogo **Agregar esquema** .

5. Seleccione un esquema XML que contenga elementos de esquema que no sean de repetición en el cuadro de diálogo **Agregar esquema** y haga clic en **abrir**.

     Aparece el cuadro de diálogo **configuración de esquema** .

6. Asigne un alias o haga clic en **Aceptar** para agregar el esquema sin un alias.

     El esquema se agrega al cuadro de diálogo **Agregar esquema** .

7. En el cuadro de diálogo **Agregar esquema** , haga clic en **Aceptar**.

8. Se abre el panel de tareas **estructura XML** .

9. Haga clic en el elemento de esquema no repetitivo del panel de tareas **estructura XML** para agregarlo al documento.

     <xref:Microsoft.Office.Tools.Word.XMLNode>Se crea un control y se agrega al proyecto.

## <a name="see-also"></a>Vea también
- [XMLNode (control)](../vsto/xmlnode-control.md)
- [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
