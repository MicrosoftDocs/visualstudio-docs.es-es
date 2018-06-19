---
title: Opciones, editor de texto, C/C++, experimental
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: 36826a998c579526487b440ebe9d3ddab228daab
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945976"
---
# <a name="options-text-editor-cc-experimental"></a>Opciones, editor de texto, C/C++, experimental

Al cambiar estas opciones, puede modificar el comportamiento relacionado con IntelliSense y la base de datos de exploración cuando programa en C o C++. Estas características son experimentales y se pueden modificar o quitar de Visual Studio en una versión futura. En este tema se describen las opciones de Visual Studio 2017. En el caso de Visual Studio 2015, consulte [Opciones, editor de texto, C/C++, Experimental](https://msdn.microsoft.com/library/mt591979.aspx).

Para acceder a esta página de propiedades, pulse **Ctrl+Q** para activar `Quick Launch` y, después, escriba "experimental". La función Inicio rápido encontrará la página después de las primeras letras. También puede acceder a ella eligiendo **Herramientas | Opciones** y expandiendo **Editor de texto**. Después, elija **C/C++** y **Experimental**.

Estas características están disponibles en una instalación de Visual Studio 2017.

> [!NOTE]
> Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Habilitar IntelliSense predictivo

IntelliSense predictivo limita el número de resultados que se muestran en la lista desplegable de IntelliSense para que vea únicamente los resultados que son relevantes en el contexto. Por ejemplo, si escribe <code>int x =</code> e invoca la lista desplegable de IntelliSense, solo verá números enteros o funciones que devuelven enteros. IntelliSense predictivo está desactivado de forma predeterminada.

## <a name="enable-faster-project-load"></a>Habilitar la carga de proyectos más rápida

**Visual Studio 2017 versión 15.3 y posteriores**: esta característica ahora se denomina **Habilitar almacenamiento en caché de los proyectos** y se ha movido a la página de propiedades [Configuración de proyecto de VC++](vcpp-project-settings-projects-and-solutions-options-dialog-box.md).
Esta opción permite que Visual Studio copie en caché los datos de un proyecto para que, cuando lo abra la próxima vez, se carguen esos datos en lugar de volver a calcularlos desde los archivos de proyecto. Usar datos en caché puede acelerar de forma significativa el tiempo de carga de un proyecto.

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Características adicionales de Visual Studio Marketplace

Puede examinar las características adicionales del editor de texto en [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads). Un ejemplo es [C++ Quick Fixes](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017), que admite lo siguiente:

- **Agregar #include faltante** : sugiere las directivas #include pertinentes para símbolos desconocidos en el código

- **Agregar mediante espacio de nombres o símbolo completo** : similar al elemento anterior, pero para espacios de nombres

- **Agregar punto y coma faltante**

- **Ayuda en pantalla**: buscar ayuda en línea para los mensajes de error

- Y mucho más...

## <a name="see-also"></a>Vea también

- [Opciones del editor específicas del lenguaje](../../ide/reference/setting-language-specific-editor-options.md)
- [Refactorización en C++ (Blog de VC)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
