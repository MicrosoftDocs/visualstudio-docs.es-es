---
title: Procedimiento Agregar controles XMLNodes a documentos de Word
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b27753590ea84fac6029bea0919a1aeda90543fa
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647141"
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>Procedimiento Agregar controles XMLNodes a documentos de Word
  **Importante** la información en este tema con respecto a Microsoft Word se presenta exclusivamente para el uso y disfrute de individuos y organizaciones que se encuentran fuera de Estados Unidos y sus territorios o quién está usando o desarrollo programas que se ejecutan en, los productos de Microsoft Word que se licencia de Microsoft antes de enero de 2010, cuando Microsoft quita una implementación de la funcionalidad concreta relacionadas con XML personalizado de Microsoft Word. Esta información con respecto a Microsoft Word no puede ser leída o utilizada por personas u organizaciones en Estados Unidos o en sus territorios que utiliza, o desarrollar programas que se ejecutan en los productos de Microsoft Word que se licencia de Microsoft después de 10 de enero de 2010 ; los productos no comportarán igual que los productos con licencia antes de esa fecha o adquirido y con licencia para su uso fuera de Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Al asignar un elemento repetitivo de esquema XML a un documento de Microsoft Office Word, Visual Studio agrega automáticamente un <xref:Microsoft.Office.Tools.Word.XMLNodes> control al documento.  
  
 Para obtener información sobre cómo asignar elementos de esquema XML no repetitivo, vea [Cómo: Agregar controles XMLNode a documentos de Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
> [!NOTE]  
>  El <xref:Microsoft.Office.Tools.Word.XMLNodes> control no está disponible desde el **cuadro de herramientas** o **orígenes de datos** ventana, ni puede crearse mediante programación.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnodes-control-to-a-document"></a>Para agregar un control XMLNodes a un documento  
  
1.  En el documento en el Diseñador de Visual Studio, en la cinta de opciones, haga clic en el **Developer** ficha.  
  
    > [!NOTE]  
    >  Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, vea [Cómo: Mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  En el **XML** grupo, haga clic en **esquema**.  
  
     El **plantillas y complementos** abre el cuadro de diálogo.  
  
3.  Haga clic en el **esquema XML** ficha.  
  
4.  Haga clic en **Agregar esquema**.  
  
     El **Agregar esquema** abre el cuadro de diálogo.  
  
5.  Seleccione un esquema XML que contiene los elementos de esquema de repetición y haga clic en **abierto**.  
  
     El **configuración del esquema** aparece el cuadro de diálogo.  
  
6.  Asignar un alias o haga clic en **Aceptar** para agregar el esquema sin un alias.  
  
     El esquema se agrega a la **Agregar esquema** cuadro de diálogo.  
  
7.  En el **Agregar esquema** cuadro de diálogo, haga clic en **Aceptar**.  
  
     El **estructura XML** abre el panel de tareas.  
  
8.  Haga clic en el elemento de esquema repetitivo en el **estructura XML** panel de tareas para agregarlo al documento.  
  
     Un <xref:Microsoft.Office.Tools.Word.XMLNodes> control se crea y se agrega al proyecto.  
  
## <a name="see-also"></a>Vea también  
 [XMLNodes (control)](../vsto/xmlnodes-control.md)   
 [Automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  