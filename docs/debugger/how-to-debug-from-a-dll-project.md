---
title: para depurar desde un proyecto DLL | Microsoft Docs
description: Puede iniciar la depuración de un proyecto de DLL desde el propio proyecto, especificando la aplicación que realiza la llamada en las propiedades del proyecto. Consulta este artículo para obtener más información.
ms.custom: SEO-VS-2020
ms.date: 3/30/2021
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7846cc3fd17b46365da59f6fe1a744032cb8ba14
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106083647"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>Procedimiento para depurar desde un proyecto DLL en Visual Studio (C#, C++, Visual Basic, F#)

Una manera de depurar un proyecto DLL consiste en especificar la aplicación que realiza la llamada en las propiedades del proyecto DLL. Después, puede iniciar la depuración desde el propio proyecto DLL. Para que este método funcione, la aplicación debe llamar al mismo archivo DLL en la misma ubicación que en la que se configura. Si la aplicación encuentra y carga otra versión del archivo DLL, esa versión no contendrá los puntos de interrupción. Para obtener otros métodos de depuración de archivos DLL, vea [Depuración de proyectos DLL](../debugger/debugging-dll-projects.md).

Si la aplicación administrada llama a un archivo DLL nativo o si la aplicación nativa llama a un archivo DLL administrado, puede depurar el archivo DLL y la aplicación que realiza la llamada. Para obtener más información, vea [Cómo: Depurar en modo mixto](../debugger/how-to-debug-in-mixed-mode.md).

Los proyectos de archivos DLL nativos y administrados tienen otra configuración para especificar las aplicaciones que realizan la llamada.

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>Especificación de una aplicación de llamada en un proyecto DLL nativo

1. Seleccione el proyecto DLL de C++ en el **Explorador de soluciones**. Seleccione el icono **Propiedades**, presione **Alt**+**Entrar**, o bien haga clic con el botón derecho y seleccione **Propiedades**.

1. En el cuadro de diálogo **Páginas de propiedades de \<Project>** , asegúrese de que el campo **Configuración** de la parte superior de la ventana esté establecido en **Depurar**.

1. Seleccione **Propiedades de configuración** > **Depuración**.

1. En la lista **Depurador para iniciar**, elija **Depurador local de Windows** o  **Depurador remoto de Windows**.

1. En el cuadro **Comando** o **Comando remoto**, agregue la ruta de acceso completa y el nombre de archivo de la aplicación que realiza la llamada, como un archivo *.exe*.

   ![Ventana Propiedades de depuración](../debugger/media/dbg-debugging-properties-dll.png "Ventana Propiedades de depuración")

1. Agregue los argumentos de programa necesarios en el cuadro **Argumentos de comandos**.

1. Seleccione **Aceptar**.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>Especificación de una aplicación de llamada en un proyecto DLL administrado

1. Seleccione el proyecto DLL de C# o Visual Basic en el **Explorador de soluciones**. Seleccione el icono **Propiedades**, presione **Alt**+**Entrar**, o bien haga clic con el botón derecho y seleccione **Propiedades**.

1. Asegúrese de que el campo **Configuración** que hay en la parte superior de la ventana esté establecido en **Depurar**.

1. En **Acción de inicio**:

   - Para archivos DLL de .NET Framework, seleccione **Programa externo de inicio** y agregue la ruta de acceso y el nombre completo de la aplicación que realiza la llamada.

   - O bien, seleccione **Iniciar explorador con la dirección URL** y rellene la dirección URL de una aplicación de ASP.NET local.

   - En el caso de los archivos DLL de .NET Core, la página **Propiedades de depuración** es diferente. Seleccione **Ejecutable** en el menú desplegable **Inicio** y, después, agregue la ruta de acceso y el nombre completo de la aplicación que realiza la llamada en el campo **Ejecutable**.

1. Agregue los argumentos de línea de comandos necesarios en el campo **Argumentos de la línea de comandos** o **Argumentos de la aplicación**.

   ![Ventana Propiedades de depuración de C#](../debugger/media/dbg-debugging-properties-dll-csharp.png "Ventana Propiedades de depuración de C#")

1. Use **Archivo** > **Guardar elementos seleccionados** o presione **Ctrl**+**S** para guardar los cambios.

## <a name="debug-from-the-dll-project"></a>Depuración desde el proyecto DLL

1. Establezca puntos de interrupción en el proyecto de DLL.

1. Haga clic con el botón derecho en el proyecto de DLL y seleccione **Establecer como proyecto de inicio**.

1. Asegúrese de que el campo **Configuración de soluciones** está establecido en **Depuración**. Presione **F5**, haga clic en la flecha **Iniciar** de color verde o seleccione **Depurar** > **Iniciar depuración**.

Sugerencias adicionales:

- Si la depuración no alcanza los puntos de interrupción, asegúrese de que la salida del archivo DLL (de forma predeterminada, la carpeta *\<project>\Debug*) es la ubicación a la que llama la aplicación que realiza la llamada.

- Si quiere interrumpir el código en una aplicación de llamada administrada desde un archivo DLL nativo, o viceversa, habilite la [depuración en modo mixto](../debugger/how-to-debug-in-mixed-mode.md).

- En algunos escenarios, puede que tenga que indicar al depurador dónde encontrar el código fuente. Para más información, consulte [Uso de las páginas No se cargaron símbolos o No se cargaron orígenes](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#use-the-no-symbols-loadedno-source-loaded-pages).

## <a name="see-also"></a>Vea también
- [Depuración de proyectos DLL](../debugger/debugging-dll-projects.md)
- [Configuración de proyectos para configuraciones de depuración en C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
