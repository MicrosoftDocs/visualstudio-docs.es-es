---
title: "C&#243;mo: Depurar c&#243;digo insertado | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.injected"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "lenguaje ensamblador, ver"
  - "depurar [C++], habilitar la anotación del código fuente"
  - "depurar [C++], código insertado"
  - "depurar [C++], utilizar atributos"
  - "depurar [C++], ver código de ensamblado"
  - "código desensamblador, depurar"
  - "código insertado"
  - "Mostrar código fuente (comando) [depurador]"
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Depurar c&#243;digo insertado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar su configuración, elija la opción Importar y exportar configuraciones del menú Herramientas.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 El uso de atributos puede simplificar enormemente la programación en C\+\+.  Para obtener más información, vea [Concepts](/visual-cpp/windows/attributed-programming-concepts).  El compilador se encarga de interpretar directamente algunos atributos.  Otros atributos insertan código en el archivo de código fuente del programa, que el compilador se encarga entonces de compilar.  Este código insertado facilita la programación al reducir la cantidad de código que se debe escribir.  Sin embargo, a veces un error puede hacer que la aplicación no funcione correctamente mientras se ejecuta el código insertado.  En estos casos, debería examinarse el código insertado.  Visual Studio proporciona dos modos de examinar el código insertado.  
  
-   Puede ver el código insertado en la ventana **Desensamblado**.  
  
-   Mediante [\/Fx](/visual-cpp/build/reference/fx-merge-injected-code), se puede crear un archivo de código fuente combinado que contiene código original e insertado.  
  
 La ventana **Desensamblado** muestra instrucciones en lenguaje de ensamblado que corresponden al código fuente y al código insertado por los atributos.  Además, la ventana **Desensamblado** puede mostrar la anotación del código fuente.  
  
### Para activar la anotación del código fuente  
  
-   Haga clic con el botón secundario del mouse en la ventana **Desensamblado** y elija **Mostrar código fuente** en el menú contextual.  
  
     Si conoce la ubicación de un atributo en una ventana de código fuente, puede utilizar el menú contextual para buscar el código insertado en la ventana **Desensamblado**.  
  
### Para ver el código insertado  
  
1.  El depurador debe hallarse en modo de interrupción.  
  
2.  En una ventana de código fuente, coloque el cursor delante de los atributos cuyo código insertado desea ver.  
  
3.  Haga clic con el botón secundario y seleccione **Ir al desensamblado** en el menú contextual.  
  
     Si la ubicación del atributo está cerca del punto de ejecución actual, puede seleccionar la ventana **Desensamblado** en el menú **Depurar**.  
  
### Para ver el código de desensamblado en el punto de ejecución actual  
  
1.  El depurador debe hallarse en modo de interrupción.  
  
2.  En el menú **Depurar**, elija **Ventanas** y, a continuación, haga clic en **Desensamblado**.  
  
## Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)