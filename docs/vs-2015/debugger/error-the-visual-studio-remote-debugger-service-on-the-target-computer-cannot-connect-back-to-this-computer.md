---
title: 'Error: El servicio de Visual Studio Remote Debugger del equipo de destino no se puede conectar a este equipo | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f1e457829f7b6ab5050a02bd8f20e1c51d5df14
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798474"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Error: El servicio del depurador remoto de Visual Studio del equipo de destino no se puede volver a conectar a este equipo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
-   La cuenta también debe concederse el `Log on as a service` privilegios en el equipo remoto que está usando el **directiva de seguridad Local** herramienta administrativa.  
  
-   Si está usando un acceso de cuenta local al equipo, debe ejecutar el servicio del depurador remoto de Visual Studio con una cuenta local.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Asegúrese de que el servicio del depurador remoto de Visual Studio esté correctamente configurado en el equipo remoto. Para obtener más información, consulte [establecer las herramientas remotas en el dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
2.  Ejecute el servicio del depurador remoto bajo una cuenta que puede tener acceso al equipo host del depurador, como se muestra en la tabla anterior.  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>Para agregar el privilegio "Iniciar sesión como servicio"  
  
1.  En el **iniciar** menú, elija **Panel de Control**.  
  
2.  En el Panel de Control, elija **vista clásica**, si es necesario.  
  
3.  Haga doble clic en **herramientas administrativas**.  
  
4.  En la ventana Herramientas administrativas, haga doble clic en **directiva de seguridad Local**.  
  
5.  En el **configuración de seguridad Local** ventana, expanda el **directivas locales** carpeta.  
  
6.  Haga clic en **asignación de derechos de usuario**.  
  
7.  En el **directiva** columna, haga doble clic en **iniciar sesión como un servicio** para ver las asignaciones actuales de la directiva de grupo locales en el **iniciar sesión como un servicio** cuadro de diálogo.  
  
8.  Para agregar nuevos usuarios, haga clic en el **Agregar usuario o grupo** botón.  
  
9. Cuando haya terminado de agregar usuarios, haga clic en **Aceptar**.  
  
### <a name="to-work-around-this-error"></a>Para solucionar este error  
  
-   Ejecute el Monitor de depuración remota como aplicación en lugar de como servicio.  
  
## <a name="see-also"></a>Vea también  
 [Errores de depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



