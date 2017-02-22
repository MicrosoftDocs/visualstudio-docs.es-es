---
title: "C&#243;mo: Agregar o quitar espacios de nombres importados (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "agregar espacios de nombres importados"
  - "espacios de nombres [Visual Studio]"
  - "espacios de nombres [Visual Studio], importados"
  - "referencias [Visual Studio], espacios de nombres importados"
  - "quitar espacios de nombres importados"
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Agregar o quitar espacios de nombres importados (Visual Basic)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La importación de un espacio de nombres permite utilizar elementos de ese espacio en el código sin necesidad de calificar totalmente el elemento.  Por ejemplo, si desea tener acceso al método `Create` de la clase `System.Messaging.MessageQueue`, puede importar el espacio de nombres `System.Messaging` y hacer referencia al elemento que necesita en el código como `MessageQueue.Create`.  
  
 Los espacios de nombres importados se administran en la página **Referencias** del **Diseñador de proyectos**.  Las importaciones que se especifiquen en este cuadro de diálogo se pasan directamente al compilador \(`/imports`\) y se aplican a todos los archivos del proyecto.  Use la instrucción `Imports` para utilizar un espacio de nombres en un único archivo de código fuente.  
  
### Para agregar un espacio de nombres importado  
  
1.  En el **Explorador de soluciones**, haga doble clic en el nodo **Mi proyecto** del proyecto.  
  
2.  En el **Diseñador de proyectos**, haga clic en la ficha **Referencias**.  
  
3.  En la lista **Espacios de nombres importados**, active la casilla del espacio de nombres que desea agregar.  
  
    > [!NOTE]
    >  Para poder importarse, el espacio de nombres debe estar en un componente al que se ha hecho referencia.  Si el espacio de nombres no aparece en la lista, tendrá que agregar una referencia al componente que lo contiene.  Para obtener más información, vea [Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
### Para quitar un espacio de nombres importado  
  
1.  En el **Explorador de soluciones**, haga doble clic en el nodo **Mi proyecto** del proyecto.  
  
2.  En el **Diseñador de proyectos**, haga clic en la ficha **Referencias**.  
  
3.  En la lista **Espacios de nombres importados**, desactive la casilla del espacio de nombres que desea quitar.  
  
## Importaciones de usuario  
 Las importaciones de usuario le permiten importar una clase determinada dentro de un espacio de nombres en lugar de importar todo el espacio de nombres.  Por ejemplo, puede que su aplicación tenga una importación para el espacio de nombres `Systems.Diagnostics`, pero la única clase de ese espacio de nombres que le interesa está en la clase `Debug`.  Puede definir `System.Diagnostics.Debug` como una importación de usuario y, después, quitar la importación para `System.Diagnostics`.  
  
 Si más tarde cambia de opinión y decide que realmente necesita la clase `EventLog`, puede especificar `System.Diagnostics.EventLog` como una importación de usuario y reemplazar `System.Diagnostics.Debug` mediante la funcionalidad de actualización.  
  
#### Para agregar una importación de usuario  
  
1.  En el **Explorador de soluciones**, haga doble clic en el nodo **Mi proyecto** del proyecto.  
  
2.  En el **Diseñador de proyectos**, haga clic en la ficha **Referencias**.  
  
3.  En el cuadro de texto que hay debajo de la lista **Espacios de nombres importados**, escriba el nombre completo del espacio de nombres que desea importar, incluyendo el espacio de nombres de la raíz.  
  
4.  Haga clic en el botón **Agregar importación del usuario** para agregar el espacio de nombres a la lista **Espacios de nombres importados**.  
  
    > [!NOTE]
    >  Se deshabilitará el botón **Agregar importación del usuario** si el espacio de nombres coincide con uno que ya existe en la lista; no puede agregar una importación dos veces.  
  
#### Para actualizar una importación de usuario  
  
1.  En el **Explorador de soluciones**, haga doble clic en el nodo **Mi proyecto** del proyecto.  
  
2.  En el **Diseñador de proyectos**, haga clic en la ficha **Referencias**.  
  
3.  En la lista **Espacios de nombres importados**, seleccione el espacio de nombres que desea cambiar.  
  
4.  En el cuadro de texto que hay debajo de la lista **Espacios de nombres importados**, escriba el nombre para el nuevo espacio de nombres.  
  
5.  Haga clic en el botón **Actualizar importación del usuario** para actualizar el espacio de nombres en la lista **Espacios de nombres importados**.  
  
## Vea también  
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)