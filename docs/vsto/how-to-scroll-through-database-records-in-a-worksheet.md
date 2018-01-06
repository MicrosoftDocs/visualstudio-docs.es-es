---
title: "Cómo: desplazarse por registros de base de datos en una hoja de cálculo | Documentos de Microsoft"
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
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
ms.assetid: aea4c86c-9d6d-47dd-8977-066e21945dab
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6e3dcc6d0ed711d41fd47f043177e5d172193249
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Cómo: Desplazarse por los registros de una base de datos en una hoja de cálculo
  El siguiente procedimiento muestra cómo utilizar el diseñador para mostrar un único campo de una tabla de base de datos en una hoja de cálculo de Microsoft Office Excel, con controles que permiten al usuario final para desplazarse por todos los registros.  
  
 Puede utilizar el diseñador exclusivamente en proyectos de nivel de documento. Sin embargo, también puede agregar controles y enlazarlos a datos mediante programación en tiempo de ejecución. Para obtener más información, consulte [Tutorial: enlace de datos complejos en VSTO complemento proyecto](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### <a name="to-scroll-through-database-records-in-a-worksheet"></a>Para desplazarse por registros de base de datos en una hoja de cálculo  
  
1.  Abra un proyecto de aplicación de Excel en Visual Studio.  
  
2.  Abra la **orígenes de datos** ventana y crear un origen de datos de la base de datos. Para obtener más información, consulte [agregar nuevas conexiones](../data-tools/add-new-connections.md).  
  
3.  Expanda la tabla que contiene los datos que desea mostrar y seleccione la columna concreta.  
  
4.  Abra la lista de controles y seleccione **NamedRange**.  
  
5.  Arrastre el <xref:Microsoft.Office.Tools.Excel.NamedRange> control a la celda donde desea que aparezcan los datos.  
  
6.  Desde el **formularios Windows Forms** pestaña de la **cuadro de herramientas**, agregar un <xref:System.Windows.Forms.BindingNavigator> el control a la hoja de cálculo y configurar los controles que se va a utilizar. Para obtener más información, vea [información general del Control BindingNavigator &#40; Formularios Windows Forms &#41; ](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Vea también  
 [Enlace de datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  