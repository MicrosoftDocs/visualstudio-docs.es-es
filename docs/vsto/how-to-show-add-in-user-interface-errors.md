---
title: 'Cómo: agregar en Mostrar errores de interfaz de usuario'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dd6da0c83d0dee835169a0a8068af8d75facbbd4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674762"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Cómo: agregar en Mostrar errores de interfaz de usuario
  De forma predeterminada, si un complemento VSTO intenta manipular la interfaz de usuario (UI) de Microsoft Office y se produce un error, no se muestra ningún mensaje de error. Sin embargo, puede configurar las aplicaciones de Microsoft Office para mostrar los mensajes de errores relacionados con la interfaz de usuario. Puede utilizar estos mensajes para ayudar a determinar por qué no aparece una cinta personalizada, o por qué aparece una cinta pero ningún control.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="to-show-vsto-add-in-user-interface-errors"></a>Cómo mostrar errores de la interfaz de usuario  
  
1.  Inicie la aplicación.  
  
2.  Haga clic en la pestaña **Archivo** .  
  
3.  Haga clic en **Opciones**.  
  
4.  En el panel de categorías, haga clic en **Opciones avanzadas**.  
  
5.  En el panel de detalles, seleccione **Mostrar errores de interfaz de usuario de complemento de VSTO**y luego haga clic en **Aceptar**.  
  
    > [!NOTE]  
    >  Para Outlook, la casilla **Mostrar errores de interfaz de usuario de complemento de VSTO** se encuentra en la sección **Desarrollador** del panel de detalles. Para otras aplicaciones, la casilla se encuentra en la sección **General** del panel de detalles.  
  
## <a name="see-also"></a>Vea también  
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [Información general sobre el panel de acciones](../vsto/actions-pane-overview.md)  
  
  