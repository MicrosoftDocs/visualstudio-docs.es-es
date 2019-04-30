---
title: Procedimiento Mostrar errores de interfaz de usuario del complemento
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 78cc4d2e85e2f7a5347fe0c8927c855160fbb511
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441788"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Procedimiento Mostrar errores de interfaz de usuario del complemento
  De forma predeterminada, si un complemento VSTO intenta manipular la interfaz de usuario (UI) de Microsoft Office y se produce un error, no se muestra ningún mensaje de error. Sin embargo, puede configurar las aplicaciones de Microsoft Office para mostrar los mensajes de errores relacionados con la interfaz de usuario. Puede utilizar estos mensajes para ayudar a determinar por qué no aparece una cinta personalizada, o por qué aparece una cinta pero ningún control.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>Cómo mostrar errores de la interfaz de usuario

1. Inicie la aplicación.

2. Haga clic en la pestaña **Archivo** .

3. Haga clic en **Opciones**.

4. En el panel de categorías, haga clic en **Opciones avanzadas**.

5. En el panel de detalles, seleccione **Mostrar errores de interfaz de usuario de complemento de VSTO**y luego haga clic en **Aceptar**.

    > [!NOTE]
    > Para Outlook, la casilla **Mostrar errores de interfaz de usuario de complemento de VSTO** se encuentra en la sección **Desarrollador** del panel de detalles. Para otras aplicaciones, la casilla se encuentra en la sección **General** del panel de detalles.

## <a name="see-also"></a>Vea también
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)
- [Información general de la cinta de opciones](../vsto/ribbon-overview.md)
- [Información general sobre el panel de acciones](../vsto/actions-pane-overview.md)
