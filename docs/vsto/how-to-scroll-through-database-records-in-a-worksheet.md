---
title: 'Cómo: desplazarse por los registros de base de datos de una hoja de cálculo'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8127a5f61e292fb777be4854796535bbe01226aa
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545800"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Cómo: desplazarse por los registros de base de datos de una hoja de cálculo
  En el procedimiento siguiente se muestra cómo usar el diseñador para mostrar un solo campo de una tabla de base de datos en una hoja de cálculo de Excel de Microsoft Office, con controles que permiten al usuario final desplazarse por todos los registros.

 Puede usar el diseñador solo en proyectos de nivel de documento. Sin embargo, también puede Agregar controles y enlazarlos a datos mediante programación en tiempo de ejecución. Para obtener más información, vea [Tutorial: enlace de datos simple en un proyecto de complemento de VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Para desplazarse por los registros de base de datos de una hoja de cálculo

1. Abra un proyecto de aplicación de Excel en Visual Studio.

2. Abra la ventana **orígenes de datos** y cree un origen de datos a partir de la base de datos. Para obtener más información, consulte [Agregar nuevas conexiones](../data-tools/add-new-connections.md).

3. Expanda la tabla que contiene los datos que desea mostrar y seleccione la columna específica.

4. Abra la lista de controles y seleccione **NamedRange**.

5. Arrastre el <xref:Microsoft.Office.Tools.Excel.NamedRange> control hasta la celda en la que desea que aparezcan los datos.

6. En la pestaña **Windows Forms** del **cuadro de herramientas**, agregue un <xref:System.Windows.Forms.BindingNavigator> control a la hoja de cálculo y configure los controles que desea usar. Para obtener más información, vea [información general sobre el control BindingNavigator &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Consulte también
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
