---
title: "Solucionar problemas de referencias rotas | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "hacer referencia a componentes, solucionar problemas"
  - "hacer referencia a archivos desde proyectos"
  - "solución de problemas de referencias"
  - "proyectos de Visual Basic, referencias"
  - "proyectos de Visual C#, referencias"
ms.assetid: 00a9ade9-652e-40de-8ada-85f63cd183ee
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Solucionar problemas de referencias rotas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si la aplicación intenta utilizar una referencia rota, se generará un error de excepción.  La incapacidad para encontrar el componente al que se hace referencia es el desencadenador principal del error, pero hay varias situaciones en las cuales una referencia puede considerarse rota.  La lista siguiente muestra estas circunstancias:  
  
-   La ruta de acceso a la referencia del proyecto es incorrecta o está incompleta.  
  
-   El archivo al que se hace referencia se eliminó.  
  
-   El archivo al que se hace referencia cambió de nombre.  
  
-   Se ha producido un error de autenticación o conexión de red.  
  
-   Se ha realizado una referencia a un componente COM que no está instalado en equipo.  
  
 A continuación se indican las soluciones para estos problemas.  
  
> [!NOTE]
>  Se hace referencia a los archivos de los ensamblados mediante rutas absolutas en el archivo de proyectos.  Por ello, los usuarios pueden trabajar en un entorno de varios programadores al que le falte un ensamblado en su entorno local.  Para evitar estos errores, en estos casos, es preferible agregar referencias entre proyectos.  Para obtener más información, consulte [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) y [Programar con ensamblados](../Topic/Programming%20with%20Assemblies.md).  
  
## La ruta de acceso de referencia es incorrecta  
 Si se comparten los proyectos en equipos diferentes, es posible que no se encuentren algunas referencias, cuando un componente esté ubicado en un directorio diferente en cada equipo.  Las referencias se almacenan bajo el nombre del archivo de componente \(por ejemplo, MiComponente\).  Cuando se agrega una referencia a un proyecto, la ubicación de la carpeta del archivo de componentes \(por ejemplo, C:\\MisComponentes\\\) se agrega a la propiedad de proyecto **ReferencePath**.  
  
 Cuando se abre el proyecto, intenta encontrar estos archivos de componente a los que se hace referencia; buscando en los directorios de la ruta de acceso de referencia.  Si se abre en un equipo que almacene el componente en un directorio diferente, tal como D:\\MisComponentes\\, no podrá encontrarse la referencia y aparecerá un error en la Lista de tareas.  
  
 Para solucionar este problema, puede eliminar la referencia rota y, a continuación, reemplazarla mediante el cuadro de diálogo Agregar referencia.  Otra solución consiste en utilizar el elemento **Ruta de acceso de referencias** en las páginas de propiedades del proyecto y modificar las carpetas de la lista para que apunten a las ubicaciones correctas.  La propiedad **Ruta de acceso de referencias** se conserva para cada usuario en cada equipo.  Por consiguiente, modificar la ruta de acceso de referencias no afecta a los demás usuarios del proyecto.  
  
> [!TIP]
>  Las referencias entre proyectos no tienen estos problemas.  Por este motivo, se recomienda utilizarlas en lugar las referencias a archivos, siempre que sea posible.  
  
#### Para reparar una referencia del proyecto rota mediante la corrección de la ruta de acceso de referencias  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el nodo del proyecto y, a continuación, haga clic en **Propiedades**.  
  
2.  Aparece el **Diseñador de proyectos**.  
  
3.  Si está utilizando Visual Basic, selecciona la página **Referencias** y haga clic en el botón **Rutas de acceso de referencia**.  En el cuadro de diálogo **Rutas de referencia de acceso**, escriba la ruta de acceso de la carpeta que contiene el elemento al que desee hacer referencia en el campo **Carpeta** y haga clic en el botón **Agregar carpeta**.  
  
     O bien  
  
     Si está utilizando Visual C\#, seleccione la página **Rutas de acceso de referencia**.  En el campo **Carpeta**, escriba la ruta de acceso de la carpeta que contiene el elemento al que desea hacer referencia y, a continuación, haga clic en el botón **Agregar carpeta**.  
  
## El archivo al que se hace referencia se eliminó  
 Es posible que el archivo al que se hace referencia se haya eliminado y ya no exista en la unidad.  
  
#### Para reparar una referencia de proyecto rota a un archivo que ya no exista en la unidad  
  
-   Elimine la referencia.  
  
-   Si existe la referencia en otra ubicación del equipo, léala en esa ubicación.  
  
-   Para obtener más información, consulte [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## El archivo al que se hace referencia cambió de nombre  
 Es posible que el archivo al que se hace referencia haya cambiado de nombre.  
  
#### Para reparar una referencia rota de un archivo que cambió de nombre  
  
-   Elimine la referencia y, a continuación, agregue una referencia al archivo que ha cambiado de nombre.  
  
-   Si existe la referencia en otra ubicación del equipo, deberá leerla de esa ubicación.  Para obtener más información, consulte [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## Se ha producido un error de autenticación o conexión de red  
 Hay muchas causas posibles por las que no se pueda tener acceso a un archivo: un error en la conexión de red o una autenticación incorrecta, por ejemplo.  Cada causa puede tener un único medio de recuperación; por ejemplo, puede que tenga que ponerse en contacto con el administrador local para tener acceso a los recursos necesarios.  Sin embargo, siempre es una opción eliminar la referencia y reparar el código que la utilizaba.  Para obtener más información, consulte [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## El componente COM no está instalado en el equipo  
 Si un usuario ha agregado una referencia a un componente COM y un segundo usuario intenta ejecutar el código en un equipo que no tenga este componente instalado, el segundo usuario recibirá un error indicando que la referencia está rota.  El error se corregirá instalando el componente en el segundo equipo.  Para obtener más información sobre cómo utilizar las referencias a los componentes COM en los proyectos, consulte [Interoperabilidad COM en aplicaciones .NET Framework](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).  
  
## Vea también  
 [Introduction to the Project Designer](http://msdn.microsoft.com/es-es/898dd854-c98d-430c-ba1b-a913ce3c73d7)   
 [Página Referencias, Diseñador de proyectos \(Visual Basic\)](../ide/reference/references-page-project-designer-visual-basic.md)   
 [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)