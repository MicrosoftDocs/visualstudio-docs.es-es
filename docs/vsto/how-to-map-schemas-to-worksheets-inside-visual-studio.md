---
title: "Cómo: asignar esquemas a hojas de cálculo dentro de Visual Studio | Documentos de Microsoft"
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
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
ms.assetid: cef3f751-c1cf-46f3-9177-0bacdcee4121
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c09c99bc5d8bc964ae3afd82fe7a4a9fd5764edd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Cómo: Asignar esquemas a hojas de cálculo en Visual Studio
  Puede asignar un esquema XML a una hoja de cálculo mientras la hoja de cálculo está abierta en Visual Studio. Use las mismas herramientas de Microsoft Office Excel que usan cuando el libro está abierto fuera de Visual Studio. El proyecto de Office crea los mismos objetos independientemente de si asigna el esquema a la hoja de cálculo antes o después de crear la solución de Excel.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  No se puede utilizar esquemas XML compuestos en soluciones de Excel.  
  
### <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Para asignar un esquema XML a una hoja de cálculo de Excel en Visual Studio  
  
1.  Abra el proyecto de libro o plantilla de Excel en Visual Studio.  
  
2.  Haga clic en la hoja de cálculo para mover el foco al diseñador.  
  
3.  En la cinta de opciones, haga clic en la pestaña **Desarrollador** .  
  
    > [!NOTE]  
    >  Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, consulta [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  En el **XML** grupo, haga clic en **origen**.  
  
     El **origen XML** abre la ventana.  
  
5.  En el **origen XML** ventana, haga clic en **asignaciones XML**.  
  
     El **asignaciones XML** abre el cuadro de diálogo.  
  
6.  En el **asignaciones XML** cuadro de diálogo, haga clic en **agregar**.  
  
7.  Vaya al archivo de esquema, selecciónelo y, a continuación, haga clic en **abiertos**.  
  
8.  Haga clic en **Aceptar**.  
  
     El esquema se representa en el **origen XML** ventana. En el proyecto, un tipo <xref:System.Data.DataSet> se genera basándose en el esquema y un <xref:System.Windows.Forms.BindingSource> se crea.  
  
9. Arrastre elementos desde la **origen XML** ventana hasta los lugares de la hoja de cálculo donde desea que los controles correspondientes que se va a crear.  
  
     Si arrastra un elemento de esquema no repetitivo, el proyecto de Office genera una <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control que se enlaza automáticamente a la <xref:System.Windows.Forms.BindingSource>.  
  
     Si arrastra un elemento de esquema repetitivo, el proyecto de Office genera una <xref:Microsoft.Office.Tools.Excel.ListObject> control que no se enlaza automáticamente a un origen de datos. Para obtener más información, consulte [esquemas y datos en las personalizaciones de nivel de documento XML](../vsto/xml-schemas-and-data-in-document-level-customizations.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Esquemas y datos XML en personalizaciones de nivel de documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  