---
title: Desarrollar aplicaciones para la Plataforma universal de Windows (UWP)
description: Aprenda a crear aplicaciones con Visual Studio y las herramientas de desarrollo de aplicaciones universales de Windows.
ms.custom: SEO-VS-2020
ms.date: 10/24/2017
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: e9cff517c60a67ee9bbf929c59a1150d5ace3757
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671424"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Desarrollar aplicaciones para la Plataforma universal de Windows (UWP)

Con la Plataforma universal de Windows y nuestro núcleo único de Windows, puede ejecutar la misma aplicación en cualquier dispositivo con Windows 10, desde teléfonos hasta equipos de escritorio. Cree estas aplicaciones con Visual Studio y las herramientas de desarrollo de aplicaciones Windows universales.

![Plataforma universal de Windows](../cross-platform/media/uwp_coreextensions.png)

Ejecute su aplicación en un teléfono con Windows 10, un equipo de escritorio con Windows 10 o una Xbox. Es el mismo paquete de aplicaciones. Con la introducción del núcleo unificado de Windows 10, un mismo paquete de la aplicación puede ejecutarse en todas las plataformas. Varias plataformas tienen SDK de extensión que puede agregar a su aplicación para aprovechar los comportamientos específicos de cada plataforma. Por ejemplo, un SDK de extensión para móvil controla la pulsación del botón atrás en un teléfono Windows. Si hace referencia a un SDK de extensión en su proyecto, solo tiene que agregar comprobaciones en tiempo de ejecución para comprobar que ese SDK se encuentre disponible en esa plataforma. Así es cómo puede tener el mismo paquete de aplicaciones para todas las plataformas.

**¿Qué es el núcleo de Windows?**

Por primera vez Windows se ha refactorizado para que tenga un núcleo común para todas las plataformas Windows 10. Hay un código fuente común, un kernel de Windows común, una pila común de E/S de archivos y un modelo de aplicación común. Para la interfaz de usuario, solo hay un marco de interfaz de usuario XAML y un marco de interfaz de usuario HTML. Puede concentrarse en crear una excelente aplicación, ya que hemos hecho muy fácil que pueda ejecutarse en distintos dispositivos con Windows 10.

**¿Qué es exactamente la Plataforma universal de Windows?**

La Plataforma universal de Windows es simplemente una colección de contratos y versiones. Estos le permiten definir dónde se puede ejecutar la aplicación. El destino ya no es un sistema operativo; ahora el destino es una o varias familias de dispositivos. Para obtener más información, lea [Introducción a la Plataforma universal de Windows](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="requirements"></a>Requisitos

Las herramientas de desarrollo de aplicaciones Windows universales incluyen emuladores que puede usar para ver su aspecto en diferentes dispositivos. Si quiere usar estos emuladores, debe instalar este software en un equipo físico. El equipo físico debe ejecutar Windows 8.1 (x 64) Professional Edition o superior y disponer de un procesador compatible con Cliente Hyper-V y Traducción de direcciones de segundo nivel (SLAT). Los emuladores no se pueden usar cuando Visual Studio está instalado en una máquina virtual.

Esta es la lista del software que necesita:

::: moniker range="vs-2017"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Visual Studio 2017 solo admite el desarrollo para UWP en Windows 10. Para obtener más información, vea [Destinatarios de la plataforma](/visualstudio/productinfo/vs2017-compatibility-vs) y [Requisitos del sistema](/visualstudio/productinfo/vs2017-system-requirements-vs) de Visual Studio.

- [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download). También necesitará la carga de trabajo opcional de desarrollo de la Plataforma universal de Windows.

     ![Carga de trabajo de UWP](media/uwp_workload.png)

::: moniker-end

::: moniker range="vs-2019"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Visual Studio 2019 solo admite el desarrollo para UWP en Windows 10. Para obtener más información, vea [Destinatarios de la plataforma](/visualstudio/releases/2019/compatibility/) y [Requisitos del sistema](/visualstudio/releases/2019/system-requirements/) de Visual Studio.

- [Visual Studio](https://visualstudio.microsoft.com/downloads). También necesitará la carga de trabajo opcional de desarrollo de la Plataforma universal de Windows.

     ![Carga de trabajo de UWP](media/uwp_workload.png)

::: moniker-end

Después de instalar este software, tiene que habilitar el dispositivo con Windows 10 para el desarrollo. Vea [Habilitar el dispositivo para el desarrollo](/windows/uwp/get-started/enable-your-device-for-development). Ya no necesita una licencia de desarrollador para cada dispositivo con Windows 10.

## <a name="universal-windows-apps"></a>Aplicaciones Windows universales

Elija el lenguaje de desarrollo que prefiera (C#, Visual Basic, C++ o JavaScript) para crear una aplicación Plataforma universal de Windows para dispositivos con Windows 10. Lea [Crear tu primera aplicación](/windows/uwp/get-started/your-first-app) o vea el vídeo de [información general sobre las herramientas para Windows 10](https://channel9.msdn.com/Series/ConnectOn-Demand/229).

Si tiene aplicaciones de la Tienda Windows 8.1, de Windows Phone 8.1 o aplicaciones Windows universales creadas con Visual Studio 2015, tendrá que portar estas aplicaciones para usar la Plataforma universal de Windows más reciente. Vea [Mover de Windows Runtime 8.x a UWP](/windows/uwp/porting/w8x-to-uwp-root).

Después de crear la aplicación Windows universal, debe empaquetarla para instalarla en un dispositivo con Windows 10 o enviarla a la Tienda Windows. Vea [Empaquetado de aplicaciones](/windows/uwp/packaging/index).

## <a name="see-also"></a>Consulte también

- [Desarrollo móvil multiplataforma en Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)
