---
title: 'Cómo: Introducción a la personalización de la cinta de opciones'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: be311f87862f4447d903294508927735d3507b08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520073"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Cómo: Introducción a la personalización de la cinta de opciones
  Para personalizar la cinta de opciones de una aplicación Microsoft Office, agregue un elemento **cinta (diseñador visual)** o **cinta (XML)** a un proyecto de Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Para agregar una cinta a un proyecto

1. En el menú **proyecto** , haga clic en **Agregar nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **cinta (diseñador visual)** o **cinta (XML)**. Para obtener más información acerca de estas plantillas, consulte [información general de la cinta](../vsto/ribbon-overview.md)de opciones.

3. En el cuadro **nombre** , escriba un nombre para el elemento de la cinta de opciones.

    Los nombres no pueden contener los siguientes caracteres:

   - Número (#)

   - Porcentaje (%)

   - Símbolo de y comercial (&)

   - Asterisco (*)

   - Barra vertical (|)

   - Barra diagonal inversa (\\)

   - Dos puntos (:)

   - Comillas dobles (")

   - Menor que (\<)

   - Mayor que (>)

   - Signo de interrogación (?)

   - Barra diagonal (/)

   - Espacios iniciales y finales (' ')

   - Nombres reservados para Windows o DOS como ("NUL", "AUX", "con", "COM1", "LPT1", etc.)

4. Haga clic en **OK**.

   El elemento de la cinta de opciones aparece en **Explorador de soluciones**. Para obtener información sobre los pasos siguientes, consulte [información general](../vsto/ribbon-overview.md)de la cinta de opciones.

## <a name="see-also"></a>Consulte también
- [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
- [Diseñador de la cinta](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Tutorial: crear una pestaña personalizada mediante el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Tutorial: crear una pestaña personalizada usando XML de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
