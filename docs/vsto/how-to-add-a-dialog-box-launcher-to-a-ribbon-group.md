---
title: Procedimiento Agregar un selector de cuadro de diálogo a un grupo de cinta de opciones
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aa12fdc3eea5c353071fb4a80e2c99f2f9e060c2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629955"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Filtrar Agregar un selector de cuadro de diálogo a un grupo de cinta de opciones
  Puede agregar un selector de cuadro de diálogo a cualquier grupo de una cinta. Un selector de cuadro de diálogo es un pequeño icono que aparece en un grupo. Los usuarios, haga clic en este icono para abrir cuadros de diálogo relacionados o paneles de tareas que proporcionan más opciones que se relacionan con el grupo.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Para agregar un selector de cuadro de diálogo a un grupo de cinta de opciones

1.  Seleccione el archivo de código de la cinta de opciones (*.vb* o *.cs* archivo) en **el Explorador de soluciones**.

2.  En el **vista** menú, haga clic en **diseñador**.

3.  En el Diseñador de cinta de opciones, haga clic en cualquier grupo y, a continuación, haga clic en **agregar DialogBoxLauncher**.

     Agregue código a la <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> eventos del grupo para abrir un cuadro de diálogo integrado o personalizado.

## <a name="see-also"></a>Vea también
- [Información general de la cinta de opciones](../vsto/ribbon-overview.md)
- [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
- [Tutoriales y ejemplos de desarrollo de office](../vsto/office-development-samples-and-walkthroughs.md)
- [Diseñador de cinta](../vsto/ribbon-designer.md)
- [Información general sobre el modelo de objetos de cinta de opciones](../vsto/ribbon-object-model-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Cómo: Exportar una cinta desde el Diseñador de cinta de opciones a XML de la cinta](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Cómo: Cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)
- [Cómo: Agregar controles a la vista backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Cómo: Mostrar errores de interfaz de usuario del complemento](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Tutorial: Crear una pestaña personalizada usando el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Tutorial: Actualizar los controles de una cinta en tiempo de ejecución](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Tutorial: Crear una pestaña personalizada usando XML de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
