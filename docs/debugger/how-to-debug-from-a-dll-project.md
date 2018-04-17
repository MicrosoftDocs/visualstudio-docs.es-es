---
title: 'Cómo: depurar desde un proyecto DLL | Documentos de Microsoft'
ms.custom: ''
ms.date: 05/24/2017
ms.technology:
- vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 903723616b55467a49c43986ccd6df63dea71491
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio"></a>Cómo: depurar desde un proyecto DLL en Visual Studio
Es una manera de depurar un proyecto DLL especificar la aplicación que realiza la llamada en las propiedades del proyecto del proyecto de DLL y, a continuación, puede iniciar la depuración desde el propio proyecto DLL. Para que funcione este método, la aplicación debe llamar a la DLL y el archivo DLL debe estar en la ubicación donde la aplicación espera encontrarla (en caso contrario, la aplicación podría encontrar una versión diferente del archivo DLL y cargarla en su lugar, y que no ejecute los puntos de interrupción). Para otros métodos de depuración de archivos DLL, consulte [depurar proyectos DLL](../debugger/debugging-dll-projects.md).
  
Si se llama a un DLL administrado mediante código nativo y desea realizar la depuración en ambos elementos, puede especificarlo en las propiedades del proyecto. Para obtener más información, consulta [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md).   

Las páginas de propiedades de C++ difieren en diseño y contenido de las páginas de propiedades de C# y Visual Basic. 
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>Para especificar la aplicación que realiza la llamada en un proyecto de C++  
  
1.  Haga clic en el nodo de proyecto en el **el Explorador de soluciones** y seleccione **propiedades**.  
  
2.  Asegúrese de que el **configuración** campo en la parte superior de la ventana está establecido en **depurar**. 

    A **depurar** configuración es necesaria para este método. 
  
3.  Vaya a **propiedades de configuración > depuración**.  
  
4.  En el **depurador para iniciar** elija **depurador Local de Windows** o **depurador remoto de Windows**.  
  
5.  En el **comando** o **comando remoto** , agregue el nombre de ruta de acceso completa de la aplicación que realiza la llamada (por ejemplo, un archivo .exe).

    ![Ventana de propiedades de depuración](../debugger/media/dbg-debugging-properties-dll.png "DebuggingPropertiesWindow")  
  
6.  Agregue los argumentos de programa necesarios en el **argumentos del comando** cuadro.  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>Para especificar la aplicación que realiza la llamada en un proyecto de C# o de Visual Basic  
  
1.  Haga clic en el nodo de proyecto en el **el Explorador de soluciones** y seleccione **propiedades**y, a continuación, seleccione la **depurar** ficha.

2.  Asegúrese de que el **configuración** campo en la parte superior de la ventana está establecido en **depurar**.

3.  (.NET framework) Seleccione **iniciar programa externo**y agregue el nombre de ruta de acceso completa de la aplicación que realiza la llamada.

4.  (.NET core) Seleccione **ejecutable** desde el **iniciar** lista y, a continuación, agregue el nombre de ruta de acceso completa de la aplicación que realiza la llamada en el **ejecutable** campo. 
  
     Si tiene que agregar argumentos de línea de comandos del programa externo, agregarlos en el **argumentos de línea de comandos** (o **argumentos de la aplicación**) campo.

    ![Ventana de propiedades de depuración](../debugger/media/dbg-debugging-properties-dll-csharp.png "DebuggingPropertiesWindow") 

5.  Si es necesitan, también puede llamar a una aplicación como una dirección URL. (Esto es útil cuando depura un archivo DLL administrado por una aplicación ASP.NET local.)  
  
     En **acción de inicio**, seleccione la **Iniciar explorador con la dirección URL:** botón de radio y escriba la dirección URL.
  
### <a name="to-start-debugging-from-the-dll-project"></a>Para iniciar la depuración del proyecto DLL  
  
1.  Establecer puntos de interrupción en el proyecto DLL. 

2.  Haga clic en el proyecto DLL y elija **establecer como proyecto de inicio**. 

    (Además, asegúrese de que el **configuración de soluciones** campo todavía está establecido en **depurar**.)   
  
3.  Iniciar la depuración (presione F5, haga clic en la flecha verde o haga clic en **Depurar > Iniciar depuración**).

    Se alcanzarán los puntos de interrupción en el archivo DLL. Si no es capaz de establecer los puntos de interrupción, asegúrese de que el archivo DLL de salida (de forma predeterminada, el **project\Debug** carpeta) está en una ubicación que la aplicación que realiza la llamada espera encontrarla.
  
## <a name="see-also"></a>Vea también  
 [Depurar proyectos DLL](../debugger/debugging-dll-projects.md)   
 [Configuración de proyectos para configuraciones de depuración en C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)