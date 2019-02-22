---
title: Filtrar Agregar controles XMLNode a documentos de Word
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 08ab6ab47ff3c916b2818d9cceac1ee839939a42
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638483"
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Procedimiento Agregar controles XMLNode a documentos de Word
  **Importante** la información en este tema con respecto a Microsoft Word se presenta exclusivamente para el uso y disfrute de individuos y organizaciones que se encuentran fuera de Estados Unidos y sus territorios o quién está usando o desarrollo programas que se ejecutan en, los productos de Microsoft Word que se licencia de Microsoft antes de enero de 2010, cuando Microsoft quita una implementación de la funcionalidad concreta relacionadas con XML personalizado de Microsoft Word. Esta información con respecto a Microsoft Word no puede ser leída o utilizada por personas u organizaciones en Estados Unidos o en sus territorios que utiliza, o desarrollar programas que se ejecutan en los productos de Microsoft Word que se licencia de Microsoft después de 10 de enero de 2010 ; los productos no comportarán igual que los productos con licencia antes de esa fecha o adquirido y con licencia para su uso fuera de Estados Unidos.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Al asignar un elemento de esquema XML no repetitivo a un documento de Microsoft Office Word, Visual Studio agrega automáticamente un <xref:Microsoft.Office.Tools.Word.XMLNode> control al documento. Para obtener información sobre cómo asignar elementos repetidos del esquema XML, vea [Cómo: Agregar controles XMLNodes a documentos de Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).

> [!NOTE]
>  El <xref:Microsoft.Office.Tools.Word.XMLNode> control no está disponible desde el **cuadro de herramientas** o **orígenes de datos** ventana y no se puede crear mediante programación.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnode-control-to-a-document"></a>Para agregar un XMLNode (control) a un documento

1.  En el documento en el Diseñador de Visual Studio, en la cinta de opciones, haga clic en el **Developer** ficha.

    > [!NOTE]
    >  Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, vea [Cómo: Mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

2.  En el **XML** grupo, haga clic en **esquema**.

     El **plantillas y complementos** abre el cuadro de diálogo.

3.  Haga clic en el **esquema XML** ficha.

4.  Haga clic en **Agregar esquema**.

     El **Agregar esquema** abre el cuadro de diálogo.

5.  Seleccione un esquema XML que contiene los elementos de esquema no es de repetición de la **Agregar esquema** cuadro de diálogo y haga clic en **abierto**.

     El **configuración del esquema** aparece el cuadro de diálogo.

6.  Asignar un alias o haga clic en **Aceptar** para agregar el esquema sin un alias.

     El esquema se agrega a la **Agregar esquema** cuadro de diálogo.

7.  En el **Agregar esquema** cuadro de diálogo, haga clic en **Aceptar**.

8.  El **estructura XML** abre el panel de tareas.

9. Haga clic en el elemento de esquema no repetitivo en el **estructura XML** panel de tareas para agregarlo al documento.

     Un <xref:Microsoft.Office.Tools.Word.XMLNode> control se crea y se agrega al proyecto.

## <a name="see-also"></a>Vea también
- [XMLNode (control)](../vsto/xmlnode-control.md)
- [Automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
