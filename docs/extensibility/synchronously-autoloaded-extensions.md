---
title: Extensiones cargadas automáticamente y sincrónicamente
ms.date: 02/16/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b18642269326c516c2af0baef57cb306f60ae6a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316714"
---
# <a name="synchronously-autoloaded-extensions"></a>Extensiones cargadas automáticamente y sincrónicamente

Sincrónicamente autocargado extensiones tienen un impacto negativo en el rendimiento de Visual Studio y se deben convertir para utilizar autoload asincrónica en su lugar. A partir de Visual Studio 2019 Preview 2, los usuarios reciben notificaciones cuando una extensión se está autocargado sincrónicamente. La extensión cargará y funcionan con normalidad.

![Advertencia de compatibilidad de extensión](media/extension-compatibility-warning.png)

Los usuarios pueden:

- Haga clic en **más** para acceder a esta página de información.

- Haga clic en **administrar el rendimiento** para abrir el [cuadro de diálogo Administrador de rendimiento](#performance-manager-dialog) que muestran los problemas de rendimiento con las extensiones y ventanas de herramientas.

- Haga clic en **no volver a mostrar este mensaje** para descartarla. Si elige esta opción también impide que todas las notificaciones futuras de forma sincrónica autocargado extensiones. Los usuarios seguirán recibiendo notificaciones otras características de Visual Studio.

## <a name="performance-manager-dialog"></a>Cuadro de diálogo Administrador de rendimiento

![cuadro de diálogo de administrador de rendimiento](media/performance-manager.png)

Todas las extensiones que cargó sincrónicamente todos los paquetes en las sesiones de usuario aparecen en la **API en desuso** ficha.

* Los usuarios pueden hacer clic en el **para obtener más información sobre este problema** para recopilar más información acerca de las API en desuso.
* Los usuarios pueden ponerse en contacto con sus proveedores de extensión para ver el progreso de la migración.

Los autores de extensiones pueden encontrar instrucciones para migrar paquetes de carga asincrónica automática en [migrar a AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Especificar la configuración autoload sincrónica mediante la directiva de grupo

A partir de Visual Studio 2019 Update 1, de forma predeterminada, la carga automática sincrónica bloques instalación de Visual Studio. Cuando se habilita la directiva de grupo, puede configurar Visual Studio para permitir autoload sincrónico en equipos individuales. Para ello, establezca una directiva basada en el Registro en la siguiente clave:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

Entrada = **permitido**

Value = (DWORD)
* **0** autoload sincrónica no está permitido
* **1** se permite autoload sincrónica

Para obtener más información acerca de la configuración autoload sincrónico 2019 de Visual Studio Update 1, consulte el [comportamiento Autoload sincrónico](https://aka.ms/AA52xzw) página.
