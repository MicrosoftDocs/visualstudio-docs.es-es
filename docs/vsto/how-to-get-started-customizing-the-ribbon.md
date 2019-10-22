---
title: Procedimiento Introducción a la personalización de la cinta de opciones
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, adding Ribbon to project
- Ribbon [Office development in Visual Studio], adding
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, adding Ribbon to project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a9b0f1ef704f5dd1426374e23806e5950ed5f6bb
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255863"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Procedimiento Introducción a la personalización de la cinta de opciones
  Para personalizar la cinta de opciones de una aplicación Microsoft Office, agregue un elemento **cinta (diseñador visual)** o **cinta (XML)** a un proyecto de Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Para agregar una cinta a un proyecto

1. En el menú **proyecto** , haga clic en **Agregar nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **cinta (diseñador visual)** o **cinta (XML)** . Para obtener más información acerca de estas plantillas, consulte [información general de la cinta](../vsto/ribbon-overview.md)de opciones.

3. En el cuadro **nombre** , escriba un nombre para el elemento de la cinta de opciones.

    Los nombres no pueden contener los caracteres siguientes:

   - Almohadilla (#)

   - Porcentaje (%)

   - Y comercial (&)

   - Asterisco (*)

   - Barra vertical (|)

   - Barra diagonal inversa (\\)

   - Dos puntos (:)

   - Comillas dobles (")

   - Menor que (\<)

   - Mayor que (>)

   - Signo de interrogación (?)

   - Barra diagonal (/)

   - Espacios iniciales o finales (' ')

   - Nombres reservados para Windows o DOS como ("NUL", "AUX", "con", "COM1", "LPT1", etc.)

4. Haga clic en **Aceptar**.

   El elemento de la cinta de opciones aparece en **Explorador de soluciones**. Para obtener información sobre los pasos siguientes, consulte [información general](../vsto/ribbon-overview.md)de la cinta de opciones.

## <a name="see-also"></a>Vea también
- [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
- [Diseñador de la cinta](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Tutorial: Crear una pestaña personalizada mediante el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Tutorial: Crear una pestaña personalizada usando XML de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
