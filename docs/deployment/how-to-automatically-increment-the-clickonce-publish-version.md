---
title: Procedimiento Automáticamente incrementar la publicación de ClickOnce versión | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 174506e9ee88de385f5bbba6fe09276d9297f298
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937709"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Procedimiento Incremento automático de la versión de publicación de ClickOnce

Al publicar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, cambiar el `Publish Version` propiedad hace que la aplicación se publica como una actualización. De forma predeterminada, Visual Studio incrementa automáticamente el `Revision` número de la `Publish Version` cada vez publique la aplicación.

Puede deshabilitar este comportamiento en el **publicar** página de la **Diseñador de proyectos**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>Para deshabilitar incrementar automáticamente la versión de publicación

1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.

2.  Haga clic en la pestaña **Publicar**.

3.  En el **Publicar versión** sección, desactive la **incrementar revisión automáticamente con cada versión** casilla de verificación.

## <a name="see-also"></a>Vea también

- [Cómo: Establecimiento de la versión de publicación de ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)
- [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)