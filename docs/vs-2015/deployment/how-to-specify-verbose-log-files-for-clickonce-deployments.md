---
title: 'Cómo: especificar archivos de registro detallados para las implementaciones de ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: b30260267fca5b7de16316e84082fc3b464f7deb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575807"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Cómo: Especificar archivos de registro detallados para las implementaciones ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: especificar archivos de registro detallado para implementaciones con ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-verbose-log-files-for-clickonce-deployments).  
  
[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] mantiene los archivos de registro de actividad para todas las implementaciones. Estos registros documentan los detalles relativos a la instalación, inicializando, actualización y desinstalación de un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementación. Para aumentar el detalle que [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] escrituras en estos archivos de registro, use el Editor del registro (**regedit.exe**) para especificar el nivel de detalle.  
  
> [!CAUTION]
>  Si utiliza incorrectamente el Editor del registro, puede provocar problemas graves que quizás requieran reinstalar el sistema operativo. Use el Editor del Registro bajo su propia responsabilidad.  
  
 El siguiente procedimiento describe cómo especificar el nivel de detalle para [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] archivos de registro para el usuario actual. Para reducir el nivel de detalle, quite este valor del registro.  
  
### <a name="to-specify-verbose-log-files"></a>Para especificar archivos de registro detallados  
  
1.  Abra **Regedit.exe**.  
  
2.  Desplácese hasta el nodo `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Si es necesario, cree un nuevo valor de cadena denominado `LogVerbosityLevel`.  
  
4.  Establecer el `LogVerbosityLevel` valor `1`.  
  
## <a name="see-also"></a>Vea también  
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)



