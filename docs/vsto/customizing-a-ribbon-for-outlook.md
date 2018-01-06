---
title: Personalizar una cinta de opciones para Outlook | Documentos de Microsoft
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
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
ms.assetid: 11d10e72-806d-4d5e-b080-139bd8633eaa
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f44d1d8c2982e23995a3625205eaa0bddf7adc4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-a-ribbon-for-outlook"></a>Personalizar una cinta de opciones para Outlook
  Al personalizar la cinta en Microsoft Office Outlook, debe tener en cuenta dónde aparecerá la cinta personalizada en la aplicación. Outlook muestra la cinta en la interfaz de usuario (UI) de la aplicación principal y en las ventanas que se abren cuando los usuarios realizan ciertas tareas, como crear mensajes de correo electrónico. Estas ventanas de la aplicación se denominan inspectores.  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") para una demostración en vídeo relacionada, vea [Cómo: usar el Diseñador de la cinta de opciones para personalizar la cinta de opciones en Outlook?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="adding-a-custom-ribbon-to-the-main-application-ui"></a>Agregar una Cinta personalizada a la interfaz de usuario de la aplicación principal  
 La interfaz de usuario de la aplicación principal en Outlook se denomina Explorador. Si usas el **cinta (diseñador Visual)** producto, puede agregar una cinta de opciones al explorador haciendo clic en el **RibbonType** propiedad de la cinta de opciones en la **propiedades** ventana, y, a continuación, seleccione **Microsoft.Outlook.Explorer**.  
  
## <a name="assigning-a-ribbon-to-an-inspector"></a>Asignar una cinta a un Inspector  
 Para identificar el inspector que desea personalizar, debe especificar el tipo de cinta que corresponde a la clase de mensaje del Inspector.  
  
 Si usas el **cinta (diseñador Visual)** de elemento, haga clic en el **RibbonType** propiedad de la cinta de opciones en la **propiedades** ventana y, a continuación, seleccione uno o varios identificadores de la cinta de opciones la lista de valores.  
  
 Puede agregar más de una cinta a un proyecto. Si más de una cinta comparte el mismo identificador de cinta, invalide el método CreateRibbonExtensibilityObject en la `ThisAddin` clase de su proyecto para especificar qué cinta se mostrará en tiempo de ejecución. Para obtener más información, consulte [información general de la cinta de opciones](../vsto/ribbon-overview.md). Para obtener más información acerca de cada tipo de cinta de opciones, consulte el artículo técnico [personalizar la cinta en Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
## <a name="specifying-the-ribbon-type-by-using-ribbon-xml"></a>Especificar el Tipo de Cinta mediante código XML de Cinta  
 Si usas el **cinta (XML)** item, compruebe el valor de la *ribbonID* parámetro en el <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> método y devuelva la cinta adecuada.  
  
 Visual Studio genera automáticamente el método <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> en el archivo de código de la cinta. El *ribbonID* parámetro es una cadena que identifica el explorador o un tipo específico de inspector. Para obtener una lista completa de los valores posibles de la *ribbonID* parámetro, consulte el artículo técnico [personalizar la cinta en Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
 En el siguiente ejemplo de código se indica cómo mostrar una cinta personalizada únicamente en el inspector `Microsoft.Outlook.Mail.Compose`. Este es el inspector que se abre cuando un usuario crea un nuevo mensaje de correo electrónico. La cinta de opciones para mostrar se especifica en el `GetResourceText()` método, que se genera en el **cinta** clase. Para obtener más información sobre la **cinta** de clases, vea [XML de cinta de opciones](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]  
  
## <a name="see-also"></a>Vea también  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [Diseñador de la cinta](../vsto/ribbon-designer.md)   
 [XML de la cinta](../vsto/ribbon-xml.md)  
  
  