---
title: Cómo cambiar la posición de una pestaña en la cinta de opciones
description: Puede cambiar el orden de las pestañas personalizadas en una cinta de opciones y colocar las pestañas personalizadas antes o después de una pestaña integrada en la cinta de opciones mediante el editor de la colección de pestañas.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: dc0b4548ffa4e5efa75734b5528a7021cf122bfa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921923"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Cómo cambiar la posición de una pestaña en la cinta de opciones
  Puede cambiar el orden de las pestañas personalizadas en una cinta de opciones mediante el editor de la **colección de pestañas**. Puede colocar las pestañas personalizadas antes o después de una pestaña integrada en la cinta de opciones. Una pestaña integrada es una pestaña que ya está en la cinta de opciones de una aplicación Microsoft Office. Por ejemplo, la pestaña **datos** es una pestaña integrada en Excel.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Para cambiar el orden de las pestañas en la cinta de opciones

1. Seleccione el archivo de código de la cinta de opciones (archivo *. VB* o *. cs* ) en **Explorador de soluciones**.

2. En el menú **Ver** , haga clic en **Diseñador**.

3. Haga clic con el botón secundario en el diseñador de la cinta y, a continuación, haga clic en **propiedades**.

4. En la ventana **propiedades** , seleccione la propiedad **Tabs** y, a continuación, haga clic en el botón de puntos suspensivos (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")).

     Aparece el editor de la **colección de pestañas** .

5. En el **Editor de la colección de pestañas**, en la lista **miembros** , seleccione la pestaña que desea desplace y haga clic en las flechas arriba o abajo para cambiar el orden de tabulación.

### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Para colocar una tabulación antes o después de una pestaña integrada en la cinta de opciones

1. En el diseñador de la cinta de opciones, seleccione una pestaña personalizada.

2. En la ventana **propiedades** , expanda la propiedad **ControlID** y, a continuación, asegúrese de que el valor de la propiedad **ControlIdType** está establecido en **Custom**.

3. En la ventana **propiedades** , expanda la propiedad **posición** .

4. Establezca la propiedad **PositionType** en el valor adecuado:

    - **BeforeOfficeId** coloca el grupo antes de una pestaña integrada especificada.

    - **AfterOfficeId** coloca el grupo después de una pestaña integrada especificada.

5. Establezca la propiedad **OfficeId** en el identificador de control de una pestaña integrada.

     Para obtener una lista de identificadores de control, consulte [archivos de ayuda de office 2010: identificadores de control de la interfaz de usuario de Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

## <a name="see-also"></a>Vea también
- [Información general sobre la cinta](../vsto/ribbon-overview.md)
- [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Tutorial: crear una pestaña personalizada mediante el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Tutorial: crear una pestaña personalizada usando XML de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
