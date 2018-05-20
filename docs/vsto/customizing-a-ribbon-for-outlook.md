---
title: Personalizar una cinta de opciones para Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ef1c72d5c24c70a539b909e8d338a235ceb52a49
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="customize-a-ribbon-for-outlook"></a>Personalizar una cinta de opciones para Outlook
  Al personalizar la cinta en Microsoft Office Outlook, debe tener en cuenta dónde aparecerá la cinta personalizada en la aplicación. Outlook muestra la cinta en la interfaz de usuario (UI) de la aplicación principal y en las ventanas que se abren cuando los usuarios realizan ciertas tareas, como crear mensajes de correo electrónico. Estas ventanas de la aplicación se denominan inspectores.  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") para una demostración en vídeo relacionada, vea [How do i Use el Diseñador de la cinta de opciones para personalizar la cinta de opciones en Outlook?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Agregar una cinta de opciones personalizada al interfaz de usuario de la aplicación principal  
 La interfaz de usuario de la aplicación principal en Outlook se denomina Explorador. Si usas el **cinta (diseñador Visual)** producto, puede agregar una cinta de opciones al explorador haciendo clic en el **RibbonType** propiedad de la cinta de opciones en la **propiedades** ventana, y, a continuación, seleccione **Microsoft.Outlook.Explorer**.  
  
## <a name="assign-a-ribbon-to-an-inspector"></a>Asignar una cinta de opciones a un inspector  
 Para identificar el inspector que desea personalizar, debe especificar el tipo de cinta que corresponde a la clase de mensaje del Inspector.  
  
 Si usas el **cinta (diseñador Visual)** de elemento, haga clic en el **RibbonType** propiedad de la cinta de opciones en la **propiedades** ventana y, a continuación, seleccione uno o varios identificadores de la cinta de opciones la lista de valores.  
  
 Puede agregar más de una cinta a un proyecto. Si más de una cinta comparte el mismo identificador de cinta, reemplace el método `CreateRibbonExtensibilityObject` de la clase `ThisAddin` de su proyecto para especificar qué cinta se mostrará en tiempo de ejecución. Para obtener más información, consulte [información general de la cinta de opciones](../vsto/ribbon-overview.md). Para obtener más información acerca de cada tipo de cinta de opciones, consulte el artículo técnico [personalizar la cinta en Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Especificar el tipo de cinta de opciones mediante XML de la cinta de opciones  
 Si usas el **cinta (XML)** item, compruebe el valor de la *ribbonID* parámetro en el <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> método y devuelva la cinta adecuada.  
  
 Visual Studio genera automáticamente el método <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> en el archivo de código de la cinta. El *ribbonID* parámetro es una cadena que identifica el explorador o un tipo específico de inspector. Para obtener una lista completa de los valores posibles de la *ribbonID* parámetro, consulte el artículo técnico [personalizar la cinta en Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
 En el siguiente ejemplo de código se indica cómo mostrar una cinta personalizada únicamente en el inspector `Microsoft.Outlook.Mail.Compose`. Este es el inspector que se abre cuando un usuario crea un nuevo mensaje de correo electrónico. La cinta de opciones para mostrar se especifica en el `GetResourceText()` método, que se genera en el **cinta** clase. Para obtener más información sobre la **cinta** de clases, vea [XML de cinta de opciones](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]  
  
## <a name="see-also"></a>Vea también  
 [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [Diseñador de la cinta](../vsto/ribbon-designer.md)   
 [XML de la cinta](../vsto/ribbon-xml.md)  
  
  