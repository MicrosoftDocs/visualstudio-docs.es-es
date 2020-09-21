---
title: Especificar archivos de registro detallados (implementaciones ClickOnce)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 54c90f6a544607e78dd8f294bfc307bc87377b70
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808716"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Cómo: Especificar archivos de registro detallados para las implementaciones ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mantiene los archivos de registro de actividad de todas las implementaciones. Estos registros documentan los detalles relativos a la instalación, la inicialización, la actualización y la desinstalación de una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación. Para aumentar el detalle que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] escribe en estos archivos de registro, use el editor del registro (*regedit.exe*) para especificar el nivel de detalle.

> [!CAUTION]
> Si utiliza el editor del registro incorrectamente, puede provocar problemas graves que pueden requerir la reinstalación del sistema operativo. Use el Editor del Registro bajo su propia responsabilidad.

 En el procedimiento siguiente se describe cómo especificar el nivel de detalle de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] los archivos de registro para el usuario actual. Para reducir el nivel de detalle, quite este valor del registro.

### <a name="to-specify-verbose-log-files"></a>Para especificar archivos de registro detallados

1. Abra *Regedit.exe*.

2. Navegue hasta el nodo **HKEY_CURRENT_USER \software\classes\software\microsoft\windows\currentversion\deployment**.

3. Si es necesario, cree un nuevo valor de cadena denominado `LogVerbosityLevel` .

4. Establezca el valor `LogVerbosityLevel` en `1`.

## <a name="see-also"></a>Consulte también
- [Solución de problemas de implementaciones de ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)