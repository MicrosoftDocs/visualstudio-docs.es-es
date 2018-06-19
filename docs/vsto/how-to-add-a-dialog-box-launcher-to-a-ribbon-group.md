---
title: 'Cómo: agregar un selector de cuadro de diálogo a un grupo de la cinta de opciones'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2513113b473341f2ed099ef0c5ff5961694acb19
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548398"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Cómo: agregar un selector de cuadro de diálogo a un grupo de la cinta de opciones
  Puede agregar un selector de cuadro de diálogo a cualquier grupo de una cinta de opciones. Un selector de cuadro de diálogo es un icono pequeño que aparece en un grupo. Los usuarios, haga clic en este icono para abrir cuadros de diálogo relacionados o paneles de tareas que proporcionan más opciones relacionadas con el grupo.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Para agregar un selector de cuadro de diálogo a un grupo de la cinta de opciones  
  
1.  Seleccione el archivo de código de la cinta de opciones (*.vb* o *.cs* archivo) en **el Explorador de soluciones**.  
  
2.  En el **vista** menú, haga clic en **diseñador**.  
  
3.  En el Diseñador de la cinta de opciones, haga clic en cualquier grupo y, a continuación, haga clic en **DialogBoxLauncher agregar**.  
  
     Agregue código a la <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> eventos del grupo para abrir un cuadro de diálogo integrado o personalizado.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Tutoriales y ejemplos de desarrollo de office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Diseñador de la cinta](../vsto/ribbon-designer.md)   
 [Información general sobre el modelo de objetos de la cinta de opciones](../vsto/ribbon-object-model-overview.md)   
 [XML de la cinta de opciones](../vsto/ribbon-xml.md)   
 [Cómo: exportar una cinta de opciones desde el Diseñador de la cinta de opciones a XML de la cinta de opciones](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Cómo: cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Cómo: personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)   
 [Cómo: agregar controles a la vista backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Cómo: empezar a personalizar la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Cómo: agregar en Mostrar errores de interfaz de usuario](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Tutorial: Crear una pestaña personalizada usando el Diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Tutorial: Actualizar los controles de una cinta de opciones en tiempo de ejecución](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Tutorial: Crear una pestaña personalizada usando XML de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  