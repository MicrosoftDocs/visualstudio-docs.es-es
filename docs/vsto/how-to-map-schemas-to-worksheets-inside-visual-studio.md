---
title: Procedimiento Asignar esquemas a hojas de cálculo en Visual Studio
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d01d68404314b366e968f0c2551352d8501ed9ae
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866339"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Procedimiento Asignar esquemas a hojas de cálculo en Visual Studio
  Puede asignar un esquema XML a una hoja de cálculo mientras la hoja de cálculo está abierto en Visual Studio. Use las mismas herramientas de Microsoft Office Excel que usan cuando el libro se abre fuera de Visual Studio. El proyecto de Office crea los mismos objetos independientemente de si asigna el esquema de la hoja de cálculo antes o después de crear la solución de Excel.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  No se puede usar los esquemas XML con varias partes en soluciones de Excel.  
  
## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Para asignar un esquema XML a una hoja de cálculo de Excel en Visual Studio  
  
1.  Abra el proyecto de libro o plantilla de Excel en Visual Studio.  
  
2.  Haga clic en la hoja de cálculo para mover el foco al diseñador.  
  
3.  En la cinta de opciones, haga clic en la pestaña **Desarrollador** .  
  
    > [!NOTE]  
    >  Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, vea [Cómo: Mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  En el **XML** grupo, haga clic en **origen**.  
  
     El **origen XML** abre la ventana.  
  
5.  En el **origen XML** ventana, haga clic en **mapas XML**.  
  
     El **mapas XML** abre el cuadro de diálogo.  
  
6.  En el **mapas XML** cuadro de diálogo, haga clic en **agregar**.  
  
7.  Busque el archivo de esquema, selecciónelo y, a continuación, haga clic en **abierto**.  
  
8.  Haga clic en **Aceptar**.  
  
     El esquema se representa en el **origen XML** ventana. En el proyecto, con tipo <xref:System.Data.DataSet> se genera basándose en el esquema y un <xref:System.Windows.Forms.BindingSource> se crea.  
  
9. Arrastre elementos desde el **origen XML** ventana a los lugares en la hoja de cálculo donde desea que los controles correspondientes a crearse.  
  
     Si arrastra un elemento de esquema no es de repetición, el proyecto de Office genera una <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control que se enlaza automáticamente a la <xref:System.Windows.Forms.BindingSource>.  
  
     Si arrastra un elemento de esquema repetitivo, el proyecto de Office genera un <xref:Microsoft.Office.Tools.Excel.ListObject> control que no se enlaza automáticamente a un origen de datos. Para obtener más información, consulte [esquemas XML y los datos en el nivel de documento personalizaciones](../vsto/xml-schemas-and-data-in-document-level-customizations.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Esquemas y datos en las personalizaciones de nivel de documento XML](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
