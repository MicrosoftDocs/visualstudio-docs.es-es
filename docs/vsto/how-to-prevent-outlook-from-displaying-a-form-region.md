---
title: 'Cómo: Impedir que Outlook muestre un área de formulario'
description: Obtenga información sobre cómo evitar que Microsoft Office Outlook muestre un área de formulario para un elemento determinado.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1dc9322dd2ad3c3a2111222d7491f9e1a82cd6c4
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825854"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Cómo: Impedir que Outlook muestre un área de formulario
  Puede haber situaciones en las que no desee que Microsoft Office Outlook muestre un área de formulario para un elemento determinado. Por ejemplo, si un elemento de contacto no contiene una dirección de negocio, puede evitar que aparezca un área de formulario que muestre la ubicación de la empresa en un mapa.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Para evitar que Outlook muestre un área de formulario

1. Abra el archivo de código para el área de formulario que desea modificar.

2. Expanda la región **de código Generador de regiones** de formulario.

3. Agregue código al controlador `FormRegionInitializing` de eventos que establece la propiedad de la clase en <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> **true.**

   En este ejemplo, si el elemento de contacto no contiene una dirección, la propiedad se establece en true y el área <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> de formulario no aparece. 

## <a name="example"></a>Ejemplo
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet1":::


## <a name="see-also"></a>Consulte también
- [Creación de regiones de formulario de Outlook](../vsto/creating-outlook-form-regions.md)
- [Tutorial: Diseño de un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Tutorial: Diseño de un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Tutorial: Importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
