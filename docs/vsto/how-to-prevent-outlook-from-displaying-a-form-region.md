---
title: "C&#243;mo: Impedir que Outlook muestre un &#225;rea de formulario"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "cancelar visualización del área de formulario"
  - "áreas de formulario [desarrollo de Office en Visual Studio], cancelar la visualización"
ms.assetid: 82a25def-776a-476a-a72d-d0a48a827d3c
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# C&#243;mo: Impedir que Outlook muestre un &#225;rea de formulario
  Es posible que haya situaciones en las que desee que Microsoft Office Outlook no muestre un área de formulario para un elemento determinado.  Por ejemplo, si un elemento de contacto no contiene una dirección profesional, puede evitar que aparezca un área de formulario que muestre la ubicación de la empresa en un mapa.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### Para impedir que Outlook muestre un área de formulario  
  
1.  Abra el archivo de código del área de formulario que desea modificar.  
  
2.  Expanda el área de código **Generador de áreas de formulario**.  
  
3.  Agregue código al controlador de eventos  `FormRegionInitializing` que establezca la propiedad <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> de la clase <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> en **true**.  
  
 En este ejemplo, si el elemento de contacto no contiene una dirección, la propiedad <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> se establece en **true** y no aparece el área de formulario.  
  
## Ejemplo  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#1)]  
  
## Vea también  
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Tutorial: Importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  