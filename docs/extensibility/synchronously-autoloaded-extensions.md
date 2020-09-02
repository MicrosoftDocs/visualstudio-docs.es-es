---
title: Extensiones cargadas automáticamente y sincrónicamente
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab62d235fd6ed4e47e765fc23868acd5c56efcb2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699370"
---
# <a name="synchronously-autoloaded-extensions"></a>Extensiones cargadas automáticamente y sincrónicamente

Las extensiones autocargadas de forma sincrónica tienen un impacto negativo en el rendimiento de Visual Studio y deben convertirse para usar la carga asincrónica asincrónica en su lugar. De forma predeterminada, Visual Studio 2019 bloquea los paquetes cargados de forma sincrónica desde cualquier extensión y notifica al usuario.

![ADVERTENCIA de compatibilidad de extensión](media/extension-compatibility-warning-16-1.png.png)

Puede:

- Haga clic en **permitir autocargas sincrónicas** para permitir la carga de las extensiones. Para cambiar esta configuración en opciones de Visual Studio, haga clic en entorno, haga clic en extensiones y, a continuación, active la casilla "permitir autocargas sincrónicas de extensiones". 

- Haga clic en **administrar rendimiento** para abrir el [cuadro de diálogo Administrador de rendimiento](#performance-manager-dialog) que muestra los problemas de rendimiento de las ventanas de herramientas y extensiones.

- Haga clic en **no mostrar este mensaje para las extensiones actuales** para descartar la notificación y evitar las futuras notificaciones de las extensiones instaladas existentes. Si agrega una nueva extensión que se carga de forma sincrónica, esta notificación se volverá a mostrar. Seguirá recibiendo notificaciones sobre otras características de Visual Studio.

## <a name="performance-manager-dialog"></a>Cuadro de diálogo Administrador de rendimiento

![cuadro de diálogo Administrador de rendimiento](media/performance-manager.png)

Todas las extensiones que cargan de forma sincrónica los paquetes de cualquier sesión de usuario aparecen en la pestaña **API en desuso** .

* Haga clic en **más información sobre este problema** para recopilar más información sobre las API en desuso.
* Póngase en contacto con sus proveedores de extensión para el progreso de la migración.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Especificar la configuración sincrónica de carga asincrónica mediante la Directiva de grupo

Los administradores pueden habilitar una directiva de grupo para permitir la carga asincrónica sincrónica. Para ello, establezca una directiva basada en el Registro en la siguiente clave:

**HKEY_LOCAL_MACHINE \SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

Entry = **permitido**

Valor = (DWORD)
* **0** no se permite la carga automático sincrónica
* **1** se permite la carga automático sincrónica

## <a name="extension-authors"></a>Autores de extensiones
Los autores de extensiones pueden encontrar instrucciones para migrar paquetes a la carga asincrónica asincrónica en [migrar a AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="see-also"></a>Vea también
Para obtener más información sobre la configuración de la carga asincrónica sincrónica en Visual Studio 2019, vea la página [comportamiento de carga asincrónica sincrónica](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/) .
