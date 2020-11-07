---
title: Habilitar la configuración de seguridad de ClickOnce | Microsoft Docs
description: Obtenga información sobre cómo el Asistente para publicación habilita automáticamente la seguridad de acceso del código para que las aplicaciones ClickOnce publiquen la aplicación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db31d0182c598b32933cf2d4260706a2252a9b6f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351172"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Cómo: Habilitar la configuración de seguridad para aplicaciones ClickOnce
La seguridad de acceso del código de las aplicaciones ClickOnce debe estar habilitada para poder publicar la aplicación. Esto se hace automáticamente al publicar una aplicación mediante el Asistente para publicación.

 En algunos casos, la habilitación de la seguridad de acceso del código puede afectar al rendimiento al compilar o depurar la aplicación; en estos casos, puede que desee deshabilitar temporalmente la configuración de seguridad.

 La configuración de seguridad de ClickOnce puede habilitarse o deshabilitarse en la página **seguridad** del **Diseñador de proyectos**.

### <a name="to-enable-clickonce-security-settings"></a>Para habilitar la configuración de seguridad de ClickOnce

1. Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Security** (Seguridad).

3. Active la casilla **Habilitar configuración de seguridad de ClickOnce** .

     Ahora puede personalizar la configuración de seguridad de la aplicación en la página seguridad.

    > [!NOTE]
    > Esta casilla se selecciona automáticamente cada vez que se publica la aplicación con el Asistente para **publicación** .

### <a name="to-disable-clickonce-security-settings"></a>Para deshabilitar la configuración de seguridad de ClickOnce

1. Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Security** (Seguridad).

3. Desactive la casilla **Habilitar la configuración de seguridad de ClickOnce** .

     La aplicación se ejecutará con la configuración de seguridad de plena confianza; se omitirá cualquier configuración de la página **seguridad** .

    > [!NOTE]
    > Cada vez que se publica la aplicación con el Asistente para publicación, esta casilla se activará; debe borrarlo de nuevo después de cada publicación correcta.

## <a name="see-also"></a>Vea también
- [Protección de las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)
- [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
