---
title: "Obtener acceso a la cinta de opciones en tiempo de ejecución | Documentos de Microsoft"
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
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
ms.assetid: 8a7c7c6d-1a18-4d6b-98ee-e483d41f0cd8
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f69818d2e7c1b6ef2babd651247fe81709b80097
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="accessing-the-ribbon-at-run-time"></a>Obtener acceso a la cinta de opciones en tiempo de ejecución
  Puede escribir código para mostrar, ocultar y modificar la cinta de opciones y permitir a los usuarios ejecutar el código desde los controles de un panel de tareas personalizado, un panel de acciones o un área del formulario de Outlook.  
  
 Puede acceder a la cinta de opciones mediante la clase `Globals`. Para los proyectos de Outlook, puede acceder a las cintas de opciones que aparecen en una ventana específica del Inspector de Outlook o del Explorador de Outlook.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="accessing-the-ribbon-by-using-the-globals-class"></a>Acceder a la cinta de opciones mediante la clase Globals  
 Puede usar la clase `Globals` para acceder a la cinta de opciones de un proyecto de nivel de documento o un proyecto de complemento de VSTO desde cualquier lugar del proyecto.  
  
 Para obtener más información sobre la `Globals` de clases, consulte [acceso Global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 En el ejemplo siguiente se usa la clase `Globals` para acceder a una cinta personalizada llamada `Ribbon1` y establecer el texto que aparece en un cuadro combinado de la cinta de opciones para `Hello World`.  
  
 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]  
  
## <a name="accessing-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Acceder a una colección de cintas de opciones que aparecen en una ventana específica del Inspector de Outlook  
 Puede tener acceso a una colección de cintas de opciones que aparecen en Outlook *inspectores*. Un Inspector es una ventana que se abre en Outlook cuando los usuarios realizan ciertas tareas, como crear mensajes de correo electrónico. Para acceder a la cinta de opciones de una ventana del Inspector, llame a la propiedad `Ribbons` de la clase `Globals` y pase un objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> que representa el Inspector.  
  
 En el ejemplo siguiente se obtiene la colección de la cinta de opciones del Inspector que actualmente tiene el foco. A continuación, se accede a una cinta de opciones llamada `Ribbon1` y se establece el texto que aparece en un cuadro combinado de la cinta de opciones para `Hello World`.  
  
 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]  
  
## <a name="accessing-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Acceder a una colección de cintas de opciones que aparecen para un Explorador de Outlook específico  
 Puede tener acceso a una colección de cintas de opciones que aparecen en un Outlook *Explorer*. Un explorador es la interfaz de usuario (UI) de la aplicación principal de una instancia de Outlook. Para acceder a la cinta de opciones de una ventana del Explorador, llame a la propiedad `Ribbons` de la clase `Globals` y pase un objeto <xref:Microsoft.Office.Interop.Outlook.Explorer> que representa el Explorador.  
  
 En el ejemplo siguiente se obtiene la colección de la cinta de opciones del Explorador que actualmente tiene el foco. A continuación, se accede a una cinta de opciones llamada `Ribbon1` y se establece el texto que aparece en un cuadro combinado de la cinta de opciones para `Hello World`.  
  
 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]  
  
## <a name="see-also"></a>Vea también  
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [Diseñador de la cinta](../vsto/ribbon-designer.md)   
 [XML de la cinta de opciones](../vsto/ribbon-xml.md)   
 [Información general sobre el modelo de objetos de la cinta de opciones](../vsto/ribbon-object-model-overview.md)   
 [Tutorial: Crear una pestaña personalizada usando el Diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Tutorial: Actualizar los controles de una cinta de opciones en tiempo de ejecución](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Obtener acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)  
  
  