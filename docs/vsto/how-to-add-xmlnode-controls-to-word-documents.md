---
title: 'Cómo: agregar controles XMLNode a documentos de Word | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4dd214262f66bfa21cdb168e948c70437487761e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Cómo: Agregar controles XMLNode a documentos de Word
  **Importante** la información que figura en este tema con respecto a Microsoft Word está presentado exclusivamente para el beneficio y el uso de personas y organizaciones que se encuentran fuera de Estados Unidos y sus territorios o que está usando, o del desarrollo programas que se ejecutan en, productos de Microsoft Word que se autoriza el uso de Microsoft antes de enero de 2010, cuando Microsoft quita una implementación de funcionalidad concreta relacionada con XML personalizado de Microsoft Word. Esta información con respecto a Microsoft Word no puede leer o utilizada por personas u organizaciones en Estados Unidos o en sus territorios que están usando o desarrollar programas que se ejecutan en productos de Microsoft Word que se usan bajo licencia Microsoft después de 10 de enero de 2010 ; los productos no comportarán igual que los productos con licencia antes de esa fecha o adquirido y licencia para su uso fuera de Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Al asignar un elemento de esquema XML no repetitivo a un documento de Microsoft Office Word, Visual Studio agrega automáticamente un <xref:Microsoft.Office.Tools.Word.XMLNode> control al documento. Para obtener información acerca de cómo asignar elementos de esquema XML de repetición, consulte [Cómo: agregar controles XMLNodes a documentos de Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).  
  
> [!NOTE]  
>  El <xref:Microsoft.Office.Tools.Word.XMLNode> control no está disponible en la **cuadro de herramientas** o **orígenes de datos** ventana y no se puede crear mediante programación.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnode-control-to-a-document"></a>Para agregar un control XMLNode a un documento  
  
1.  En el documento en el Diseñador de Visual Studio, en la cinta de opciones, haga clic en el **Developer** ficha.  
  
    > [!NOTE]  
    >  Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, consulta [Cómo: Mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  En el **XML** grupo, haga clic en **esquema**.  
  
     El **plantillas y complementos** abre el cuadro de diálogo.  
  
3.  Haga clic en el **esquema XML** ficha.  
  
4.  Haga clic en **Agregar esquema**.  
  
     El **Agregar esquema** abre el cuadro de diálogo.  
  
5.  Seleccione un esquema XML que contiene los elementos de esquema no repetitivo de la **Agregar esquema** cuadro de diálogo y haga clic en **abiertos**.  
  
     El **configuración del esquema** aparece el cuadro de diálogo.  
  
6.  Asignar un alias o haga clic en **Aceptar** para agregar el esquema sin un alias.  
  
     El esquema se agrega a la **Agregar esquema** cuadro de diálogo.  
  
7.  En el **Agregar esquema** cuadro de diálogo, haga clic en **Aceptar**.  
  
8.  El **estructura XML** abre el panel de tareas.  
  
9. Haga clic en el elemento de esquema no repetitivo en el **estructura XML** panel de tareas para agregar al documento.  
  
     Un <xref:Microsoft.Office.Tools.Word.XMLNode> control se crea y se agrega al proyecto.  
  
## <a name="see-also"></a>Vea también  
 [XMLNode (Control)](../vsto/xmlnode-control.md)   
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  