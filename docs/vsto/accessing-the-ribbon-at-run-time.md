---
title: Acceso a la cinta de opciones en tiempo de ejecución
description: Puede escribir código para mostrar, ocultar y modificar la cinta de opciones y permitir a los usuarios ejecutar el código desde los controles de un panel de tareas personalizado, un panel de acciones o un área del formulario de Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e20c9a54d2fa352c51d5ae5383f5c5b7861e0fdf
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825230"
---
# <a name="access-the-ribbon-at-run-time"></a>Acceso a la cinta de opciones en tiempo de ejecución
  Puede escribir código para mostrar, ocultar y modificar la cinta de opciones y permitir a los usuarios ejecutar el código desde los controles de un panel de tareas personalizado, un panel de acciones o un área del formulario de Outlook.

 Puede acceder a la cinta de opciones mediante la clase `Globals`. Para los proyectos de Outlook, puede acceder a las cintas de opciones que aparecen en una ventana específica del Inspector de Outlook o del Explorador de Outlook.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="access-the-ribbon-by-using-the-globals-class"></a>Acceso a la cinta de opciones mediante la clase Globals
 Puede usar la clase `Globals` para acceder a la cinta de opciones de un proyecto de nivel de documento o un proyecto de complemento de VSTO desde cualquier lugar del proyecto.

 Para obtener más información sobre la `Globals` clase , vea Acceso global a objetos en proyectos de [Office.](../vsto/global-access-to-objects-in-office-projects.md)

 En el ejemplo siguiente se usa la clase `Globals` para acceder a una cinta personalizada llamada `Ribbon1` y establecer el texto que aparece en un cuadro combinado de la cinta de opciones para `Hello World`.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet4":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet4":::

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Acceso a una colección de cintas de opciones que aparecen en una ventana específica de Outlook Inspector
 Puede acceder a una colección de cintas de opciones que aparecen en *Inspectores de* Outlook. Un Inspector es una ventana que se abre en Outlook cuando los usuarios realizan ciertas tareas, como crear mensajes de correo electrónico. Para acceder a la cinta de opciones de una ventana del Inspector, llame a la propiedad `Ribbons` de la clase `Globals` y pase un objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> que representa el Inspector.

 En el ejemplo siguiente se obtiene la colección de la cinta de opciones del Inspector que actualmente tiene el foco. A continuación, se accede a una cinta de opciones llamada `Ribbon1` y se establece el texto que aparece en un cuadro combinado de la cinta de opciones para `Hello World`.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet5":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet5":::

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Acceso a una colección de cintas de opciones que aparecen para un Explorador de Outlook específico
 Puede acceder a una colección de cintas de opciones que aparecen en un Explorador *de* Outlook. Un explorador es la interfaz de usuario (UI) de la aplicación principal de una instancia de Outlook. Para acceder a la cinta de opciones de una ventana del Explorador, llame a la propiedad `Ribbons` de la clase `Globals` y pase un objeto <xref:Microsoft.Office.Interop.Outlook.Explorer> que representa el Explorador.

 En el ejemplo siguiente se obtiene la colección de la cinta de opciones del Explorador que actualmente tiene el foco. A continuación, se accede a una cinta de opciones llamada `Ribbon1` y se establece el texto que aparece en un cuadro combinado de la cinta de opciones para `Hello World`.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet6":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet6":::

## <a name="see-also"></a>Consulte también
- [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)
- [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Información general sobre el modelo de objetos de la cinta de opciones](../vsto/ribbon-object-model-overview.md)
- [Tutorial: Crear una pestaña personalizada mediante el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Tutorial: Actualización de los controles de una cinta de opciones en tiempo de ejecución](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)
