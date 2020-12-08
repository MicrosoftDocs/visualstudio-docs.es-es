---
title: Personalización de una cinta para Outlook
description: Sepa que al personalizar la cinta de opciones en Microsoft Office Outlook, debe tener en cuenta dónde aparecerá la cinta personalizada en la aplicación.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 25b4faa994a99bccdc2122ad6b9d124f7391e9f8
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848110"
---
# <a name="customize-a-ribbon-for-outlook"></a>Personalización de una cinta para Outlook
  Al personalizar la cinta en Microsoft Office Outlook, debe tener en cuenta dónde aparecerá la cinta personalizada en la aplicación. Outlook muestra la cinta en la interfaz de usuario (UI) de la aplicación principal y en las ventanas que se abren cuando los usuarios realizan ciertas tareas, como crear mensajes de correo electrónico. Estas ventanas de la aplicación se denominan inspectores.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Agregar una cinta de opciones personalizada a la interfaz de usuario de la aplicación principal
 La interfaz de usuario de la aplicación principal en Outlook se denomina Explorador. Si está utilizando el elemento **cinta (diseñador visual)** , puede Agregar una cinta de opciones al explorador haciendo clic en la propiedad **RibbonType** de la cinta de opciones en la ventana **propiedades** y, a continuación, seleccionando **Microsoft. Outlook. Explorer**.

## <a name="assign-a-ribbon-to-an-inspector"></a>Asignar una cinta de opciones a un inspector
 Para identificar el inspector que desea personalizar, debe especificar el tipo de cinta que corresponde a la clase de mensaje del Inspector.

 Si está utilizando el elemento **cinta (diseñador visual)** , haga clic en la propiedad **RibbonType** de la cinta de opciones en la ventana **propiedades** y, a continuación, seleccione uno o más identificadores de la cinta de opciones en la lista de valores.

 Puede agregar más de una cinta a un proyecto. Si más de una cinta comparte el mismo identificador de cinta, reemplace el método `CreateRibbonExtensibilityObject` de la clase `ThisAddin` de su proyecto para especificar qué cinta se mostrará en tiempo de ejecución. Para obtener más información, vea [información general sobre la cinta](../vsto/ribbon-overview.md)de opciones. Para obtener más información acerca de cada tipo de cinta, consulte el artículo técnico [personalizar la cinta de opciones en Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Especificar el tipo de cinta mediante el XML de la cinta
 Si está utilizando el elemento **cinta (XML)** , compruebe el valor del parámetro *ribbonID* en el <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> método y devuelva la cinta adecuada.

 Visual Studio genera automáticamente el método <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> en el archivo de código de la cinta. El parámetro *ribbonID* es una cadena que identifica el explorador o un tipo específico de inspector. Para obtener una lista completa de los valores posibles del parámetro *ribbonID* , consulte el artículo técnico [personalizar la cinta de opciones en Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

 En el siguiente ejemplo de código se indica cómo mostrar una cinta personalizada únicamente en el inspector `Microsoft.Outlook.Mail.Compose`. Este es el inspector que se abre cuando un usuario crea un nuevo mensaje de correo electrónico. La cinta de opciones que se va a mostrar se especifica en el `GetResourceText()` método, que se genera en la clase **Ribbon** . Para obtener más información acerca de la clase **Ribbon** , vea XML de la [cinta](../vsto/ribbon-xml.md)de opciones.

 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]

## <a name="see-also"></a>Vea también
- [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
- [Información general sobre la cinta](../vsto/ribbon-overview.md)
- [Diseñador de la cinta](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
