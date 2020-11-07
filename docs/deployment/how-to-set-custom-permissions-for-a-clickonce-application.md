---
title: Establecer permisos personalizados (aplicación ClickOnce)
description: Obtenga información sobre cómo implementar una aplicación ClickOnce que use los permisos predeterminados o crear una zona personalizada para los permisos específicos que la aplicación necesita.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5d0348b882a3327c02fca6db0628822c0deffeb
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351003"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Procedimientos para establecer permisos personalizados para una aplicación ClickOnce
Puede implementar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que use los permisos predeterminados de las zonas de Internet o de la intranet local. Como alternativa, puede crear una zona personalizada para los permisos específicos necesarios para la aplicación. Para ello, personalice los permisos de seguridad en la página **Seguridad** del **Diseñador de proyectos**.

### <a name="to-customize-a-permission"></a>Para personalizar un permiso

1. Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Security** (Seguridad).

3. Active la casilla **Habilitar configuración de seguridad de ClickOnce** .

4. Seleccione el botón de la opción **Aplicación de confianza parcial** .

     Los controles de la sección **Permisos de seguridad de ClickOnce** están habilitados.

5. En la lista desplegable **Zona desde la que se instalará la aplicación** , haga clic en **(Personalizada)**.

6. Haga clic en **Editar XML de permisos**.

     El archivo *app. manifest* se abre en el editor XML.

7. Antes del elemento `</applicationRequestMinimum>` , agregue el código XML de los permisos necesarios para la aplicación.

    > [!NOTE]
    > Puede usar el método `ToXml` de un conjunto de permisos para generar el código XML del manifiesto de la aplicación. Por ejemplo, para generar el XML del conjunto de permisos <xref:System.Security.Permissions.EnvironmentPermission> , llame al método <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> .

## <a name="see-also"></a>Vea también
- [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)
- [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
