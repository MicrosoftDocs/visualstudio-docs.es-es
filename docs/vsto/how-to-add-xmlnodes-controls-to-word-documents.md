---
title: "Cómo: agregar controles XMLNodes a documentos de Word | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
ms.assetid: 315c6def-51f6-4ba6-bd9e-55cdf70f15bf
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ad54a3f554de6212f1bdeaeb6ba23dcbdbfce6c8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>Cómo: Agregar controles XMLNodes a documentos de Word
  **Importante** la información que figura en este tema con respecto a Microsoft Word está presentado exclusivamente para el beneficio y el uso de personas y organizaciones que se encuentran fuera de Estados Unidos y sus territorios o que está usando, o del desarrollo programas que se ejecutan en, productos de Microsoft Word que se autoriza el uso de Microsoft antes de enero de 2010, cuando Microsoft quita una implementación de funcionalidad concreta relacionada con XML personalizado de Microsoft Word. Esta información con respecto a Microsoft Word no puede leer o utilizada por personas u organizaciones en Estados Unidos o en sus territorios que están usando o desarrollar programas que se ejecutan en productos de Microsoft Word que se usan bajo licencia Microsoft después de 10 de enero de 2010 ; los productos no comportarán igual que los productos con licencia antes de esa fecha o adquirido y licencia para su uso fuera de Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Al asignar un elemento de esquema XML repetitivo a un documento de Microsoft Office Word, Visual Studio agrega automáticamente un <xref:Microsoft.Office.Tools.Word.XMLNodes> control al documento.  
  
 Para obtener información acerca de cómo asignar elementos de esquema XML no repetitivo, consulte [Cómo: agregar controles XMLNode a documentos de Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
> [!NOTE]  
>  El <xref:Microsoft.Office.Tools.Word.XMLNodes> control no está disponible en la **cuadro de herramientas** o **orígenes de datos** ventana, así como tampoco puede crearse mediante programación.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnodes-control-to-a-document"></a>Para agregar un control XMLNodes a un documento  
  
1.  En el documento en el Diseñador de Visual Studio, en la cinta de opciones, haga clic en el **Developer** ficha.  
  
    > [!NOTE]  
    >  Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, consulta [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  En el **XML** grupo, haga clic en **esquema**.  
  
     El **plantillas y complementos** abre el cuadro de diálogo.  
  
3.  Haga clic en el **esquema XML** ficha.  
  
4.  Haga clic en **Agregar esquema**.  
  
     El **Agregar esquema** abre el cuadro de diálogo.  
  
5.  Seleccione un esquema XML que contiene elementos de esquema de repetición y haga clic en **abiertos**.  
  
     El **configuración del esquema** aparece el cuadro de diálogo.  
  
6.  Asignar un alias o haga clic en **Aceptar** para agregar el esquema sin un alias.  
  
     El esquema se agrega a la **Agregar esquema** cuadro de diálogo.  
  
7.  En el **Agregar esquema** cuadro de diálogo, haga clic en **Aceptar**.  
  
     El **estructura XML** abre el panel de tareas.  
  
8.  Haga clic en el elemento de esquema repetitivo en el **estructura XML** panel de tareas para agregar al documento.  
  
     Un <xref:Microsoft.Office.Tools.Word.XMLNodes> control se crea y se agrega al proyecto.  
  
## <a name="see-also"></a>Vea también  
 [XMLNodes (Control)](../vsto/xmlnodes-control.md)   
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  