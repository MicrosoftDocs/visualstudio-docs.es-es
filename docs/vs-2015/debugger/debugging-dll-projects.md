---
title: Depurar proyectos DLL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c5177d7bd43a0bc1ba29778ba99cc891fd9f739b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792390"
---
# <a name="debugging-dll-projects"></a>Depurar proyectos DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las plantillas siguientes crean archivos DLL:  
  
- (C++, C# y Visual Basic): Biblioteca de clases  
  
- (C++, C# y Visual Basic): Biblioteca de controles de formularios Windows Forms  
  
   Depurar una biblioteca de controles de Windows es similar a depurar un proyecto de biblioteca de clases. En la mayoría de los casos, el control de Windows se llama desde otro proyecto. Cuando se depura el proyecto que hace la llamada, se puede ejecutar paso a paso el código del control de Windows, establecer puntos de interrupción y realizar otras operaciones de depuración. Para obtener más información, vea [Controles de formularios Windows Forms](http://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a).  
  
- (C# y Visual Basic): Biblioteca de controles web  
  
   Para obtener más información, consulta [Web Control Library (Managed Code)](../debugger/web-control-library-managed-code.md).  
  
- (C++): Control ActiveX MFC y Control ActiveX de Smart Device MFC  
  
   Los controles ActiveX son controles que se pueden descargar a través de Internet en un equipo cliente, y se pueden mostrar y activar en páginas web.  
  
   Depurar estos controles es similar a depurar otros tipos de controles ya que no pueden ejecutarse como independientes, sino que deben incrustarse en una página web HTML. Para obtener más información, consulta [How to: Debug an ActiveX Control](../debugger/how-to-debug-an-activex-control.md).  
  
- (C++): Archivo DLL MFC de Smart Device  
  
   Para obtener más información, consulta [MFC Debugging Techniques](../debugger/mfc-debugging-techniques.md).  
  
  Esta sección también contiene información sobre los temas siguientes:  
  
- [Cómo: Depurar desde un proyecto DLL](../debugger/how-to-debug-from-a-dll-project.md)  
  
- [Cómo: Depurar en modo mixto](../debugger/how-to-debug-in-mixed-mode.md)  
  
  En este tema se incluyen las siguientes secciones, que tratan consideraciones relativas a la preparación de la depuración de bibliotecas de clases:  
  
- [Building a Debug Version](#vxtskdebuggingdllprojectsbuildingadebugversion)  
  
- [Mixed-Mode Debugging](#vxtskdebuggingdllprojectsmixedmodedebugging)  
  
- [Changing Default Configurations](#vxtskdebuggingdllprojectschangingdefaultconfigurations)  
  
- [Maneras de depurar la DLL](#vxtskdebuggingdllprojectswaystodebugthedll)  
  
- [The Calling Application](#vxtskdebuggingdllprojectsthecallingapplication)  
  
- [Controls on a Web Page](#vxtskdebuggingdllprojectscontrolsonawebpage)  
  
- [The Immediate Window](#vxtskdebuggingdllprojectstheimmediatewindow)  
  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Creación de una versión de depuración  
 Cualquiera que sea la forma en la que inicia la depuración, primero debe asegurarse de compilar la versión de depuración del archivo DLL y, después, de que dicha versión está en la ubicación donde la aplicación espera encontrarla. Esto puede parecer una obviedad pero, si olvida este paso, la aplicación podría encontrar y cargar una versión diferente del archivo DLL. Después el programa continuará ejecutándose mientras se pregunta por qué nunca se visitó el punto de interrupción. Durante la depuración, para comprobar qué archivos DLL ha cargado el programa, abra la ventana **Módulos** del depurador. La ventana **Módulos** muestra cada uno de los archivos DLL o EXE cargados en el proceso que se depura. Para obtener más información, consulta [How to: Use the Modules Window](../debugger/how-to-use-the-modules-window.md).  
  
 Para que el depurador se asocie al código escrito en C++, el código debe emitir `DebuggableAttribute`. Puede agregar este atributo automáticamente al código vinculando con la opción [/ASSEMBLYDEBUG](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) del vinculador.  
  
##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Mixed-Mode Debugging  
 La aplicación que realiza la llamada a la DLL puede estar escrita en código administrado o en código nativo. Si el código nativo llama a la DLL administrada y se desea depurar ambos, deben habilitarse los depuradores administrados y nativos. Se puede seleccionar esta opción en el  **\<proyecto > páginas de propiedades** cuadro de diálogo o ventana. La forma de hacerlo depende de si inicia la depuración desde el proyecto DLL o desde el proyecto de la aplicación que hace la llamada. Para obtener más información, consulta [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md).  
  
##  <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Changing Default Configurations  
 Cuando se crea un proyecto de aplicación de consola con la plantilla de proyecto, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crea automáticamente la configuración requerida para las configuraciones Debug y Release. Si fuera necesario, puede cambiar esa configuración. Para obtener más información, consulte [configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [configuración del proyecto para configuraciones de depuración de C#](../debugger/project-settings-for-csharp-debug-configurations.md), [configuración del proyecto para una configuración de depuración de Visual Basic ](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), y [Cómo: establecer configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md).  
  
##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Maneras de depurar la DLL  
 Cada uno de los proyectos de esta sección crea un archivo DLL. No es posible ejecutar un archivo DLL directamente; se debe utilizar una aplicación para llamarlo, normalmente un archivo EXE. Para obtener más información, consulta [Creating and Managing Visual C++ Projects](http://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047). La aplicación que realiza la llamada podría ajustarse a cualquiera de los criterios siguientes:  
  
-   Una aplicación integrada en otro proyecto de la misma solución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que contiene la biblioteca de clases.  
  
-   Una aplicación existente ya implementada en un equipo de pruebas o de producción.  
  
-   Ubicada en Internet y accesible mediante una dirección URL.  
  
-   Una aplicación web que contiene una página web que incrusta el archivo DLL.  
  
###  <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Depurar la aplicación que hace la llamada  
 Para depurar un archivo DLL, comience por depurar la aplicación que realiza la llamada, que por lo general es un archivo EXE o una aplicación Web. Hay varias formas de hacerlo.  
  
- Si tiene un proyecto para la aplicación que hace la llamada, ábralo e inicie la ejecución desde el menú **Depurar** . Para obtener más información, consulta [How to: Start Execution](http://msdn.microsoft.com/en-us/b0fe0ce5-900e-421f-a4c6-aa44ddae453c).  
  
- Si la aplicación que realiza la llamada es un programa existente, implementado en un equipo de pruebas o de producción que ya está en ejecución, asócielo a él. Utilice este método si el archivo DLL es un control hospedado en Internet Explorer o un control de una página Web. Para obtener más información, consulta [How to: Attach to a Running Process](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).  
  
- Puede depurarlo desde el proyecto DLL. Para obtener más información, consulta [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md).  
  
- Puede depurarlo desde la ventana [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Immediate** window. En este caso, la ventana **Inmediato** realiza el rol de la aplicación.  
  
  Antes de iniciar la depuración de la aplicación que hace la llamada, normalmente es conveniente establecer un punto de interrupción en la biblioteca de clases. Para obtener más información, consulta [Breakpoints and Tracepoints](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583). Cuando se visita el punto de interrupción, se puede ejecutar paso a paso el código y observar la acción en cada línea hasta aislar el problema. Para obtener más información, consulta [Code Stepping Overview](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9).  
  
###  <a name="vxtskdebuggingdllprojectscontrolsonawebpage"></a> Controles de una página Web  
 Para depurar un control de una página web, cree una página de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] que lo incruste si dicha página aún no existe. Luego, coloque los puntos de interrupción en el código de la página web, así como el código de control. A continuación, invoque la página Web desde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Antes de iniciar la depuración de la aplicación que hace la llamada, normalmente es conveniente establecer un punto de interrupción en el archivo DLL. Cuando se visita el punto de interrupción, se puede ejecutar paso a paso el código y observar la acción en cada línea hasta aislar el problema. Para obtener más información, consulta [Breakpoints and Tracepoints](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> The Immediate Window  
 Puede evaluar funciones o métodos en el archivo DLL sin necesidad de que una aplicación realice la llamada. Efectúe una depuración en tiempo de diseño y utilice la ventana **Inmediato** . Para depurar de esta manera, siga estos pasos mientras el proyecto DLL está abierto:  
  
1.  Abra la ventana **Inmediato** del depurador.  
  
2.  Para probar un método denominado `Test` en la clase `Class1`, cree instancias de un objeto de tipo `Class1` escribiendo el siguiente código de C# en la ventana Inmediato. Este código administrado funciona para Visual Basic y C++, con los cambios de sintaxis adecuados:  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     En C#, todos los nombres deben estar completos. Además, cualquier método o variable debe estar en el ámbito y contexto actual de la sesión de depuración.  
  
3.  Suponiendo que `Test` acepte un parámetro `int` , evalúe `Test` mediante la ventana **Inmediato** :  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     El resultado se imprimirá en la ventana **Inmediato** .  
  
4.  Para continuar la depuración de `Test` , coloque un punto de interrupción dentro de ella y evalúe nuevamente la función:  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     Se llegará al punto de interrupción y podrá recorrer `Test`. Después de que la ejecución sale de `Test`, el depurador regresa al modo de diseño.  
  
## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Tipos de proyecto de Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Configuración de proyectos para configuraciones de depuración en C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)



