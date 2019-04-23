---
title: Procedimiento Especificar archivos de registro detallados para las implementaciones de ClickOnce | Documentos de Microsoft
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70c83c31ba8c415de9c2a7be8f60c9c6ee8ba9ac
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111537"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Procedimiento Especificación de archivos de registro detallados para implementaciones de ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mantiene los archivos de registro de actividad para todas las implementaciones. Estos registros documentan los detalles relativos a la instalación, inicializando, actualización y desinstalación de un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación. Para aumentar el detalle que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] escrituras en estos archivos de registro, use el Editor del registro (*regedit.exe*) para especificar el nivel de detalle.

> [!CAUTION]
>  Si utiliza incorrectamente el Editor del registro, puede provocar problemas graves que quizás requieran reinstalar el sistema operativo. Use el Editor del Registro bajo su propia responsabilidad.

 El siguiente procedimiento describe cómo especificar el nivel de detalle para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivos de registro para el usuario actual. Para reducir el nivel de detalle, quite este valor del registro.

### <a name="to-specify-verbose-log-files"></a>Para especificar archivos de registro detallados

1. Abra *Regedit.exe*.

2. Desplácese hasta el nodo **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment**.

3. Si es necesario, cree un nuevo valor de cadena denominado `LogVerbosityLevel`.

4. Establezca el valor `LogVerbosityLevel` en `1`.

## <a name="see-also"></a>Vea también
- [Solución de problemas de implementaciones de ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)