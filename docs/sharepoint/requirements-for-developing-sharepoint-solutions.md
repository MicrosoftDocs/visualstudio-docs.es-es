---
title: Requisitos para desarrollar soluciones de SharePoint | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, prerequisites
- SharePoint development in Visual Studio, requirements
ms.assetid: ae8ff69d-4540-4380-ab0b-845f7108e89c
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a32ceee7609fca96f27388839415ec5ac4d219de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="requirements-for-developing-sharepoint-solutions"></a>Requisitos para desarrollar soluciones de SharePoint
  Debe instalar en el sistema los requisitos previos siguientes para poder utilizar las herramientas de desarrollo de las soluciones de SharePoint incluidas en Visual Studio:  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]o una edición de Visual Studio Application Lifecycle Management (ALM).  
  
    -   La característica [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] o [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], o ambas, cuando instale [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]instalado en 64 bits [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] o de 64 bits [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.  
  
     o  
  
-   [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]instalado en 64 bits [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] o de 64 bits [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.  
  
> [!NOTE]  
>  Mientras que oficialmente solo los sistemas operativos de servidor son compatibles con SharePoint, también se permiten dos sistemas operativos cliente: [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] y [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] SP1. Para obtener más información, consulte [Guía de instalación de la estación de trabajo de desarrollador de SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkID=164557).  
  
 Los tipos de proyecto Modelo de conectividad a datos profesionales (BDC) requieren que [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] se instale en el sistema.  
  
 Para desarrollar las soluciones de SharePoint en Visual Studio, debe instalar SharePoint en el mismo equipo que Visual Studio. Asimismo, las herramientas de desarrollo de SharePoint admiten solo una configuración independiente de SharePoint; no admiten una configuración de granja (remota) de servidores.  
  
> [!NOTE]  
>  Los proyectos de SharePoint en Visual Studio admiten únicamente [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]. Si selecciona [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)] para un nuevo proyecto de SharePoint, su destino seguirá siendo [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].  
  
 Para obtener más información sobre cómo instalar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], consulte [instalar Visual Studio](../install/install-visual-studio.md).  
  
## <a name="vista-and-windows-7-user-account-control-uac"></a>Control de cuentas de usuario (UAC) de Windows Vista y Windows 7  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]y [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporan una característica de seguridad que se conoce como Control de cuentas de usuario (UAC). Para poder desarrollar soluciones de SharePoint mediante [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en sistemas [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] y [!INCLUDE[win7](../sharepoint/includes/win7-md.md)], UAC requiere que se ejecute [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] como administrador del sistema. En el escritorio, abra el menú contextual para [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]y, a continuación, elija **ejecutar como administrador**.  
  
 Para configurar el acceso directo del escritorio para siempre se ejecute como administrador, abra el menú contextual, elija **propiedades**, elija la **avanzadas** y, a continuación, seleccione la **ejecutar como administrador**  casilla de verificación.  
  
 Para obtener más información, consulte [descripción y configuración de Control de cuentas de usuario en Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). y [Control de cuentas de usuario de Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## <a name="sharepoint-permissions-considerations"></a>Consideraciones sobre los permisos de SharePoint  
 Para desarrollar las soluciones de SharePoint, debe tener los permisos necesarios para ejecutar y depurar soluciones de SharePoint. Antes de probar una solución de SharePoint, dé los pasos siguientes para asegurarse de que tiene los permisos necesarios:  
  
1.  Agregue su cuenta de usuario como administrador del sistema.  
  
2.  Agregue su cuenta de usuario como administrador del conjunto de servidores en el servidor de SharePoint.  
  
    1.  En Administración Central de SharePoint, elija el **administrar el grupo de administradores de la granja de servidores** vínculo.  
  
    2.  En el **administradores de la granja** página, elija la **New** botón.  
  
3.  Agregue su cuenta de usuario al grupo WSS_ADMIN_WPG.  
  
## <a name="see-also"></a>Vea también  
 [Introducción a &#40; Desarrollo de SharePoint en Visual Studio &#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)  
  
  