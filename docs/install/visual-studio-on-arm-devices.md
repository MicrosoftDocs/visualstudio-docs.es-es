---
title: Visual Studio en dispositivos con tecnología ARM
description: Recomendaciones para usar Visual Studio en dispositivos con procesadores basados en ARM.
ms.date: 09/10/2020
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 367b3681d2ff8a828ee45f59359043b5fede3d26
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668110"
---
# <a name="visual-studio-on-arm-powered-devices"></a>Visual Studio en dispositivos con tecnología ARM

> [!IMPORTANT]
> Visual Studio solo es compatible en dispositivos que usan un procesador basado en AMD64/x64 o x86.

Visual Studio está creado para apuntar a procesadores basados en la arquitectura x86 y no hay versiones de Visual Studio para procesadores basados en ARM. Sin embargo, Windows proporciona [emulación de x86 en ARM](https://www.docs.microsoft.com/windows/uwp/porting/apps-on-arm-x86-emulation), que Visual Studio puede ejecutar. La ejecución de Visual Studio en un procesador ARM a través de la emulación de x86 perjudica considerablemente el rendimiento de Visual Studio y son varias las características de Visual Studio que no están diseñadas para funcionar en este escenario. Por lo tanto, no es recomendable ejecutar Visual Studio en dispositivos que usan procesadores basados en ARM y, en su lugar, se recomiendan los dispositivos ARM de destino remoto.

## <a name="remote-targeting-arm-devices"></a>Dispositivos ARM de destino remoto
Para disfrutar de la mejor experiencia, se recomienda usar Visual Studio en un equipo independiente con tecnología x86 y usar las características de implementación y depuración remotas de Visual Studio para apuntar al dispositivo basado en ARM. Para depurar las aplicaciones universales de Windows que ya están instaladas en el dispositivo, consulte la documentación [Depuración de un paquete de aplicaciones instalado](../debugger/debug-installed-app-package.md). Para implementar una aplicación nueva, consulte el artículo sobre la [ejecución remota de una aplicación de la Tienda Windows](../debugger/run-windows-store-apps-on-a-remote-machine.md). Para todos los demás tipos de aplicaciones, consulte la documentación sobre la [depuración remota](../debugger/remote-debugging.md).

## <a name="tips-for-running-visual-studio-on-arm-devices"></a>Sugerencias para ejecutar Visual Studio en dispositivos ARM

### <a name="use-only-when-needed"></a>Uso solo cuando sea necesario
Optimice su tiempo usando Visual Studio solo cuando sea necesario para realizar trabajo específico de ARM. El rendimiento en cualquier dispositivo con tecnología ARM va a ser deficiente y es probable que le resulte inaceptable para el uso habitual.

### <a name="install-time"></a>Hora de instalación
Prepárese para que Visual Studio tarde más en instalarse y tenga en cuenta que es posible que se pause durante ciertos períodos de tiempo o que sea necesario reiniciar.
 
### <a name="remote-tools"></a>Herramientas remotas
Para depurar una aplicación que se ejecuta en un dispositivo remoto, deberá [descargar e instalar las herramientas remotas](../debugger/remote-debugging.md#download-and-install-the-remote-tools) para ARM.

### <a name="start-debugging-f5"></a>Iniciar la depuración (F5)
No todos los proyectos de Visual Studio están configurados para iniciar proyectos de manera local cuando se inicia la depuración (**F5**) desde un dispositivo ARM. Es posible que tenga que configurar Visual Studio para realizar la depuración remota, aunque la aplicación se ejecute localmente. Para más información, consulte [Depuración remota](../debugger/remote-debugging.md).

## <a name="we-need-your-help"></a>Necesitamos que nos ayude.
Si quiere que Visual Studio se ejecute de forma nativa en dispositivos ARM, nos encantaría saber sobre los escenarios y el soporte necesarios. Puede ponerse en contacto con nosotros si publica en [Developer Community](https://developercommunity.visualstudio.com/idea/1161018/native-arm-support-for-visual-studio.html).
