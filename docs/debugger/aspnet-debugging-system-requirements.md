---
title: 'Depuración ASP.NET: Requisitos del sistema | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: d86b27a27884c0b8764c28a25ffb8ea9623efd9c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55025382"
---
# <a name="aspnet-debugging-system-requirements"></a>Depuración ASP.NET: Requisitos del sistema
En este tema se describen los requisitos de software y seguridad de los escenarios de depuración de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] :  
  
- Depuración local, en la que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y la aplicación web se ejecutan en el mismo equipo. Existen dos versiones de este escenario:  
  
  - El código de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] reside en el sistema de archivos.  
  
  - El código de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] reside en un sitio web de IIS.  
  
- La depuración remota, en la que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se ejecuta en un equipo cliente y depura una aplicación web que se está ejecutando en un equipo servidor remoto.  
  
## <a name="security-requirements"></a>Requisitos de seguridad  
 Para la depuración remota, los equipos locales y remotos deben estar en una configuración de dominio o una configuración de grupo de trabajo.  
  
 Para depurar el [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] el proceso de trabajo (hospedado por un grupo de aplicaciones), debe tener permiso para depurar dicho proceso. De forma predeterminada, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicaciones anteriores a IIS 6.0 se ejecutan como la **ASPNET** usuario. En IIS 6.0 e IIS 7.0, el **NETWORK SERVICE** cuenta es el valor predeterminado. Si el proceso de trabajo se ejecuta con la cuenta **ASPNET**o **NETWORK SERVICE**, deberá tener privilegios de administrador para depurarlo.

 > [!IMPORTANT]
 > A partir de Windows Server 2008 R2, se recomienda el uso de la [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) como identidad para cada grupo de aplicaciones.
  
 El nombre del proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] varía en función del escenario de depuración y de la versión de IIS. Para obtener más información, vea [Cómo: Búsqueda del nombre de un proceso de ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Puede cambiar la cuenta de usuario en la que se ejecuta el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] editando el archivo machine.config en el servidor que ejecuta IIS. La mejor manera de hacerlo es mediante el **Administrador de Internet Information Services (IIS)**. Para obtener más información, vea [Cómo: Ejecución de un proceso de trabajo en una cuenta de usuario](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Si cambia el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para que se ejecute en su propia cuenta de usuario, no tiene porqué ser administrador en el servidor que esté ejecutando IIS.  
  
> [!CAUTION]
>  Antes de cambiar el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para que se ejecute en una cuenta diferente, tenga en cuenta las posibles consecuencias de que el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pudiera sufrir intrusiones mientras se ejecute en dicha cuenta. Las cuentas de usuario ASPNET y NETWORK SERVICE se ejecutan con permisos mínimos, lo que reduce los posibles daños si el proceso sufre alguna intrusión. Si debe cambiar el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para que se ejecute en una cuenta que tenga permisos superiores, el daño puede ser mayor.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de aplicaciones ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Cómo: Ejecución de un proceso de trabajo en una cuenta de usuario](../debugger/how-to-run-the-worker-process-under-a-user-account.md)