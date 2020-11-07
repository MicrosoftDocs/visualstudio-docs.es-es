---
title: Establecimiento de la zona de seguridad (aplicación ClickOnce)
description: Obtenga información sobre cómo establecer permisos de seguridad de acceso del código para una aplicación ClickOnce, que comienza con un conjunto básico de permisos en el diseñador de proyectos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2e8b49f833b5dd91dc6379d2a015d41a9679afe
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349781"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Procedimientos para establecer una zona de seguridad para una aplicación ClickOnce
Al establecer permisos de seguridad de acceso del código para una aplicación ClickOnce, debe empezar con un conjunto básico de permisos en la página **Seguridad** del **Diseñador de proyectos**.

 En la mayoría de los casos también puede elegir la zona **Internet** , que contiene un conjunto limitado de permisos, o la zona **Intranet local** , que contiene un conjunto de permisos más grande. Si la aplicación necesita permisos personalizados, puede hacerlo eligiendo la zona de seguridad **Personalizada** . Para obtener más información sobre cómo establecer permisos personalizados, consulte [Cómo: Establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

### <a name="to-set-a-security-zone"></a>Para establecer una zona de seguridad

1. Con un proyecto seleccionado en **Explorador de soluciones** , en el menú **proyecto** , haga clic en **propiedades**.

2. Haga clic en la pestaña **Security** (Seguridad).

3. Active la casilla **Habilitar configuración de seguridad de ClickOnce** .

4. Seleccione el botón de la opción **Aplicación de confianza parcial** .

     Los controles de la sección **Permisos de seguridad de ClickOnce** están habilitados.

5. En la lista desplegable **Zona desde la que se instalará la aplicación** , seleccione una zona de seguridad.

## <a name="see-also"></a>Vea también
- [Cómo: establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Protección de las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)
- [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
