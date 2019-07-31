---
title: Opciones, editor de texto, C/C++, experimental
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 75f36d66ea46e7a0474c3b76ae000f745337fc45
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461380"
---
# <a name="options-text-editor-cc-experimental"></a>Opciones, editor de texto, C/C++, experimental

Al cambiar estas opciones, puede modificar el comportamiento relacionado con IntelliSense y la base de datos de exploración cuando programa en C o C++. Estas características son experimentales y se pueden modificar o quitar de Visual Studio en una versión futura.

::: moniker range="vs-2017"

En este artículo se describen las opciones de Visual Studio 2017. En Visual Studio 2015, seleccione **2015** en el selector situado encima de la tabla de contenido.

::: moniker-end

Para acceder a esta página de propiedades, presione **Ctrl**+**Q** para activar el cuadro de búsqueda y luego escriba **experimental**. La búsqueda encuentra la página después de las primeras letras. También puede acceder a ella si elige **Herramientas** > **Opciones** y expande **Editor de texto**, luego **C/C++** y elige **Experimental**.

Estas características están disponibles en una instalación de Visual Studio.

> [!NOTE]
> Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Habilitar IntelliSense predictivo

IntelliSense predictivo limita el número de resultados que se muestran en la lista desplegable de IntelliSense para que vea únicamente los resultados que son relevantes en el contexto. Por ejemplo, si escribe `int x =` e invoca la lista desplegable de IntelliSense, solo verá números enteros o funciones que devuelven enteros. IntelliSense predictivo está desactivado de forma predeterminada.

::: moniker range="vs-2017"

## <a name="enable-faster-project-load"></a>Habilitar la carga de proyectos más rápida

A partir de Visual Studio 2017 versión 15.3, esta característica se denomina **Habilitar almacenamiento en caché de los proyectos** y se ha movido a la página de propiedades [Configuración de proyecto de VC++](vcpp-project-settings-projects-and-solutions-options-dialog-box.md).

Esta opción permite que Visual Studio copie en caché los datos de un proyecto para que, cuando lo abra la próxima vez, se carguen esos datos en lugar de volver a calcularlos desde los archivos de proyecto. Usar datos en caché puede acelerar de forma significativa el tiempo de carga de un proyecto.

::: moniker-end

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Características adicionales de Visual Studio Marketplace

Puede examinar las características adicionales del editor de texto en [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads). Un ejemplo es [C++ Quick Fixes](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017), que admite lo siguiente:

- **Agregar #include faltante** : sugiere las directivas #include pertinentes para símbolos desconocidos en el código

- **Agregar mediante espacio de nombres o símbolo completo** : similar al elemento anterior, pero para espacios de nombres

- **Agregar punto y coma faltante**

- **Ayuda en pantalla**: buscar ayuda en línea para los mensajes de error

- Y mucho más...

## <a name="see-also"></a>Vea también

- [Opciones del editor específicas del lenguaje](../../ide/reference/setting-language-specific-editor-options.md)
- [Refactorización en C++ (Blog de VC)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/
)
