---
title: Personalizar una cinta de opciones para Outlook
description: Aprenda que al personalizar la cinta de opciones Microsoft Office Outlook, debe tener en cuenta dónde aparecerá la cinta de opciones personalizada en la aplicación.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: df28de0f8a9497fabecff816c26db7593bf349bd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828064"
---
# <a name="customize-a-ribbon-for-outlook"></a>Personalización de una cinta de opciones para Outlook
  Al personalizar la cinta en Microsoft Office Outlook, debe tener en cuenta dónde aparecerá la cinta personalizada en la aplicación. Outlook muestra la cinta en la interfaz de usuario (UI) de la aplicación principal y en las ventanas que se abren cuando los usuarios realizan ciertas tareas, como crear mensajes de correo electrónico. Estas ventanas de la aplicación se denominan inspectores.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Agregar una cinta de opciones personalizada a la interfaz de usuario principal de la aplicación
 La interfaz de usuario de la aplicación principal en Outlook se denomina Explorador. Si usa el elemento Cinta **de opciones (Diseñador visual),** puede agregar una cinta al Explorador  haciendo clic en la propiedad **RibbonType** de la cinta de opciones en la ventana Propiedades y, a continuación, **seleccionando Microsoft.Outlook.Explorer**.

## <a name="assign-a-ribbon-to-an-inspector"></a>Asignación de una cinta de opciones a un inspector
 Para identificar el inspector que desea personalizar, debe especificar el tipo de cinta que corresponde a la clase de mensaje del Inspector.

 Si usa el elemento **Cinta de opciones (Diseñador visual),** haga  clic en la propiedad **RibbonType** de la cinta de opciones en la ventana Propiedades y, a continuación, seleccione uno o varios iDs de la cinta de opciones de la lista de valores.

 Puede agregar más de una cinta a un proyecto. Si más de una cinta comparte el mismo identificador de cinta, reemplace el método `CreateRibbonExtensibilityObject` de la clase `ThisAddin` de su proyecto para especificar qué cinta se mostrará en tiempo de ejecución. Para obtener más información, vea Información general [de la cinta de opciones.](../vsto/ribbon-overview.md) Para obtener más información sobre cada tipo de cinta de opciones, vea el artículo técnico [Personalización de la cinta de opciones en Outlook 2007.](/previous-versions/office/developer/office-2007/bb226712(v=office.12))

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Especificar el tipo de cinta de opciones mediante XML de cinta
 Si usa el elemento **Ribbon (XML),** compruebe el valor del parámetro *ribbonID* en el método y <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> devuelva la cinta de opciones adecuada.

 Visual Studio genera automáticamente el método <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> en el archivo de código de la cinta. El *parámetro ribbonID* es una cadena que identifica el Explorador o un tipo específico de inspector. Para obtener una lista completa de los posibles valores del parámetro *ribbonID,* consulte el artículo técnico Personalización de la cinta [de opciones en Outlook 2007.](/previous-versions/office/developer/office-2007/bb226712(v=office.12))

 En el siguiente ejemplo de código se indica cómo mostrar una cinta personalizada únicamente en el inspector `Microsoft.Outlook.Mail.Compose`. Este es el inspector que se abre cuando un usuario crea un nuevo mensaje de correo electrónico. La cinta de opciones que se va a mostrar se especifica en `GetResourceText()` el método , que se genera en la clase **Ribbon.** Para obtener más información sobre la **clase Ribbon,** vea [RIBBON XML](../vsto/ribbon-xml.md).

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb" id="Snippet1":::

## <a name="see-also"></a>Consulte también
- [Acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
- [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)
- [Diseñador de cinta de opciones](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
