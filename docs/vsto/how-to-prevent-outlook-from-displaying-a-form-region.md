---
title: "Cómo: impedir que Outlook muestre un área de formulario | Documentos de Microsoft"
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
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
ms.assetid: 82a25def-776a-476a-a72d-d0a48a827d3c
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fb181ba7bd408194bec52224496ebef7f343f5d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Cómo: Impedir que Outlook muestre un área de formulario
  Puede haber situaciones en las que no desea que Microsoft Office Outlook muestre un área de formulario de un elemento determinado. Por ejemplo, si un elemento de contacto no contiene una dirección de la empresa, puede evitar que un área de formulario que muestra la ubicación de la empresa en un mapa que aparezcan.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Para impedir que Outlook muestre un área de formulario  
  
1.  Abra el archivo de código para el área de formulario que desea modificar.  
  
2.  Expanda el **generador de áreas de formulario** región de código.  
  
3.  Agregue código a la `FormRegionInitializing` controlador de eventos que establece el <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propiedad de la <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> clase a **true**.  
  
 En este ejemplo, si el elemento de contacto no contiene una dirección, el <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propiedad está establecida en **true**, y no aparece el área de formulario.  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
## <a name="see-also"></a>Vea también  
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Cómo: agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Tutorial: Importación de un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  