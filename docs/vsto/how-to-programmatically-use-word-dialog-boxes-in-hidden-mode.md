---
title: "Cómo: usar mediante programación los cuadros de diálogo de Word en modo oculto | Documentos de Microsoft"
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
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
ms.assetid: a5619325-8b54-41f1-becb-3f6eae7e4a6b
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3d36bb9342c1db3fcf0fe007b87831b8c921af6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Cómo: Usar cuadros de diálogo de Word en modo oculto mediante programación
  Puede realizar operaciones complejas con una llamada al método invocando los cuadros de diálogo integrados en Microsoft Office Word sin mostrarlos al usuario. Puede hacerlo mediante el uso de la <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> método de la <xref:Microsoft.Office.Interop.Word.Dialog> objeto sin llamar a la <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> método.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="examples"></a>Ejemplos  
 Los ejemplos de código siguientes muestran cómo utilizar el **Configurar página** cuadro de diálogo en modo oculto para establecer varias páginas de propiedades de configuración sin intervención del usuario. Los ejemplos utilizan un <xref:Microsoft.Office.Interop.Word.Dialog> objeto que se va a configurar un tamaño de página personalizado. La configuración específica para la instalación de la página, como el margen superior, margen inferior etc., está disponible como propiedades en tiempo de ejecución de la <xref:Microsoft.Office.Interop.Word.Dialog> objeto. Estas propiedades se crean dinámicamente por Word en tiempo de ejecución.  
  
 En el ejemplo siguiente se muestra cómo realizar esta tarea en proyectos de Visual Basic donde **Option Strict** está desactivada y en los proyectos de Visual C# que tienen como destino el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. En estos proyectos, puede usar características de enlace de tiempo de ejecución en los compiladores de Visual Basic y Visual C#. Para usar este ejemplo, ejecútelo desde la `ThisDocument` o `ThisAddIn` clase en su proyecto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]  
  
 En el ejemplo siguiente se muestra cómo realizar esta tarea en proyectos de Visual Basic donde **Option Strict** se encuentra en. En estos proyectos, debe usar la reflexión para tener acceso a las propiedades de tiempo de ejecución. Para usar este ejemplo, ejecútelo desde la `ThisDocument` o `ThisAddIn` clase en su proyecto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: usar mediante programación los cuadros de diálogo integrados en Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Enlace tardío en soluciones de Office](../vsto/late-binding-in-office-solutions.md)   
 [Reflexión (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflexión (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  