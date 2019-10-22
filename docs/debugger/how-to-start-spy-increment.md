---
title: Procedimiento Iniciar Spy ++ | Documentos de Microsoft
ms.date: 12/16/2018
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc247a6391df0357905e2cbdb895bec4e469a248
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387533"
---
# <a name="how-to-start-spy"></a>Procedimiento Iniciar Spy++

Puede iniciar Spy ++ desde Visual Studio o en un símbolo del sistema.

 Al iniciar Spy ++, si se muestra un mensaje para solicitar permiso para realizar cambios en el equipo, seleccione **Sí**.

> [!NOTE]
> Puede ejecutar una única instancia de Spy ++. Si intenta iniciar una segunda instancia, simplemente hace que la instancia en ejecución obtener el foco.

## <a name="prerequisites"></a>Requisitos previos

Spy ++ requiere los siguientes componentes. Puede seleccionar estos componentes desde el instalador de Visual Studio seleccionando el **componentes individuales** ficha y, a continuación, seleccione los siguientes componentes.

* En la depuración y pruebas, seleccione  **C++ herramientas de generación de perfiles**
* En las actividades de desarrollo, seleccione **Visual Studio C++ características principales**

Si ha realizado algún cambio, siga las indicaciones para instalar estos componentes.

## <a name="start-spy-from-visual-studio"></a>Iniciar Spy ++ desde Visual Studio

En el **herramientas** menú, seleccione **Spy ++**.

Dado que Spy ++ se ejecuta de forma independiente, después de iniciarla puede cerrar Visual Studio.

> [!NOTE]
> Al registrar los mensajes con Spy ++, provocaría el sistema operativo realice más lentamente.

## <a name="start-spy-at-a-command-prompt"></a>Iniciar Spy ++ en un símbolo del sistema

1. En una ventana del símbolo del sistema, cambie los directorios a la carpeta que contiene spyxx.exe. Normalmente, es la ruta de acceso a esta carpeta... \\ *Carpeta de instalación de visual Studio*\Common7\Tools\\.

2. Escriba **spyxx.exe**.

## <a name="see-also"></a>Vea también
- [Usar Spy++](../debugger/using-spy-increment.md)
- [Vistas de Spy++](../debugger/spy-increment-views.md)
- [Referencia de Spy++](../debugger/spy-increment-reference.md)