---
title: "C&#243;mo: Depurar un archivo ejecutable que no es parte de una soluci&#243;n de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurar [Visual Studio], ejecutables"
  - "archivos ejecutables, depurar fuera de los proyectos"
  - "archivos ejecutables, importar"
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# C&#243;mo: Depurar un archivo ejecutable que no es parte de una soluci&#243;n de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Es posible que haya ocasiones en las que desee depurar un archivo ejecutable que no forme parte de un proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Puede tratarse de un archivo ejecutable que se haya creado fuera de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o de un archivo ejecutable que haya recibido de otra persona.  
  
 La solución habitual a este problema consiste en iniciar el archivo ejecutable fuera de Visual Studio y asociarlo mediante el depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Para obtener más información, vea[Crear asociaciones con procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 La asignación a una aplicación requiere algunos pasos que deben realizarse manualmente, por lo que necesitan algunos segundos.  Este ligero retraso significa que la asignación no será la solución si se está intentando depurar un problema que se produce durante el inicio.  Además, si se depura un programa que no espera que el usuario proporcione datos y finaliza rápidamente, puede que no tenga tiempo de asociar el archivo al programa.  En caso de que tenga instalado [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], podrá crear un proyecto EXE para este tipo de programa.  
  
### Para crear un proyecto .EXE para un archivo ejecutable existente  
  
1.  En el menú **Archivo**, haga clic en **Abrir** y seleccione **Proyecto**.  
  
2.  En el cuadro de diálogo **Abrir proyecto**, haga clic en la lista desplegable situada junto al cuadro de **Nombre de archivo** y seleccione **Todos los archivos de proyecto**.  
  
3.  Busque el archivo ejecutable y haga clic en **Aceptar**.  
  
     De esta manera creará una solución temporal que contiene el archivo ejecutable.  
  
### Para importar una archivo ejecutable a una solución de Visual Studio  
  
1.  En el menú **Archivo**, elija **Agregar proyecto** y, a continuación, haga clic en **Proyecto existente**.  
  
2.  En el cuadro de diálogo **Agregar proyecto existente**, haga clic en la lista desplegable situada junto al cuadro de **Nombre de archivo** y seleccione **Todos los archivos de proyecto**.  
  
3.  Busque y seleccione el archivo ejecutable.  
  
4.  Haga clic en **Aceptar**.  
  
5.  Inicie el archivo ejecutable mediante la elección de un comando de ejecución, como **Iniciar**, en el menú **Depurar**.  
  
    > [!NOTE]
    >  No todos los lenguajes de programación admiten proyectos EXE.  Si necesita utilizar esta característica, instale [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].  
  
     Cuando se depura un archivo ejecutable sin el código fuente, las características de depuración disponibles son limitadas, tanto si se asocia el depurador al archivo en ejecución como si se agrega el archivo ejecutable a una solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Si el archivo ejecutable se compiló sin información de depuración en un formato compatible, las características disponibles serán aún más limitadas.  Si dispone del código fuente, lo más recomendable es que importe dicho código a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y que cree una versión de depuración del archivo ejecutable en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Vea también  
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [DBG Files](http://msdn.microsoft.com/es-es/91e449e9-8b65-4123-960f-2107cd1f1cfd)