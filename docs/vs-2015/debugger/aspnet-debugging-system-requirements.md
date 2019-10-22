---
title: 'Depuración ASP.NET: Requisitos del sistema | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aa8951be6da4d77ffb51b6bc8f09a796b373a944
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67826263"
---
# <a name="aspnet-debugging-system-requirements"></a>Depuración ASP.NET: Requisitos del sistema
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se describen los requisitos de software y seguridad de los escenarios de depuración de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] :  
  
- Depuración local, en la que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y la aplicación web se ejecutan en el mismo equipo. Existen dos versiones de este escenario:  
  
  - El código de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] reside en el sistema de archivos.  

  - El código de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] reside en un sitio web de IIS.  
  
- La depuración remota, en la que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se ejecuta en un equipo cliente y depura una aplicación web que se está ejecutando en un equipo servidor remoto.  
  
## <a name="security-requirements"></a>Requisitos de seguridad  
 Para la depuración remota, los equipos locales y remotos deben estar en una configuración de dominio o una configuración de grupo de trabajo.  
  
 Para depurar el proceso de trabajo de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , debe tener permiso para depurar dicho proceso. De forma predeterminada, las aplicaciones de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] se ejecutan como el usuario **ASPNET** . Si el proceso de trabajo se ejecuta con la cuenta **ASPNET**o **NETWORK SERVICE**, deberá tener privilegios de administrador para depurarlo.  
  
 El nombre del proceso de trabajo de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] varía en función del escenario de depuración y de la versión de IIS. Para obtener más información, consulte [Cómo Búsqueda del nombre de un proceso de ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Puede cambiar la cuenta de usuario en la que se ejecuta el proceso de trabajo de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] editando el archivo machine.config en el servidor que ejecuta IIS. La mejor manera de hacerlo es mediante el **Administrador de Internet Information Services (IIS)** . Para obtener más información, consulte [Cómo Ejecución de un proceso de trabajo en una cuenta de usuario](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Si cambia el proceso de trabajo de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] para que se ejecute en su propia cuenta de usuario, no tiene porqué ser administrador en el servidor que esté ejecutando IIS.  
  
> [!CAUTION]
> Antes de cambiar el proceso de trabajo de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] para que se ejecute en una cuenta diferente, tenga en cuenta las posibles consecuencias de que el proceso de trabajo de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pudiera sufrir intrusiones mientras se ejecute en dicha cuenta. Las cuentas de usuario ASPNET y NETWORK SERVICE se ejecutan con permisos mínimos, lo que reduce los posibles daños si el proceso sufre alguna intrusión. Si debe cambiar el proceso de trabajo de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] para que se ejecute en una cuenta que tenga permisos superiores, el daño puede ser mayor.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones de ASP.NET y AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Cómo: Ejecución de un proceso de trabajo en una cuenta de usuario](../debugger/how-to-run-the-worker-process-under-a-user-account.md)
