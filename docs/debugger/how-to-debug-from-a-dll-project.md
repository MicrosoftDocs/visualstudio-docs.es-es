---
title: 'Cómo: depurar desde un proyecto DLL | Microsoft Docs'
ms.date: 10/10/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2e4df2028a14281ee2343ad48b4b71812d29fca
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684317"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>Cómo: depurar desde un proyecto DLL en Visual Studio (C#, C++, Visual Basic, F#)

Es una manera de depurar un proyecto DLL especificar la aplicación que realiza la llamada en las propiedades del proyecto DLL. A continuación, puede iniciar la depuración desde el propio proyecto DLL. Para que este método funcione, la aplicación debe llamar a la misma DLL en la misma ubicación que la configure. Si la aplicación busca y carga una versión diferente del archivo DLL, esa versión no contiene los puntos de interrupción. Otras formas de depurar archivos DLL, consulte [proyectos DLL de depuración](../debugger/debugging-dll-projects.md).

Si su aplicación administrada llama a un archivo DLL nativo o la aplicación nativa llama a un archivo DLL administrado, puede depurar el archivo DLL y la aplicación que realiza la llamada. Para obtener más información, vea [Cómo: depurar en modo mixto (C#, C++, Visual Basic)](../debugger/how-to-debug-in-mixed-mode.md).

Proyectos de archivos DLL nativos y administrados tienen una configuración diferente para especificar las aplicaciones que realiza la llamada.

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>Especifique una aplicación que realiza la llamada en un proyecto DLL nativo

1. Seleccione el proyecto DLL de C++ en **el Explorador de soluciones**. Seleccione el **propiedades** icono, presione **Alt**+**ENTRAR**, o bien haga clic en y elija **propiedades**.

1. En el  **\<proyecto > páginas de propiedades** diálogo cuadro, asegúrese de que el **configuración** campo en la parte superior de la ventana se establece en **depurar**.

1. Seleccione **propiedades de configuración** > **depuración**.

1. En el **depurador para iniciar** elija **depurador Local de Windows** o **depurador remoto de Windows**.

1. En el **comando** o **comando remoto** , agregue la ruta de acceso completa y el nombre de la aplicación que realiza la llamada, como un *.exe* archivo.

   ![Ventana de propiedades de depuración](../debugger/media/dbg-debugging-properties-dll.png "ventana Propiedades de depuración")

1. Agregue los argumentos de programa necesarios en el cuadro **Argumentos de comandos**.

1. Seleccione **Aceptar**.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>Especifique una aplicación que realiza la llamada en un proyecto DLL administrado

1. Seleccione el C# o proyecto de DLL de Visual Basic en **el Explorador de soluciones**. Seleccione el **propiedades** icono, presione **Alt**+**ENTRAR**, o bien haga clic en y elija **propiedades**.

1. Asegúrese de que el campo **Configuración** que hay en la parte superior de la ventana esté establecido en **Depurar**.

1. En **Iniciar acción**:

   - Para los archivos DLL de .NET Framework, seleccione **iniciar programa externo**y agregue la ruta de acceso completa y nombre de la aplicación que realiza la llamada.

   - O bien, seleccione **Iniciar explorador con la dirección URL** y rellene la dirección URL de una aplicación ASP.NET local.

   - Para los archivos DLL de .NET Core, el **depurar** página de propiedades es diferente. Seleccione **ejecutable** desde el **iniciar** lista desplegable y, a continuación, agregue la ruta de acceso completa y el nombre de la aplicación que realiza la llamada en el **ejecutable** campo.

1. Agregue los argumentos de línea de comandos necesarios en el **argumentos de línea de comandos** o **argumentos de la aplicación** campo.

   ![C#Ventana de propiedades de depuración](../debugger/media/dbg-debugging-properties-dll-csharp.png " C# ventana Propiedades de depuración")

1. Use **archivo** > **guardar los elementos seleccionados** o **Ctrl**+**S** para guardar los cambios.

## <a name="debug-from-the-dll-project"></a>Depurar desde el proyecto DLL

1. Establecer puntos de interrupción en el proyecto DLL.

1. Haga clic en el proyecto DLL y elija **establecer como proyecto de inicio**.

1. Asegúrese de que el **configuración de soluciones** campo se establece en **depurar**. Presione **F5**, haga clic en el verde **iniciar** flecha, o bien seleccione **depurar** > **Iniciar depuración**.

Si la depuración no alcanza los puntos de interrupción, asegúrese de que el archivo DLL de salida (de forma predeterminada, el  *\<proyecto > \Debug* carpeta) es la ubicación que está llamando la aplicación que realiza la llamada.

## <a name="see-also"></a>Vea también
- [Depuración de proyectos DLL](../debugger/debugging-dll-projects.md)
- [Configuración de proyectos para configuraciones de depuración en C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)