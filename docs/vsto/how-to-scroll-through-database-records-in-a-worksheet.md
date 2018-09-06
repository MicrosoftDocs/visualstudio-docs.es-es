---
title: 'Cómo: desplazarse por los registros de base de datos en una hoja de cálculo'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e9ffaffdefda98e3e074467fcd4df8cacce91b4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674875"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Cómo: desplazarse por los registros de base de datos en una hoja de cálculo
  El procedimiento siguiente muestra cómo usar el diseñador para mostrar un único campo de una tabla de base de datos en una hoja de cálculo de Microsoft Office Excel, con controles que permiten al usuario final para desplazarse por todos los registros.  
  
 Puede utilizar el diseñador solo en los proyectos de nivel de documento. Sin embargo, también puede agregar controles y enlazarlos a datos mediante programación en tiempo de ejecución. Para obtener más información, consulte [Tutorial: enlace de datos Simple en el proyecto de complemento VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Desplazarse por los registros de base de datos en una hoja de cálculo  
  
1.  Abra un proyecto de aplicación de Excel en Visual Studio.  
  
2.  Abra el **orígenes de datos** ventana y crear un origen de datos de la base de datos. Para obtener más información, consulte [agregar nuevas conexiones](../data-tools/add-new-connections.md).  
  
3.  Expanda la tabla que contiene los datos que desea mostrar y seleccionar la columna.  
  
4.  Abra la lista de controles y seleccione **NamedRange**.  
  
5.  Arrastre el <xref:Microsoft.Office.Tools.Excel.NamedRange> control en la celda donde desea que aparezcan los datos.  
  
6.  Desde el **Windows Forms** pestaña de la **cuadro de herramientas**, agregar un <xref:System.Windows.Forms.BindingNavigator> el control a la hoja de cálculo y configurar los controles que desee utilizar. Para obtener más información, consulte [información general del control BindingNavigator &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  