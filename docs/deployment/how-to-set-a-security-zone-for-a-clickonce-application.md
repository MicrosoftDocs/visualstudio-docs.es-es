---
title: 'Cómo: establecer una zona de seguridad para una aplicación ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b2155cb36a2538bd93c48ccda1f2c93b0876b95
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077732"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Cómo: establecer una zona de seguridad para una aplicación ClickOnce
Al establecer permisos de seguridad de acceso del código para una aplicación ClickOnce, debe empezar con un conjunto básico de permisos en la página **Seguridad** del **Diseñador de proyectos**.  
  
 En la mayoría de los casos también puede elegir la zona **Internet** , que contiene un conjunto limitado de permisos, o la zona **Intranet local** , que contiene un conjunto de permisos más grande. Si la aplicación necesita permisos personalizados, puede hacerlo eligiendo la zona de seguridad **Personalizada** . Para obtener más información sobre cómo establecer permisos personalizados, consulte [Cómo: Establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
### <a name="to-set-a-security-zone"></a>Para establecer una zona de seguridad  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en la pestaña **Seguridad** .  
  
3.  Active la casilla **Habilitar configuración de seguridad de ClickOnce** .  
  
4.  Seleccione el botón de la opción **Aplicación de confianza parcial** .  
  
     Los controles de la sección **Permisos de seguridad de ClickOnce** están habilitados.  
  
5.  En la lista desplegable **Zona desde la que se instalará la aplicación** , seleccione una zona de seguridad.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
