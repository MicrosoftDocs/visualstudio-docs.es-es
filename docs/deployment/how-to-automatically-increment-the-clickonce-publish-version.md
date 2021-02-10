---
title: Incrementar automáticamente la versión de publicación de ClickOnce
description: Obtenga información sobre cómo deshabilitar el incremento automático del número de revisión de la aplicación ClickOnce mediante Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84b0a8932bb9d8fd4738c2cd4924b61bb6faeb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947780"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Cómo: Incrementar automáticamente la versión de publicación de ClickOnce

Al publicar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, el cambio de la `Publish Version` propiedad hace que la aplicación se publique como una actualización. De forma predeterminada, Visual Studio incrementa automáticamente el `Revision` número de `Publish Version` cada vez que se publica la aplicación.

Puede deshabilitar este comportamiento en la página **publicar** del **Diseñador de proyectos**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>Para deshabilitar la incrementación automática de la versión de publicación

1. Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. En la sección **versión de publicación** , desactive la casilla **incrementar automáticamente la revisión con cada versión** .

## <a name="see-also"></a>Vea también

- [Cómo: establecer la versión de publicación de ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)
- [Publicación de aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)