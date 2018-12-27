---
title: Procedimiento Impedir que Outlook muestre un área de formulario
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0aaeafe14f35092be30c982ebb758e40afedb8aa
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647086"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Procedimiento Impedir que Outlook muestre un área de formulario
  Puede haber situaciones en las que no desea que Microsoft Office Outlook muestre un área de formulario de un elemento determinado. Por ejemplo, si un elemento de contacto no contiene una dirección de la empresa, puede evitar un área de formulario que muestra la ubicación de la empresa en un mapa de encendido.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Para impedir que Outlook muestre un área de formulario  
  
1. Abra el archivo de código para el área de formulario que desea modificar.  
  
2. Expanda el **generador de áreas de formulario** región de código.  
  
3. Agregue código a la `FormRegionInitializing` controlador de eventos que establece el <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propiedad de la <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> clase a **true**.  
  
   En este ejemplo, si el elemento de contacto no contiene una dirección, el <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propiedad está establecida en **true**, y no aparece el área de formulario.  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
## <a name="see-also"></a>Vea también  
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Tutorial: Diseñar un formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Tutorial: Diseñar un formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Tutorial: Importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  