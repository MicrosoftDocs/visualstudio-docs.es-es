---
title: "Cómo: habilitar la configuración de seguridad de ClickOnce | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: "8"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: d9fb07f8348e161743b373a83d49c4dd614d8c5f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-clickonce-security-settings"></a>Cómo: Habilitar la configuración de seguridad para aplicaciones ClickOnce
Seguridad de acceso del código para aplicaciones ClickOnce debe estar habilitado para publicar la aplicación. Esto se hace automáticamente cuando se publica una aplicación mediante el Asistente para publicación.  
  
 En algunos casos, habilitar la seguridad de acceso del código puede afectar al rendimiento al compilar o depurar la aplicación; en estos casos, puede que desee deshabilitar temporalmente la configuración de seguridad.  
  
 Configuración de seguridad de ClickOnce puede habilitarse o deshabilitarse en el **seguridad** página de la **Diseñador de proyectos**.  
  
### <a name="to-enable-clickonce-security-settings"></a>Para habilitar la configuración de seguridad de ClickOnce  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en la pestaña **Seguridad** .  
  
3.  Active la casilla **Habilitar configuración de seguridad de ClickOnce** .  
  
     Ahora puede personalizar la configuración de seguridad para la aplicación en la página seguridad.  
  
    > [!NOTE]
    >  Esta casilla de verificación se selecciona automáticamente cada vez que la aplicación se publica con el **publicar** asistente.  
  
### <a name="to-disable-clickonce-security-settings"></a>Para deshabilitar la configuración de seguridad de ClickOnce  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en la pestaña **Seguridad** .  
  
3.  Desactive el **habilitar la configuración de seguridad de ClickOnce** casilla de verificación.  
  
     La aplicación se ejecutará con la configuración de seguridad de plena confianza; cualquier configuración en el **seguridad** se pasará por alto de página.  
  
    > [!NOTE]
    >  Cada vez que la aplicación se publica con el Asistente para publicación, se seleccionará esta casilla de verificación; primero debe borrar nuevo después de cada publicación correcta.  
  
## <a name="see-also"></a>Vea también  
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 
