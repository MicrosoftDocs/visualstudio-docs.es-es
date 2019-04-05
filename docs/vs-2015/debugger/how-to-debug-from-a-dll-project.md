---
title: Filtrar Depurar desde un proyecto DLL | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4a9a3e7cd63e5a485063789d9f9eeaf1227d1b5d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996788"
---
# <a name="how-to-debug-from-a-dll-project"></a>Filtrar Depurar desde un proyecto DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para iniciar la depuración de un proyecto DLL, es necesario especificar la aplicación que llama en las propiedades del proyecto. Las páginas de propiedades de C++ difieren en diseño y contenido de las páginas de propiedades de C# y Visual Basic.  
  
 Si se llama a un DLL administrado mediante código nativo y desea realizar la depuración en ambos elementos, puede especificarlo en las propiedades del proyecto. Para obtener más información, vea [Cómo: Depurar en modo mixto](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
>  No se puede especificar una aplicación externa que realiza la llamada en las ediciones Express de Visual Studio. En su lugar, agregue un proyecto ejecutable a la solución, establézcalo como proyecto de inicio y llame a los métodos del archivo DLL desde el proyecto ejecutable.  
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>Para especificar la aplicación que realiza la llamada en un proyecto de C++  
  
1.  Haga clic en el nodo del proyecto en el **el Explorador de soluciones** y seleccione **propiedades**. Vaya a la **depurar** ficha.  
  
2.  Asegúrese de que el campo **Configuración** que hay en la parte superior de la ventana esté establecido en **Depurar**.  
  
3.  Vaya a **propiedades de configuración / depuración**.  
  
4.  En el **depurador para iniciar** elija **depurador Local de Windows** o **depurador remoto de Windows**.  
  
5.  En el **comando** o **comando remoto** , agregue el nombre de ruta de acceso completa de la aplicación.  
  
6.  Agregue los argumentos de programa necesarios en el cuadro **Argumentos de comandos**.  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>Para especificar la aplicación que realiza la llamada en un proyecto de C# o de Visual Basic  
  
1.  Haga clic en el nodo del proyecto en el **el Explorador de soluciones** y seleccione **propiedades**. Vaya a la **depurar** ficha.  
  
     Seleccione **iniciar programa externo**y agregue el nombre de ruta de acceso completa del programa para ejecutar.  
  
     Si necesita agregar argumentos de línea de comandos del programa externo, agréguelas en el **argumentos de línea de comandos** campo.  
  
2.  También se puede llamar a una aplicación como una dirección URL. (Esto es útil cuando depura un archivo DLL administrado por una aplicación ASP.NET local.)  
  
     En **acción de inicio**, seleccione el **Iniciar explorador con la dirección URL:** botón de radio y rellene la dirección URL.  
  
### <a name="to-start-debugging-from-the-dll-project"></a>Para iniciar la depuración del proyecto DLL  
  
1.  Establezca los puntos de interrupción según sea necesario.  
  
2.  Iniciar la depuración (presione F5, haga clic en la flecha verde o haga clic en **depurar / Iniciar depuración**).  
  
## <a name="see-also"></a>Vea también  
 [Depuración de proyectos DLL](../debugger/debugging-dll-projects.md)   
 [Configuración de proyectos para configuraciones de depuración en C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
