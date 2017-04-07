---
title: Opciones, editor de texto, C/C++, experimental | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: e9a05d008f671fb79d6813a14c594b82f27697e3
ms.openlocfilehash: 780c643c25f0d43ec0564e43bc50d2f36f1aee79
ms.lasthandoff: 03/27/2017

---
# <a name="options-text-editor-cc-experimental"></a>Opciones, editor de texto, C/C++, experimental
Al cambiar estas opciones, puede modificar el comportamiento relacionado con IntelliSense y la base de datos de exploración cuando programa en C o C++. Estas características son experimentales y se pueden modificar o quitar de Visual Studio en una versión futura.  
  
 Para tener acceso a esta página, en el cuadro de diálogo **Opciones** , en el panel izquierdo, expanda **Editor de texto**, expanda **C/C++**y luego haga clic en **Experimental**.  

 Estas características están disponibles en una instalación de Visual Studio 2017.  
  
> [!NOTE]
>  Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Vea [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="enable-predictive-intellisense"></a>Habilitar Intellisense predictivo
IntelliSense predictivo limita el número de resultados que se muestran en la lista desplegable de IntelliSense para que vea únicamente los resultados que son relevantes en el contexto. Por ejemplo, si escribe <code>int x =</code> e invoca la lista desplegable de IntelliSense, solo verá números enteros o funciones que devuelven enteros. IntelliSense predictivo está desactivado de forma predeterminada.

## <a name="enable-faster-project-load"></a>Habilitar la carga de proyectos más rápida
Esta opción habilita la característica conocida como "carga de solución ligera". Cuando la carga de solución ligera está habilitada, Visual Studio no carga totalmente los proyectos hasta que son realmente necesarios. Muchas tareas comunes, como navegar por el código base, editar código y compilar proyectos, no requieren que se cargue el proyecto. Cuando esta opción está habilitada, puede empezar a realizar estas tareas comunes más rápidamente, sin tener que esperar a que se cargue el proyecto.  

## <a name="additional-features-in-the-visual-studio-gallery"></a>Características adicionales de la Galería de Visual Studio
Para conocer las características adicionales del editor de texto de la Galería de Visual Studio, consulte la lista [aquí](http://go.microsoft.com/fwlink/?LinkId=692016). Un ejemplo es [C++ Quick Fixes](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f), que admite lo siguiente:  
  
-   **Agregar #include faltante** : sugiere las directivas #include pertinentes para símbolos desconocidos en el código  
  
-   **Agregar mediante espacio de nombres o símbolo completo** : similar al elemento anterior, pero para espacios de nombres  
  
-   **Agregar el punto y coma que falta**  
  
-   **Ayuda de MSDN** : buscar en MSDN los mensajes de error  
  
 Puede mantener el puntero sobre una línea ondulada para obtener una bombilla, o bien use el método abreviado de teclado predeterminado CTRL+punto (Ctrl+.). Tenga en cuenta que en el caso del método abreviado de teclado, no es necesario situar el símbolo de intercalación en el error o token específico. Simplemente puede estar en la misma línea que el error para invocar sugerencias para cualquier elemento incluido en esa línea.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del editor específicas del lenguaje](../../ide/reference/setting-language-specific-editor-options.md)   
 [Refactorización en C++ (Blog de VC)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)

