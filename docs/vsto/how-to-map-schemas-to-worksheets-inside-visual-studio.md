---
title: 'Cómo: asignar esquemas a hojas de cálculo en Visual Studio'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: c8a0437b940953e89e24969314f63df34d223496
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538143"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Cómo: asignar esquemas a hojas de cálculo en Visual Studio
  Puede asignar un esquema XML a una hoja de cálculo mientras la hoja de cálculo está abierta en Visual Studio. Use la misma Microsoft Office herramientas de Excel que utiliza cuando el libro está abierto fuera de Visual Studio. El proyecto de Office crea los mismos objetos si asigna el esquema a la hoja de cálculo antes o después de crear la solución de Excel.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> No puede utilizar esquemas XML de varias partes en soluciones de Excel.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Para asignar un esquema XML a una hoja de cálculo de Excel en Visual Studio

1. Abra el libro de Excel o el proyecto de plantilla dentro de Visual Studio.

2. Haga clic en la hoja de cálculo para pasar el foco al diseñador.

3. En la cinta de opciones, haga clic en la pestaña **Desarrollador** .

    > [!NOTE]
    > Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, consulte [Cómo: Mostrar la pestaña programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. En el grupo **XML** , haga clic en **origen**.

     Se abrirá la ventana **origen XML** .

5. En la ventana **origen XML** , haga clic en **asignaciones XML**.

     Se abrirá el cuadro de diálogo **asignaciones XML** .

6. En el cuadro de diálogo **asignaciones XML** , haga clic en **Agregar**.

7. Busque el archivo de esquema, selecciónelo y, a continuación, haga clic en **abrir**.

8. Haga clic en **Aceptar**.

     El esquema se representa en la ventana de **código fuente XML** . En el proyecto, <xref:System.Data.DataSet> se genera un tipo basado en el esquema y <xref:System.Windows.Forms.BindingSource> se crea un.

9. Arrastre los elementos desde la ventana de **código fuente XML** hasta los lugares de la hoja de cálculo en los que desea crear los controles correspondientes.

     Si arrastra un elemento de esquema que no es de repetición, el proyecto de Office genera un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control que se enlaza automáticamente a <xref:System.Windows.Forms.BindingSource> .

     Si arrastra un elemento de esquema repetitivo, el proyecto de Office genera un <xref:Microsoft.Office.Tools.Excel.ListObject> control que no se enlaza automáticamente a un origen de datos. Para obtener más información, vea [esquemas y datos XML en personalizaciones de nivel de documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md).

## <a name="see-also"></a>Consulte también
- [Cómo: asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Esquemas y datos XML en personalizaciones de nivel de documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
