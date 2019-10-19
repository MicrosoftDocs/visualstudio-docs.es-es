---
title: Cuadro de diálogo Configuración de seguridad avanzada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
- vs.err.debug_in_zone_no_hostproc:11310
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 000c3c4e2996869e96fd0d6097b5bab8576936a7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651735"
---
# <a name="advanced-security-settings-dialog-box"></a>Cuadro de diálogo Configuración de seguridad avanzada
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Este cuadro de diálogo permite especificar la configuración de seguridad relacionada con la depuración en zona.

 Para acceder a este cuadro de diálogo, seleccione un nodo de proyecto en el **Explorador de soluciones** y después, en el menú **Proyecto**, haga clic en **Propiedades**. Cuando se muestre el **Diseñador de proyectos**, haga clic en la pestaña **Seguridad**. En la página **Seguridad**, seleccione **Habilitar configuración de seguridad de ClickOnce**, haga clic en **Aplicación de confianza parcial** y, después, haga clic en **Avanzado**.

## <a name="uielement-list"></a>Lista de UIElement
 **Depurar esta aplicación con el conjunto de permisos seleccionado** Si activa esta casilla, se usa durante la depuración el conjunto de permisos seleccionado en la página **Seguridad**. Esta opción se encuentra activada de forma predeterminada.

 Para que funcione la depuración en una zona de seguridad, esta opción debe estar habilitada. Además, debe estar habilitada la opción **Habilitar el proceso de hospedaje de Visual Studio** (disponible en la página **Depurar** del **Diseñador de proyectos**).

 Para los proyectos de aplicación de explorador web WPF, la opción **Depurar esta aplicación con el conjunto de permisos seleccionados** está activada y deshabilitada.

 **Conceder a la aplicación acceso al sitio de origen** Si activa esta casilla, la aplicación puede acceder al sitio web o recurso compartido de servidor en el que está publicada. Esta opción se encuentra activada de forma predeterminada.

 **Depurar esta aplicación como si se hubiera descargado de la siguiente dirección URL** Si necesita que la aplicación acceda al sitio web o recurso compartido de servidor correspondiente a la **Dirección URL de instalación** especificada en la página **Publicar**, escriba esa dirección URL aquí. Esta opción solo está disponible cuando está seleccionada la opción **Conceder a la aplicación acceso al sitio de origen**.

## <a name="see-also"></a>Otras referencias
 [Página Seguridad, Diseñador de proyectos](../../ide/reference/security-page-project-designer.md)
