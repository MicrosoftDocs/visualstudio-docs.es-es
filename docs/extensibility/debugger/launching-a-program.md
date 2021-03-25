---
title: Iniciar un programa | Microsoft Docs
description: Obtenga información sobre la serie de eventos que tienen lugar al depurar un programa con F5 para ejecutar el depurador desde el IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a21036d3a9661306d1efff5a66ae47f8f7404209
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094723"
---
# <a name="launch-a-program"></a>Iniciar un programa
Los usuarios que deseen depurar un programa pueden presionar **F5** para ejecutar el depurador desde el IDE. Esto inicia una serie de eventos que, en última instancia, el IDE se conecta a un motor de depuración (DE) que, a su vez, se conecta o adjunta al programa de la siguiente manera:

1. El IDE llama primero al paquete del proyecto para obtener la configuración de depuración activa del proyecto de la solución. La configuración incluye el directorio de inicio, las variables de entorno, el puerto en el que se ejecutará el programa y el DE que se va a usar para crear el programa, si se especifica. Esta configuración se pasa al paquete de depuración.

2. Si se especifica un DE, el DE llama al sistema operativo para iniciar el programa. Como consecuencia del inicio del programa, el entorno en tiempo de ejecución del programa se carga. Por ejemplo, si un programa está escrito en MSIL, se invocará el Common Language Runtime para ejecutar el programa.

    O bien

    Si no se especifica un DE, el puerto llama al sistema operativo para iniciar el programa, lo que hace que se cargue el entorno en tiempo de ejecución del programa.

   > [!NOTE]
   > Si se usa un DE para iniciar un programa, es probable que el mismo DE se adjunte al programa.

3. Dependiendo de si el DE o el puerto inició el programa, el DE o el entorno en tiempo de ejecución creará una descripción del programa, o un nodo, y notificará al puerto que el programa se está ejecutando.

   > [!NOTE]
   > Se recomienda que el entorno de tiempo de ejecución cree el nodo de programa, porque el nodo de programa es una representación ligera de un programa que se puede depurar. No es necesario cargar todo desde solo para crear y registrar un nodo DE programa. Si el DE está diseñado para ejecutarse en el proceso del IDE, pero no se está ejecutando ningún IDE, debe haber un componente que pueda agregar un nodo de programa al puerto.

   El programa recién creado, junto con cualquier otro programa, relacionado o no relacionado, iniciado o asociado desde el mismo IDE, cree una sesión de depuración.

   Mediante programación, cuando el usuario presiona **F5**, el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] paquete de depuración llama al paquete del proyecto (que está asociado con el tipo de programa que se está iniciando) a través del <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> método, que a su vez rellena una <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> estructura con la configuración de depuración activa del proyecto de la solución. Esta estructura se devuelve al paquete de depuración a través de una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> método. A continuación, el paquete de depuración crea una instancia del administrador de depuración de sesión (SDM), que inicia el programa que se está depurando y cualquier motor de depuración asociado.

   Uno de los argumentos pasados al SDM es el GUID del DE que se va a usar para iniciar el programa.

   Si no es `GUID_NULL` , el SDM crea el de y, a continuación, llama a su método [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) para iniciar el programa. Por ejemplo, si un programa está escrito en código nativo, `IDebugEngineLaunch2::LaunchSuspended` probablemente llamará `CreateProcess` `ResumeThread` a y a (funciones de Win32) para ejecutar el programa.

   Como consecuencia del inicio del programa, se carga el entorno en tiempo de ejecución del programa. A continuación, el DE o el entorno en tiempo de ejecución crea una interfaz [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) para describir el programa y pasa esta interfaz a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) para notificar al puerto que el programa se está ejecutando.

   Si `GUID_NULL` se pasa, el puerto inicia el programa. Una vez que el programa se está ejecutando, el entorno de tiempo de ejecución crea una `IDebugProgramNode2` interfaz para describir el programa y lo pasa a `IDebugPortNotify2::AddProgramNode` . Esto notifica al puerto que el programa se está ejecutando. Después, el SDM asocia el motor de depuración al programa en ejecución.

## <a name="in-this-section"></a>En esta sección
 [Notificación del puerto](../../extensibility/debugger/notifying-the-port.md) Explica lo que ocurre cuando se inicia un programa y se notifica al puerto.

 [Adjuntar después de un inicio](../../extensibility/debugger/attaching-after-a-launch.md) Documentos cuando la sesión de depuración está lista para adjuntar el DE al programa.

## <a name="related-sections"></a>Secciones relacionadas
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md) Contiene vínculos a diversas tareas de depuración, como el inicio de un programa y la evaluación de expresiones.
