---
title: 'Cómo: habilitar la configuración de seguridad de ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: f89db12596754630eddaf78b9429eb2983625481
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599858"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Cómo: Habilitar la configuración de seguridad para aplicaciones ClickOnce
Debe estar habilitada la seguridad de acceso del código para aplicaciones ClickOnce para publicar la aplicación. Esto se realiza automáticamente al publicar una aplicación mediante el Asistente para publicación.

 En algunos casos, habilitar la seguridad de acceso del código puede afectar al rendimiento cuando se compila o depurar la aplicación; en estos casos, es posible que desea deshabilitar temporalmente la configuración de seguridad.

 Configuración de seguridad de ClickOnce puede habilitarse o deshabilitarse en el **seguridad** página de la **Diseñador de proyectos**.

### <a name="to-enable-clickonce-security-settings"></a>Para habilitar a la configuración de seguridad de ClickOnce

1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.

2.  Haga clic en la pestaña **Seguridad** .

3.  Active la casilla **Habilitar configuración de seguridad de ClickOnce** .

     Ahora puede personalizar la configuración de seguridad de la aplicación en la página de seguridad.

    > [!NOTE]
    >  Esta casilla se activa automáticamente cada vez que se publica la aplicación con el **publicar** asistente.

### <a name="to-disable-clickonce-security-settings"></a>Para deshabilitar la configuración de seguridad de ClickOnce

1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.

2.  Haga clic en la pestaña **Seguridad** .

3.  Desactive el **Enable ClickOnce Security Settings** casilla de verificación.

     La aplicación se ejecutará con la configuración de seguridad de plena confianza; cualquier configuración de la **seguridad** se omitirá la página.

    > [!NOTE]
    >  Cada vez que se publica la aplicación con el Asistente para publicación, se seleccionará esta casilla de verificación; debe desactivarla nuevo después de cada publicación correcta.

## <a name="see-also"></a>Vea también
- [Proteger aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)
- [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
