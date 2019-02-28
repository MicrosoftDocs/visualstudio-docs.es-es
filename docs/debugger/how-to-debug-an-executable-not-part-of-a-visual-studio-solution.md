---
title: Depurar una aplicación que no forma parte de una solución de Visual Studio
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/19/2018
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
ms.openlocfilehash: 49636dc4a43d56afe6d9307fc7ec2ddd44a6c37f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690206"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Depurar una aplicación que no forma parte de una solución de Visual Studio (C++, C#, Visual Basic, F#)

Es posible que desea depurar una aplicación (*.exe* archivo) que no forma parte de una solución de Visual Studio. Usted u otra persona haya creado la aplicación fuera de Visual Studio, o que obtuvo de la aplicación de alguna otra parte.

Es la forma habitual para depurar una aplicación que no existe en Visual Studio iniciar la aplicación fuera de Visual Studio y, a continuación, asocie a ella mediante **asociar al proceso** en el depurador de Visual Studio. Para obtener más información, consulte [adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Asociar a una aplicación requiere pasos manuales que tardan unos segundos. Debido a este retraso, adjuntar no ayudará a depurar un problema de inicio, o una aplicación que no espera por el usuario de entrada y finaliza rápidamente.

En estas situaciones, puede crear un proyecto EXE de Visual Studio para la aplicación o importarlo en una existente C#, Visual Basic o C++ solución. No todos los lenguajes de programación admiten proyectos EXE.

>[!IMPORTANT]
>Características de depuración para una aplicación que no se compiló en Visual Studio están limitadas, asociar a la aplicación o agregarlo a una solución de Visual Studio.
>
>Si tiene el código fuente, el mejor enfoque consiste en importar el código en un proyecto de Visual Studio. A continuación, ejecute una compilación de depuración de la aplicación.
>
>Si no tiene el código fuente y la aplicación no tiene [información de depuración](../debugger/how-to-set-debug-and-release-configurations.md) en un formato compatible, son muy pocas características de depuración disponibles.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Para crear un nuevo proyecto EXE para una aplicación existente

1. En Visual Studio, seleccione **archivo** > **abierto** > **proyecto**.

1. En el **Abrir proyecto** cuadro de diálogo, seleccione **todos los archivos de proyecto**, si aún no está seleccionada, en la lista desplegable junto a **nombre de archivo**.

1. Navegue hasta la *.exe* de archivo, selecciónelo y seleccione **abierto**.

   El archivo aparece en una solución de Visual Studio de nuevo, temporal.

1. Iniciar la depuración de la aplicación seleccionando un comando de ejecución, como **Iniciar depuración**, desde el **depurar** menú.

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Para importar una aplicación en una solución existente de Visual Studio

1.  Con C++, C#, o bien seleccione Abrir en Visual Studio, solución de Visual Basic **archivo** > **agregar** > **proyecto existente**.

1. En el **Abrir proyecto** cuadro de diálogo, seleccione **todos los archivos de proyecto**, si aún no está seleccionada, en la lista desplegable junto a **nombre de archivo**.

1. Navegue hasta la *.exe* de archivo, selecciónelo y seleccione **abierto**.

   El archivo aparece como un proyecto nuevo en la solución actual.

1. Con el nuevo archivo seleccionado, iniciar la depuración de la aplicación seleccionando un comando de ejecución, como **Iniciar depuración**, desde el **depurar** menú.

### <a name="see-also"></a>Vea también
- [Preparación y configuración del depurador](../debugger/debugger-settings-and-preparation.md)
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Archivos DBG](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))