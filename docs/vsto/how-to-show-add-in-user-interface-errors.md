---
title: "Cómo: Mostrar errores de interfaz de usuario | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
ms.assetid: aa82cc04-e616-4501-940c-79d11fb393cc
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3b483889dbd970b2225c773e6dd43b9333b0d8a5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Cómo: Mostrar errores de la interfaz de usuario
  De forma predeterminada, si un complemento de VSTO intenta manipular la interfaz de usuario (IU) de Microsoft Office y no lo consigue, no se muestra ningún mensaje de error. Sin embargo, puede configurar las aplicaciones de Microsoft Office para mostrar los mensajes de errores relacionados con la interfaz de usuario. Puede usar estos mensajes para ayudar a determinar por qué no aparece una cinta personalizada, o por qué aparece una cinta pero ningún control.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-show-vsto-add-in-user-interface-errors"></a>Cómo mostrar errores de la interfaz de usuario  
  
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
 [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)  
  
  