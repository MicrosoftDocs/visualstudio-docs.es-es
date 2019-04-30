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
ms.openlocfilehash: f164a8f1d1c84725530e7a3afab5e63472ae257e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967903"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Procedimiento Introducción a la personalización de la cinta de opciones
  Para personalizar la cinta de opciones de una aplicación de Microsoft Office, agregue un **cinta (diseñador Visual)** o **cinta (XML)** a un proyecto de Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Para agregar una cinta de opciones a un proyecto

1. En el **proyecto** menú, haga clic en **Agregar nuevo elemento**.

2. En el **Agregar nuevo elemento** cuadro de diálogo, seleccione **cinta (diseñador Visual)** o **cinta (XML)**. Para obtener más información acerca de estas plantillas, consulte [información general de la cinta de opciones](../vsto/ribbon-overview.md).

3. En el **nombre** , escriba un nombre para el elemento de la cinta de opciones.

    Los nombres no pueden contener los caracteres siguientes:

   - Almohadilla (#)

   - Porcentaje (%)

   - "Y" comercial (&)

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

   - Nombres reservados para Windows o DOS como ("nul", "aux", "Configurar", "com1", "lpt1" etc.)

4. Haga clic en **Aceptar**.

   El elemento de la cinta de opciones aparece en **el Explorador de soluciones**. Para obtener información sobre los pasos siguientes, vea [información general de la cinta de opciones](../vsto/ribbon-overview.md).

## <a name="see-also"></a>Vea también
- [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
- [Diseñador de la cinta](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Tutorial: Crear una pestaña personalizada usando el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Tutorial: Crear una pestaña personalizada usando XML de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
