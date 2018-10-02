---
title: Página Seguridad, Diseñador de proyectos | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
ms.assetid: 641d9cd3-fa07-498a-8568-3c169bb4d3d5
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fb9047f0fb3ebf3eb582220ec91d08612b8b9bca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581996"
---
# <a name="security-page-project-designer"></a>Página Seguridad, Diseñador de proyectos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [seguridad Page, Project Designer](https://docs.microsoft.com/visualstudio/ide/reference/security-page-project-designer).  
  
  
La página **Seguridad** del **Diseñador de proyectos** se usa para configurar las opciones de seguridad de acceso del código para las aplicaciones que se implementan con la implementación de [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]. Para obtener más información, vea [Code Access Security for ClickOnce Applications](../../deployment/code-access-security-for-clickonce-applications.md) (Seguridad de acceso del código para aplicaciones ClickOnce).  
  
 Para obtener acceso a la página **Seguridad**, haga clic en un nodo de proyecto en el **Explorador de soluciones** y, después, en el menú **Proyecto**, haga clic en **Propiedades**. Cuando se muestre el **Diseñador de proyectos**, haga clic en la pestaña **Seguridad**.  
  
## <a name="security-settings"></a>Configuración de seguridad  
 **Habilitar la configuración de seguridad ClickOnce**  
 Determina si la configuración de seguridad está habilitada en tiempo de diseño. Cuando esta opción está desactivada, todas las demás opciones de la página **Seguridad** no están disponibles.  
  
> [!NOTE]
>  Al publicar una aplicación mediante el uso del asistente para **Publicar**, esta opción se habilita automáticamente.  
  
 Cuando se selecciona esta opción, puede elegir uno de dos botones de radio: **Aplicación de plena confianza** o **Aplicación de confianza parcial**.  
  
 De forma predeterminada, para los proyectos de aplicación de explorador web de WPF, esta opción está activada.  
  
 Para todos los demás tipos de proyecto, esta opción está desactivada de forma predeterminada.  
  
 **Aplicación de plena confianza**  
 Si selecciona esta opción, la aplicación solicita permisos de plena confianza cuando se instala o ejecuta en un equipo cliente. Evite usar la plena confianza si es posible, dado que se le concederá a la aplicación acceso sin restricciones a recursos como el sistema de archivos y el Registro.  
  
 De forma predeterminada, para los proyectos de aplicación de explorador web de WPF, esta opción está establecida en Confianza parcial.  
  
 Para todos los demás tipos de proyecto, esta opción está establecida en Plena confianza de forma predeterminada.  
  
 **Esta es una aplicación de confianza parcial**  
 Si selecciona esta opción, la aplicación solicita permisos de confianza parcial cuando se instala o ejecuta en un equipo cliente. *Confianza parcial* significa que solo se ejecutarán las acciones que están permitidas en los permisos solicitados de seguridad de acceso del código. Para obtener más información sobre cómo configurar los permisos de seguridad, vea [Code Access Security for ClickOnce Applications](../../deployment/code-access-security-for-clickonce-applications.md) (Seguridad de acceso del código para aplicaciones ClickOnce).  
  
 Puede especificar la configuración de seguridad de confianza parcial mediante las opciones del área **Permisos de seguridad de ClickOnce**.  
  
## <a name="clickonce-security-permissions"></a>Permisos de seguridad de ClickOnce  
 **Zona desde la que se instalará la aplicación**  
 Especifica un conjunto predeterminado de permisos de seguridad de acceso del código. Elija **Internet** o **Intranet local** para un conjunto de permisos restringidos o elija **(Personalizado)** para configurar un conjunto de permisos personalizado. Si la aplicación solicita más permisos de los concedidos en una zona, aparecerá un mensaje relativo a la confianza de ClickOnce para que el usuario final conceda los permisos adicionales. Para obtener más información sobre cómo configurar los permisos de seguridad, vea [Code Access Security for ClickOnce Applications](../../deployment/code-access-security-for-clickonce-applications.md) (Seguridad de acceso del código para aplicaciones ClickOnce).  
  
 De forma predeterminada, para los proyectos de aplicación de explorador web de WPF, esta opción está establecida en **Internet**.  
  
 **Editar XML de permisos**  
 Abre la plantilla de manifiesto de aplicación (app.manifest) para configurar los permisos del conjunto de permisos **(Personalizado)**.  
  
 **Avanzadas**  
 Abre el cuadro de diálogo [Configuración de seguridad avanzada](../../ide/reference/advanced-security-settings-dialog-box.md), que se usa para configurar las opciones de depuración de la aplicación con permisos restringidos. Estas configuraciones se comprueban durante la depuración, y las excepciones de los permisos indican que la aplicación puede necesitar más permisos de los definidos en una zona.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Security.Permissions.WebBrowserPermission>   
 <xref:System.Security.Permissions.MediaPermission>   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md)   
 [Cómo: Habilitar la configuración de seguridad de ClickOnce](../../deployment/how-to-enable-clickonce-security-settings.md)   
 [Cómo: Establecer una zona de seguridad para una aplicación ClickOnce](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Cómo: Establecer permisos personalizados para una aplicación ClickOnce](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Cómo: Depurar una aplicación ClickOnce con permisos restringidos](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Seguridad e implementación ClickOnce](../../deployment/clickonce-security-and-deployment.md)   
 [Referencia de propiedades del proyecto](../../ide/reference/project-properties-reference.md)   
 [Configuración de seguridad avanzada (Cuadro de diálogo)](../../ide/reference/advanced-security-settings-dialog-box.md)



