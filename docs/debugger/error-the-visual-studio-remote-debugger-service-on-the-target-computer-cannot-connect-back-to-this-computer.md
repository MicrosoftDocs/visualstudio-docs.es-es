---
title: 'Error: El servicio del depurador remoto de Visual Studio en el equipo de destino no se puede conectar a este equipo | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3cfd2db1e4bf5b87d12eb5d5ffcf94d06e142516
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471757"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Error: El servicio del depurador remoto de Visual Studio del equipo de destino no se puede volver a conectar a este equipo
Este error significa que el servicio del depurador remoto de Visual Studio se ejecuta con una cuenta de usuario que no se puede autenticar cuando intenta conectarse al equipo desde el que se realiza la depuración.  
  
 En la tabla siguiente se muestran las cuentas que pueden tener acceso al equipo:  
  
|||||  
|-|-|-|-|  
||Cuenta LocalSystem|Cuenta de dominio|Cuentas locales con el mismo nombre de usuario y contraseña en ambos equipos|  
|Ambos equipos en el mismo dominio|Sí|Sí|Sí|  
|Ambos equipos en dominios que tienen confianza bidireccional|No|No|Sí|  
|Uno o ambos equipos en un grupo de trabajo|No|No|Sí|  
|Equipos en dominios diferentes|No|No|Sí|  
  
 Además:  
  
-   La cuenta en la que se ejecuta el servicio del depurador remoto de Visual Studio debe ser una cuenta de administrador en el equipo remoto, de modo que éste pueda depurar cualquier proceso.  
  
-   La cuenta también necesita tener la `Log on as a service` con privilegios en el equipo remoto que está usando el **directiva de seguridad Local** herramienta administrativa.  
  
-   Si está usando un acceso de cuenta local al equipo, debe ejecutar el servicio del depurador remoto de Visual Studio con una cuenta local.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Asegúrese de que el servicio del depurador remoto de Visual Studio esté correctamente configurado en el equipo remoto. Para obtener más información, consulte [depuración remota](../debugger/remote-debugging.md).  
  
2.  Ejecute el servicio del depurador remoto bajo una cuenta que puede tener acceso al equipo host del depurador, como se muestra en la tabla anterior.  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>Para agregar el privilegio "Iniciar sesión como servicio"  
  
1.  En el **iniciar** menú, elija **el Panel de Control**.  
  
2.  En el Panel de Control, elija **vista clásica**, si es necesario.  
  
3.  Haga doble clic en **herramientas administrativas**.  
  
4.  En la ventana Herramientas administrativas, haga doble clic en **directiva de seguridad Local**.  
  
5.  En el **configuración de seguridad Local** ventana, expanda la **directivas locales** carpeta.  
  
6.  Haga clic en **asignación de derechos de usuario**.  
  
7.  En el **directiva** columna, haga doble clic en **iniciar sesión como un servicio** para ver las asignaciones actuales de la directiva de grupo locales en el **iniciar sesión como un servicio** cuadro de diálogo.  
  
8.  Para agregar nuevos usuarios, haga clic en el **Agregar usuario o grupo** botón.  
  
9. Cuando haya terminado de agregar usuarios, haga clic en **Aceptar**.  
  
### <a name="to-work-around-this-error"></a>Para solucionar este error  
  
-   Ejecute el Monitor de depuración remota como aplicación en lugar de como servicio.  
  
## <a name="see-also"></a>Vea también  
 [Errores de depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuración remota](../debugger/remote-debugging.md)