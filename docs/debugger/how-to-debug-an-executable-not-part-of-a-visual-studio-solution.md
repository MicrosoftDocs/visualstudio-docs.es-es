---
title: Depurar una aplicación que no forma parte de una solución de Visual Studio
titleSuffix: ''
ms.custom: ''
ms.date: 02/21/2020
ms.topic: conceptual
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
ms.openlocfilehash: 740af718a2928991d46bedbd6709337b9b20a254
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557903"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Depurar una aplicación que no forma parte de una soluciónC++de C#Visual Studio ( F#,, Visual Basic,)

Es posible que desee depurar una aplicación (archivo *. exe* ) que no forme parte de una solución de Visual Studio. Puede tratarse de un proyecto de [carpeta abierta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) , o puede que usted u otra persona haya creado la aplicación fuera de Visual Studio o que haya recibido la aplicación desde otra parte.

- Para un proyecto de carpeta abierta en Visual Studio (que no tiene un archivo de proyecto o de solución), vea [Ejecutar y depurar el código](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) o, para C++, [Configurar parámetros de depuración con Launch. vs. JSON](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson).

- En el caso de una aplicación que no existe en Visual Studio, la manera habitual de depurar es iniciar la aplicación fuera de Visual Studio y, a continuación, asociarla mediante **asociar al proceso** en el depurador de Visual Studio. Para obtener más información, vea [asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

   La asociación a una aplicación requiere pasos manuales que tardan unos segundos. Debido a este retraso, la asociación no ayudará a depurar un problema de inicio o a una aplicación que no espere la entrada del usuario y finalice rápidamente.

   En estas situaciones, puede crear un proyecto EXE de Visual Studio para la aplicación o importarlo en una solución existente C#, Visual Basic o C++ . No todos los lenguajes de programación admiten proyectos EXE.

>[!IMPORTANT]
>Las características de depuración de una aplicación que no se compilaron en Visual Studio son limitadas, tanto si se asocia a la aplicación como si se agrega a una solución de Visual Studio.
>
>Si tiene el código fuente, el mejor enfoque es importar el código en un proyecto de Visual Studio. A continuación, ejecute una compilación de depuración de la aplicación.
>
>Si no tiene el código fuente y la aplicación no tiene información de [depuración](../debugger/how-to-set-debug-and-release-configurations.md) en un formato compatible, las características de depuración disponibles son muy pocas.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Para crear un nuevo proyecto EXE para una aplicación existente

1. En Visual Studio, seleccione **archivo** > **abrir** > **proyecto**.

1. En el cuadro de diálogo **Abrir proyecto** , seleccione **todos los archivos de proyecto**, si aún no está seleccionado, en la lista desplegable junto a **nombre de archivo**.

1. Desplácese hasta el archivo *. exe* , selecciónelo y seleccione **abrir**.

   El archivo aparece en una nueva solución temporal de Visual Studio.

1. Inicie la depuración de la aplicación seleccionando un comando de ejecución, como **iniciar depuración**, en el menú **depurar** .

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Para importar una aplicación en una solución existente de Visual Studio

1. Con una C++solución C#de, o Visual Basic abierta en Visual Studio, seleccione **archivo** > **Agregar** > **proyecto existente**.

1. En el cuadro de diálogo **Abrir proyecto** , seleccione **todos los archivos de proyecto**, si aún no está seleccionado, en la lista desplegable junto a **nombre de archivo**.

1. Desplácese hasta el archivo *. exe* , selecciónelo y seleccione **abrir**.

   El archivo aparece como un nuevo proyecto en la solución actual.

1. Con el nuevo archivo seleccionado, inicie la depuración de la aplicación seleccionando un comando de ejecución, como **iniciar depuración**, en el menú **depurar** .

### <a name="see-also"></a>Consulte también
- [Preparación y configuración del depurador](../debugger/debugger-settings-and-preparation.md)
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Archivos DBG](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))