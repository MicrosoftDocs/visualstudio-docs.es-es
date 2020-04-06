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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699370"
---
# <a name="synchronously-autoloaded-extensions"></a>Extensiones cargadas automáticamente y sincrónicamente

Las extensiones cargadas automáticamente sincrónicamente tienen un impacto negativo en el rendimiento de Visual Studio y se deben convertir para usar la carga automática asincrónica en su lugar. De forma predeterminada, Visual Studio 2019 bloquea los paquetes cargados automáticamente sincrónicamente desde cualquier extensión y notifica al usuario.

![advertencia de compatibilidad de extensión](media/extension-compatibility-warning-16-1.png.png)

Puede:

- Haga clic en **Permitir carga automática sincrónica** para permitir que las extensiones se carguen automáticamente. Para cambiar esta configuración en las opciones de Visual Studio, haga clic en Entorno, haga clic en Extensionesy, a continuación, active la casilla "Permitir la carga automática sincrónica de extensiones". 

- Haga clic en **Administrar rendimiento** para abrir el cuadro de diálogo Administrador de [rendimiento](#performance-manager-dialog) que muestra problemas de rendimiento con extensiones y ventanas de herramientas.

- Haga clic en **No mostrar este mensaje para las extensiones actuales** para descartar la notificación y evitar futuras notificaciones de extensiones instaladas existentes. Si agrega una nueva extensión que se carga automáticamente, esta notificación se mostrará de nuevo. Seguirá recibiendo notificaciones sobre otras características de Visual Studio.

## <a name="performance-manager-dialog"></a>Diálogo de Performance Manager

![diálogo del administrador de rendimiento](media/performance-manager.png)

Todas las extensiones que cargaron sincrónicamente los paquetes de las sesiones de usuario aparecen en la pestaña **API en desuso.**

* Haga clic en **Más información sobre este problema** para recopilar más información sobre las API en desuso.
* Póngase en contacto con sus proveedores de extensiones para conocer el progreso de la migración.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Especificar la configuración de carga automática sincrónica mediante la directiva de grupo

Los administradores pueden habilitar una directiva de grupo para permitir la carga automática sincrónica. Para ello, establezca una directiva basada en el Registro en la siguiente clave:

**HKEY_LOCAL_MACHINE,SOFTWARE, Directivas, Microsoft, VisualStudio, SynchronousAutoload**

Entrada: **Se permite**

Valor = (DWORD)
* **0** es autocarga sincrónica no permitida
* **1** es autocarga síncrona permitida

## <a name="extension-authors"></a>Autores de extensiones
Los autores de extensiones pueden encontrar instrucciones para migrar paquetes a la carga automática asincrónica en [Migrate to AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="see-also"></a>Vea también
Para obtener más información acerca de la configuración de carga automática sincrónica en Visual Studio 2019, vea la página Comportamiento de [carga automática sincrónica.](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/)
