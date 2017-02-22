---
title: "C&#243;mo: Especificar archivos de registro detallados para las implementaciones ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implementación ClickOnce, registro"
  - "registros, implementación ClickOnce"
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Especificar archivos de registro detallados para las implementaciones ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mantiene los archivos de registro de actividades para todas las implementaciones.  Estos registros documentan los detalles relativos a la instalación, inicialización, actualización y desinstalación de una implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Si desea aumentar el nivel de detalle que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] escribe en estos archivos de registro, use el Editor del Registro \(**regedit.exe**\) para especificar dicho nivel.  
  
> [!CAUTION]
>  El uso incorrecto del Editor del Registro puede causar problemas graves que obliguen a reinstalar el sistema operativo.  Utilice el Editor del registro bajo su propia responsabilidad.  
  
 En el procedimiento siguiente se describe cómo especificar el nivel de detalle de los archivos de registro de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para el usuario actual.  Para reducir el nivel de detalle, quite este valor del Registro.  
  
### Para especificar los archivos de registro detallados  
  
1.  Abra **Regedit.exe**.  
  
2.  Navegue hasta el nodo `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Si es necesario, cree un nuevo valor de cadena denominado `LogVerbosityLevel`.  
  
4.  Establezca el valor de `LogVerbosityLevel` en `1`.  
  
## Vea también  
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)