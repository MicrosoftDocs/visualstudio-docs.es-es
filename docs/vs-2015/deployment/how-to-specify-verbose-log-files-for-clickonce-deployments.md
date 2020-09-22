---
title: 'Cómo: especificar archivos de registro detallados para implementaciones ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 78fa278952004348e035a675a1e159b2164285b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843243"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Cómo: Especificar archivos de registro detallados para las implementaciones ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] mantiene los archivos de registro de actividad de todas las implementaciones. Estos registros documentan los detalles relativos a la instalación, la inicialización, la actualización y la desinstalación de una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementación. Para aumentar el detalle que [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] escribe en estos archivos de registro, use el editor del registro (**regedit.exe**) para especificar el nivel de detalle.  
  
> [!CAUTION]
> Si utiliza el editor del registro incorrectamente, puede provocar problemas graves que pueden requerir la reinstalación del sistema operativo. Use el Editor del Registro bajo su propia responsabilidad.  
  
 En el procedimiento siguiente se describe cómo especificar el nivel de detalle de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] los archivos de registro para el usuario actual. Para reducir el nivel de detalle, quite este valor del registro.  
  
### <a name="to-specify-verbose-log-files"></a>Para especificar archivos de registro detallados  
  
1. Abra **Regedit.exe**.  
  
2. Navegue hasta el nodo `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .  
  
3. Si es necesario, cree un nuevo valor de cadena denominado `LogVerbosityLevel` .  
  
4. Establezca el valor `LogVerbosityLevel` en `1`.  
  
## <a name="see-also"></a>Consulte también  
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
