---
title: 'Cómo: establecer permisos personalizados para una aplicación ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 27302c3b2b925e66ca4b30f858fc8a54362451a9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49219263"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Cómo: Establecer permisos personalizados para una aplicación ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede implementar una aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] que use los permisos predeterminados de las zonas de Internet o de la intranet local. Como alternativa, puede crear una zona personalizada para los permisos específicos necesarios para la aplicación. Para ello, personalice los permisos de seguridad en la página **Seguridad** del **Diseñador de proyectos**.  
  
### <a name="to-customize-a-permission"></a>Para personalizar un permiso  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en la pestaña **Seguridad** .  
  
3.  Active la casilla **Habilitar configuración de seguridad de ClickOnce** .  
  
4.  Seleccione el botón de la opción **Aplicación de confianza parcial** .  
  
     Los controles de la sección **Permisos de seguridad de ClickOnce** están habilitados.  
  
5.  En la lista desplegable **Zona desde la que se instalará la aplicación** , haga clic en **(Personalizada)**.  
  
6.  Haga clic en **Editar XML de permisos**.  
  
     El archivo app.manifest se abrirá en el Editor XML.  
  
7.  Antes del elemento `</applicationRequestMinimum>` , agregue el código XML de los permisos necesarios para la aplicación.  
  
    > [!NOTE]
    >  Puede usar el método `ToXml` de un conjunto de permisos para generar el código XML del manifiesto de la aplicación. Por ejemplo, para generar el XML del conjunto de permisos <xref:System.Security.Permissions.EnvironmentPermission> , llame al método <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> . Para obtener más información sobre la estructura del XML del conjunto de permisos, consulte [NIB: How to: Import a Permission Set by Using an XML File](http://msdn.microsoft.com/en-us/dea16b54-c108-408a-ac36-cdc05f746236)(NIB: Cómo importar un conjunto de permisos mediante un archivo XML).  
  
## <a name="see-also"></a>Vea también  
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)



