---
title: "C&#243;mo: Depurar desde un proyecto DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "depurar [Visual Studio], DLL"
  - "depurar las DLL"
  - "DLL (proyectos), depurar"
  - "DLL, depurar proyectos"
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Depurar desde un proyecto DLL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para iniciar la depuración de un proyecto DLL, es necesario especificar la aplicación que llama en las propiedades del proyecto.  Las páginas de propiedades de C\+\+ difieren en diseño y contenido de las páginas de propiedades de C\# y Visual Basic.  
  
 Si se llama a un DLL administrado mediante código nativo y desea realizar la depuración en ambos elementos, puede especificarlo en las propiedades del proyecto.  Para obtener más información, consulte [Cómo: Depurar en modo mixto](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
>  No se puede especificar una aplicación externa que realiza la llamada en las ediciones Express de Visual Studio.  En su lugar, agregue un proyecto ejecutable a la solución, establézcalo como proyecto de inicio y llame a los métodos del archivo DLL desde el proyecto ejecutable.  
  
### Para especificar la aplicación que realiza la llamada en un proyecto de C\+\+  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto y seleccione **Propiedades**.  Vaya a la pestaña **Depurar**.  
  
2.  Asegúrese de que el campo **Configuración** que hay en la parte superior de la ventana esté establecido en **Depurar**.  
  
3.  Vaya a **Propiedades de configuración \> Depuración**.  
  
4.  En la lista **Depurador para iniciar**, elija **Depurador local de Windows** o **Depurador remoto de Windows**.  
  
5.  En el cuadro **Comando**  o **Comando remoto**, agregue el nombre completo de la ruta de acceso de la aplicación.  
  
6.  Agregue los argumentos de programa necesarios en el cuadro **Argumentos de comandos**.  
  
### Para especificar la aplicación que realiza la llamada en un proyecto de C\# o de Visual Basic  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto y seleccione **Propiedades**.  Vaya a la pestaña **Depurar**.  
  
     Seleccione **Programa externo de inicio** y agregue el nombre completo de la ruta de acceso del programa para ejecutarlo.  
  
     Si necesita agregar los argumentos de la línea de comandos de un programa externo, hágalo en el campo **Argumentos de la línea de comandos**.  
  
2.  También se puede llamar a una aplicación como una dirección URL.  \(Esto es útil cuando depura un archivo DLL administrado por una aplicación ASP.NET local.\)  
  
     En **Acción de inicio**, seleccione el botón de radio **Iniciar explorador con la dirección URL:** y escriba la dirección URL.  
  
### Para iniciar la depuración del proyecto DLL  
  
1.  Establezca los puntos de interrupción según sea necesario.  
  
2.  Inicie la depuración \(presione F5, haga clic en la flecha verde o haga clic en **Depurar \> Iniciar depuración**\).  
  
## Vea también  
 [Depurar proyectos DLL](../debugger/debugging-dll-projects.md)   
 [Configuración del proyecto para configuraciones de depuración en C\#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración del proyecto para una configuración de depuración de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Configuración del proyecto para una configuración de depuración de C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)