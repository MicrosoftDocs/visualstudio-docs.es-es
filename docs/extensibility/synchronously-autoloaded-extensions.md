---
title: Sincrónicamente autocargado extensiones
ms.date: 02/16/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 960fd54564bc25a8338461c30cd8a893e277b5a5
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2019
ms.locfileid: "56844585"
---
# <a name="synchronously-autoloaded-extensions"></a>Sincrónicamente autocargado extensiones

Sincrónicamente autocargado extensiones tienen un impacto negativo en el rendimiento de Visual Studio y se deben convertir para utilizar autoload asincrónica en su lugar. A partir de Visual Studio 2019 Preview 2, se notificará a los usuarios cuando una extensión se está autocargado sincrónicamente. La extensión cargará y funcionan con normalidad.

![Advertencia de compatibilidad de extensión](media/extension-compatibility-warning.png)

1. Los usuarios pueden hacer clic en **más** para acceder a esta página de información.

3. Los usuarios pueden hacer clic en **administrar el rendimiento** para abrir el [cuadro de diálogo Administrador de rendimiento](#performance-manager-dialog) que muestran los problemas de rendimiento con las extensiones y ventanas de herramientas.

3. Los usuarios pueden hacer clic en **no volver a mostrar este mensaje** para descartarla. Si elige esta opción también impedirá que todas las notificaciones futuras de forma sincrónica autocargado extensiones. Los usuarios seguirán recibir notificaciones de otras características de Visual Studio.

### <a name="performance-manager-dialog"></a>Cuadro de diálogo Administrador de rendimiento

  ![cuadro de diálogo de administrador de rendimiento](media/performance-manager.png)

Todas las extensiones que cargó sincrónicamente todos los paquetes en las sesiones de usuario se mostrarán en el **API en desuso** ficha.

* Los usuarios pueden hacer clic en el **para obtener más información sobre este problema** para recopilar más información acerca de las API en desuso.
* Los usuarios pueden ponerse en contacto con sus proveedores de extensión para ver el progreso de la migración.

Los autores de extensiones pueden encontrar instrucciones para migrar paquetes de carga asincrónica automática en [migrar a AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).
