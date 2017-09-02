---
title: Opciones, editor de texto, C/C++, experimental | Microsoft Docs
ms.custom: 
ms.date: 08/02/2017
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
ms.translationtype: HT
ms.sourcegitcommit: 8a544bd1e1242bb6fabe00f7842ac33ed9d9d444
ms.openlocfilehash: 1677db7d5af93db8a378d598332e6a6d52f09bdd
ms.contentlocale: es-es
ms.lasthandoff: 08/14/2017

---
# <a name="options-text-editor-cc-experimental"></a>Opciones, editor de texto, C/C++, experimental
Al cambiar estas opciones, puede modificar el comportamiento relacionado con IntelliSense y la base de datos de exploración cuando programa en C o C++. Estas características son experimentales y se pueden modificar o quitar de Visual Studio en una versión futura. En este tema se describen las opciones de Visual Studio 2017. En el caso de Visual Studio 2015, consulte [Opciones, editor de texto, C/C++, Experimental](https://msdn.microsoft.com/library/mt591979.aspx). 
  
 Para acceder a esta página de propiedades, pulse **Ctrl+Q** para activar `Quick Launch` y, después, escriba "experimental". La función Inicio rápido encontrará la página después de las primeras letras. También puede acceder a ella eligiendo **Herramientas | Opciones** y expandiendo **Editor de texto**. Después, elija **C/C++** y **Experimental**.  

 Estas características están disponibles en una instalación de Visual Studio 2017.  
  
> [!NOTE]
>  Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="enable-predictive-intellisense"></a>Habilitar Intellisense predictivo
IntelliSense predictivo limita el número de resultados que se muestran en la lista desplegable de IntelliSense para que vea únicamente los resultados que son relevantes en el contexto. Por ejemplo, si escribe <code>int x =</code> e invoca la lista desplegable de IntelliSense, solo verá números enteros o funciones que devuelven enteros. IntelliSense predictivo está desactivado de forma predeterminada.

## <a name="enable-faster-project-load"></a>Habilitar la carga de proyectos más rápida 
**Visual Studio 2017 versión 15.3 y posteriores**: esta característica ahora se denomina **Habilitar almacenamiento en caché de los proyectos** y se ha movido a la página de propiedades [Configuración de proyecto de VC++](vcpp-project-settings-projects-and-solutions-options-dialog-box.md).
Esta opción permite que Visual Studio copie en caché los datos de un proyecto para que, cuando lo abra la próxima vez, se carguen esos datos en lugar de volver a calcularlos desde los archivos de proyecto. Usar datos en caché puede acelerar de forma significativa el tiempo de carga de un proyecto.  

## <a name="additional-features-in-the-visual-studio-gallery"></a>Características adicionales de la Galería de Visual Studio
Para conocer las características adicionales del editor de texto de la Galería de Visual Studio, consulte la lista [aquí](http://go.microsoft.com/fwlink/?LinkId=692016). Un ejemplo es [C++ Quick Fixes](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f), que admite lo siguiente:  
  
-   **Agregar #include faltante** : sugiere las directivas #include pertinentes para símbolos desconocidos en el código  
  
-   **Agregar mediante espacio de nombres o símbolo completo** : similar al elemento anterior, pero para espacios de nombres  
  
-   **Agregar punto y coma faltante**  
  
-   **Ayuda de MSDN** : buscar en MSDN los mensajes de error  
  
 Puede mantener el puntero sobre una línea ondulada para obtener una bombilla, o bien use el método abreviado de teclado predeterminado CTRL+punto (Ctrl+.). Tenga en cuenta que en el caso del método abreviado de teclado, no es necesario situar el símbolo de intercalación en el error o token específico. Simplemente puede estar en la misma línea que el error para invocar sugerencias para cualquier elemento incluido en esa línea.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del editor específicas del lenguaje](../../ide/reference/setting-language-specific-editor-options.md)   
 [Refactorización en C++ (Blog de VC)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)

