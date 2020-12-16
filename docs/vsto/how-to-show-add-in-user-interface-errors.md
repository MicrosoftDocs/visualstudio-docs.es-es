---
title: 'Cómo: Mostrar errores de la interfaz de usuario de complementos'
description: Obtenga información sobre cómo puede usar Visual Studio para mostrar mediante programación errores de la interfaz de usuario del complemento de VTSO en aplicaciones Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e74d60fe6386575417114fe1ad4823704cf09d46
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528127"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Cómo: Mostrar errores de la interfaz de usuario de complementos
  De forma predeterminada, si un complemento de VSTO intenta manipular la interfaz de usuario Microsoft Office (UI) y se produce un error, no se muestra ningún mensaje de error. Sin embargo, puede configurar las aplicaciones de Microsoft Office para mostrar los mensajes de errores relacionados con la interfaz de usuario. Puede usar estos mensajes para ayudar a determinar por qué no aparece una cinta personalizada, o por qué aparece una cinta pero no aparece ningún control.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>Cómo mostrar errores de la interfaz de usuario

1. Inicie la aplicación.

2. Haga clic en la pestaña **Archivo** .

3. Haga clic en **Opciones**.

4. En el panel de categorías, haga clic en **Opciones avanzadas**.

5. En el panel de detalles, seleccione **Mostrar errores de interfaz de usuario de complemento de VSTO** y luego haga clic en **Aceptar**.

    > [!NOTE]
    > Para Outlook, la casilla **Mostrar errores de interfaz de usuario de complemento de VSTO** se encuentra en la sección **Desarrollador** del panel de detalles. Para otras aplicaciones, la casilla se encuentra en la sección **General** del panel de detalles.

## <a name="see-also"></a>Consulte también
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)
- [Información general sobre la cinta](../vsto/ribbon-overview.md)
- [Información general del panel de acciones](../vsto/actions-pane-overview.md)
