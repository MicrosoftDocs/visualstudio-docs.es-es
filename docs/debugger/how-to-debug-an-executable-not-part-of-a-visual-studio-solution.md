---
title: Depuración de una aplicación que no forma parte de una solución de Visual Studio
titleSuffix: ''
ms.custom: ''
ms.date: 02/21/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8cb71acb9c1c332f269f77129fa2d11a9a874f8
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350152"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Depuración de una aplicación que no forma parte de una solución de Visual Studio (C++, C#, Visual Basic y F#)

Tal vez le interese depurar una aplicación (archivo *.exe*) que no forma parte de una solución de Visual Studio. Puede que sea un proyecto de [carpeta abierta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), que usted u otra persona hayan creado la aplicación fuera de Visual Studio o que usted haya obtenido la aplicación en otra parte.

- Para un proyecto de carpeta abierta en Visual Studio (sin archivo de proyecto o de solución), vea [Ejecución y depuración del código](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) o, en el caso de C++, [Configurar parámetros de depuración con launch.vs.json](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson).

- En el caso de una aplicación que no exista en Visual Studio, la manera habitual de realizar la depuración es iniciar la aplicación fuera de Visual Studio y, a continuación, asociarla mediante **Asociar al proceso** en el depurador de Visual Studio. Para obtener más información, vea [Asociar con procesos en ejecución con el depurador de Visual Studio](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

   La asociación con una aplicación requiere pasos manuales que tardan unos segundos. Debido a este retraso, la asociación no ayudará a depurar un problema de inicio ni una aplicación que no espere la entrada de usuario y finalice rápidamente.

   En estas situaciones, puede crear un proyecto EXE de Visual Studio para la aplicación o importarlo en una solución existente de C#, Visual Basic o C++. No todos los lenguajes de programación admiten proyectos EXE.

>[!IMPORTANT]
>Las características de depuración de una aplicación que no se haya compilado en Visual Studio son limitadas, tanto si las asocia con la aplicación como si las agrega a una solución de Visual Studio.
>
>Si tiene el código fuente, el mejor enfoque es importar el código en un proyecto de Visual Studio. A continuación, ejecute una compilación de depuración de la aplicación.
>
>Si no dispone del código fuente y la aplicación no tiene [información de depuración](../debugger/how-to-set-debug-and-release-configurations.md) en un formato compatible, las características de depuración disponibles son muy pocas.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Creación de un proyecto EXE nuevo para una aplicación existente

1. En Visual Studio, seleccione **Archivo** > **Abrir** > **Proyecto**.

1. En el cuadro de diálogo **Abrir proyecto**, seleccione la opción **Todos los archivos de proyecto**, si aún no la ha seleccionado, en la lista desplegable junto a **Nombre de archivo**.

1. Vaya al archivo *.exe*, selecciónelo y elija **Abrir**.

   El archivo se muestra en una nueva solución temporal de Visual Studio.

1. Para iniciar la depuración de la aplicación, seleccione un comando de ejecución, como **Iniciar depuración**, en el menú **Depurar**.

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Importación de una aplicación en una solución de Visual Studio existente

1. Con una solución de C++, C# o Visual Basic abierta en Visual Studio, seleccione **Archivo** > **Agregar** > **Proyecto existente**.

1. En el cuadro de diálogo **Abrir proyecto**, seleccione la opción **Todos los archivos de proyecto**, si aún no la ha seleccionado, en la lista desplegable junto a **Nombre de archivo**.

1. Vaya al archivo *.exe*, selecciónelo y elija **Abrir**.

   El archivo se muestra como un proyecto nuevo en la solución actual.

1. Con el nuevo archivo seleccionado, inicie la depuración de la aplicación mediante la selección de un comando de ejecución, como **Iniciar depuración**, en el menú **Depurar**.

### <a name="see-also"></a>Vea también
- [Preparación y configuración del depurador](../debugger/debugger-settings-and-preparation.md)
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Archivos DBG](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))