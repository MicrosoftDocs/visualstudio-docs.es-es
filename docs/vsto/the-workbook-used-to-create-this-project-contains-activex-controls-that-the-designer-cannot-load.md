---
title: El libro usado para crear este proyecto contiene controles ActiveX que no se puede cargar el diseñador | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8d31674f54ce454db50a63572c24f92031e7d886
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>El libro usado para crear este proyecto contiene controles ActiveX que el diseñador no puede cargar
  Este error aparece cuando se agrega un control a un documento de Word o a una hoja de cálculo de Excel, se guarda el documento o libro mediante programación y, a continuación, se crea una nueva solución en el nivel del documento basada en el documento o libro.  
  
 La información que describe el tipo administrado del control no se guarda con el documento ni con el libro. Al crear una nueva solución basada en ese documento o libro, Visual Studio no tiene bastante información para cargar el control en el diseñador del elemento host.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Abra el documento o el libro.  
  
2.  Quite los controles que se agregaron en tiempo de ejecución. Puede hacerlo seleccionándolos en el documento o en el libro y presionando la tecla SUPR.  
  
3.  Cree una solución en el nivel del documento basada en el documento o en el libro.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  