---
title: "Requisitos para desarrollar soluciones de SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, requisitos previos"
  - "desarrollo de SharePoint en Visual Studio, requisitos"
ms.assetid: ae8ff69d-4540-4380-ab0b-845f7108e89c
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Requisitos para desarrollar soluciones de SharePoint
  Debe instalar en el sistema los requisitos previos siguientes para poder utilizar las herramientas de desarrollo de las soluciones de SharePoint incluidas en Visual Studio:  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] o una edición de Visual Studio Application Lifecycle Management \(ALM\).  
  
    -   La característica [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] o [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], o ambas, cuando instale [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] instalado en [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] de 64 bits o en [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2 de 64 bits.  
  
     \-O bien\-  
  
-   [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] instalado en [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] de 64 bits o en [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2 de 64 bits.  
  
> [!NOTE]  
>  Mientras que oficialmente solo los sistemas operativos de servidor son compatibles con SharePoint, también se permiten dos sistemas operativos cliente: [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] y [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] SP1.  Para obtener más información, vea [Configuración del entorno de desarrollo para SharePoint 2010 en Windows Vista, Windows 7 y Windows Server 2008](http://go.microsoft.com/fwlink/?LinkID=164557).  
  
 Los tipos de proyecto Modelo de conectividad a datos profesionales \(BDC\) requieren que [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] se instale en el sistema.  
  
 Para desarrollar las soluciones de SharePoint en Visual Studio, debe instalar SharePoint en el mismo equipo que Visual Studio.  Asimismo, las herramientas de desarrollo de SharePoint admiten solo una configuración independiente de SharePoint; no admiten una configuración de granja \(remota\) de servidores.  
  
> [!NOTE]  
>  Los proyectos de SharePoint en Visual Studio admiten únicamente [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].  Si selecciona [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)] para un nuevo proyecto de SharePoint, su destino seguirá siendo [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].  
  
 Para obtener más información sobre cómo instalar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vea [Instalar Visual Studio](../Topic/Installing%20Visual%20Studio.md).  
  
## Control de cuentas de usuario \(UAC\) de Windows Vista y Windows 7  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] y [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporan una característica de seguridad que se conoce como Control de cuentas de usuario \(UAC\).  Para poder desarrollar soluciones de SharePoint mediante [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en sistemas [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] y [!INCLUDE[win7](../sharepoint/includes/win7-md.md)], UAC requiere que se ejecute [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] como administrador del sistema.  En el escritorio, abra el menú contextual de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]y, a continuación, elija **Ejecutar como administrador**.  
  
 Para configurar el acceso directo del escritorio de forma que siempre se ejecute como administrador, abra su menú contextual **Propiedades**, elija el botón **Avanzadas** y, a continuación, active la casilla **Ejecutar como administrador**.  
  
 Para obtener más información, vea [Descripción y configuración del Control de cuentas de usuario en Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476) y [Control de cuentas de usuario de Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## Consideraciones sobre los permisos de SharePoint  
 Para desarrollar las soluciones de SharePoint, debe tener los permisos necesarios para ejecutar y depurar soluciones de SharePoint.  Antes de probar una solución de SharePoint, dé los pasos siguientes para asegurarse de que tiene los permisos necesarios:  
  
1.  Agregue su cuenta de usuario como administrador del sistema.  
  
2.  Agregue su cuenta de usuario como administrador del conjunto de servidores en el servidor de SharePoint.  
  
    1.  En Administración central de SharePoint, elija el vínculo **Administrar el grupo de administradores del conjunto de servidores**.  
  
    2.  En la página **Administradores del conjunto de servidores**, elija el botón **Nuevo**.  
  
3.  Agregue su cuenta de usuario al grupo WSS\_ADMIN\_WPG.  
  
## Vea también  
 [Getting Started &#40;SharePoint Development in Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)  
  
  