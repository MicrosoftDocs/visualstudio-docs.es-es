---
title: 'Cómo: especificar archivos de registro detallados para las implementaciones de ClickOnce | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8153625ec875cb54b0fc7b626d0cef61df2e9b71
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31557988"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Cómo: Especificar archivos de registro detallados para las implementaciones ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mantiene los archivos de registro de actividad para todas las implementaciones. Estos registros documentan los detalles relativos a la instalación, inicializar, actualizar y desinstalar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación. Para aumentar el detalle que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] operaciones de escritura en estos archivos de registro, use el Editor del registro (**regedit.exe**) para especificar el nivel de detalle.  
  
> [!CAUTION]
>  Si utiliza incorrectamente el Editor del registro, puede provocar problemas graves que quizás requieran reinstalar el sistema operativo. Use el Editor del Registro bajo su propia responsabilidad.  
  
 El siguiente procedimiento describe cómo especificar el nivel de detalle para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivos de registro para el usuario actual. Para reducir el nivel de detalle, quite este valor del registro.  
  
### <a name="to-specify-verbose-log-files"></a>Para especificar archivos de registro detallados  
  
1.  Abra **Regedit.exe**.  
  
2.  Desplácese hasta el nodo `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Si es necesario, cree un nuevo valor de cadena denominado `LogVerbosityLevel`.  
  
4.  Establecer el `LogVerbosityLevel` valor a `1`.  
  
## <a name="see-also"></a>Vea también  
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)