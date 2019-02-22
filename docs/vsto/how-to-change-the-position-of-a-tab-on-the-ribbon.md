---
title: Filtrar Cambiar la posición de una pestaña en la cinta de opciones
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc628ffd37cd67c080bfd544c77d6189e6eca21a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641110"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Filtrar Cambiar la posición de una pestaña en la cinta de opciones
  Puede cambiar el orden de las pestañas personalizadas en una cinta de opciones mediante la **pestaña Editor de la colección**. Puede colocar las pestañas personalizadas antes o después de una pestaña integrada en la cinta de opciones. Una pestaña integrada es una ficha que ya está en la cinta de opciones de una aplicación de Microsoft Office. Por ejemplo, el **datos** ficha es una pestaña integrada en Excel.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Para cambiar el orden de las fichas de la cinta de opciones

1.  Seleccione el archivo de código de la cinta de opciones (*.vb* o *.cs* archivo) en **el Explorador de soluciones**.

2.  En el **vista** menú, haga clic en **diseñador**.

3.  Haga clic en el Diseñador de cinta y, a continuación, haga clic en **propiedades**.

4.  En el **propiedades** ventana, seleccione el **pestañas** propiedad y, a continuación, haga clic en el botón de puntos suspensivos (![elipse Diseñador de ASP.NET mobile](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Elipse del diseñador")).

     El **pestaña Editor de la colección** aparece.

5.  En el **pestaña Editor de la colección**, en el **miembros** lista, seleccione la ficha que desee mover y haga clic en arriba o hacia abajo las flechas para cambiar el orden de tabulación.

### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Para colocar una ficha antes o después de una pestaña integrada en la cinta de opciones

1.  En el Diseñador de cinta de opciones, seleccione una ficha personalizada.

2.  En el **propiedades** ventana, expanda el **ControlId** propiedad y, a continuación, asegúrese de que el valor de la **ControlIdType** propiedad está establecida en **personalizado**.

3.  En el **propiedades** ventana, expanda el **posición** propiedad.

4.  Establecer el **PositionType** propiedad en el valor adecuado:

    -   **BeforeOfficeId** coloca el grupo antes de una pestaña integrada especificada.

    -   **AfterOfficeId** coloca el grupo después de una pestaña integrada especificada.

5.  Establecer el **OfficeId** propiedad para el identificador de control de una pestaña integrada.

     Para obtener una lista de identificadores de control, vea [los archivos de Ayuda de Office 2010: Identificadores de control de interfaz de usuario fluent Office](http://go.microsoft.com/fwlink/?LinkID=181052).

## <a name="see-also"></a>Vea también
- [Información general de la cinta de opciones](../vsto/ribbon-overview.md)
- [Diseñador de la cinta](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Tutorial: Crear una pestaña personalizada usando el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Tutorial: Crear una pestaña personalizada usando XML de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
