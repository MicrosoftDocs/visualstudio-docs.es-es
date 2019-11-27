---
title: Opciones, editor de texto, C/C++, experimental | Microsoft Docs
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5979363f16f2e9d78a2f50ffbb6511d03146caaa
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297853"
---
# <a name="options-text-editor-cc-experimental"></a>Opciones, editor de texto, C/C++, experimental
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Al cambiar estas opciones, puede modificar el comportamiento relacionado con IntelliSense y la base de datos de exploración cuando programa en C o C++.

 Para tener acceso a esta página, en el cuadro de diálogo **Opciones** , en el panel izquierdo, expanda **Editor de texto**, expanda **C/C++** y luego haga clic en **Experimental**.

 Estas características están disponibles en una instalación de Visual Studio 2015 Update 1 RC.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Consulte [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="browsingnavigation"></a>Exploración o navegación
 **Habilitar nueva motor de base de datos** Esto debe acelerar automáticamente el rellenado de la base de datos y realizar todas las operaciones de base de datos más rápido (sin pérdida de precisión) para operaciones tales como **ir a definición** y **Buscar todas las referencias**. (Para aplicar los cambios, solo cierre y vuelva a abrir la solución; no es necesario reiniciar Visual Studio).

## <a name="intellisense"></a>IntelliSense
 **Punto a flecha de la lista de miembros** Reemplaza "." por "->" cuando es aplicable para la lista de miembros.

## <a name="refactoring"></a>Refactorización
 **Habilitar extraer función** Extraer el código seleccionado a su propia función y reemplazar el código por una llamada a la nueva función. Para obtener acceso a esta característica, haga clic con el botón derecho en el código seleccionado y seleccione **Acciones rápidas**o simplemente presione el método abreviado de teclado predeterminado Ctrl+punto [Ctrl+.].

 **Habilitar cambiar firma** Agregar, reordenar y eliminar parámetros de una función y propagar los cambios a todos los sitios de llamada. Para obtener acceso a esta característica, haga clic con el botón derecho en cualquier uso de la función y seleccione **Acciones rápidas**o simplemente presione el método abreviado predeterminado Ctrl+punto [Ctrl+.].

## <a name="text-editor"></a>Editor de texto
 **Habilitar expandir ámbitos** Si está habilitada, puede escribir "{" en el editor de texto para encerrar el texto seleccionado entre llaves.

 **Habilitar expandir precedencia** Si está habilitada, puede escribir "(" en el editor de texto para rodear el texto seleccionado entre paréntesis.

 Para conocer las características adicionales del editor de texto de la Galería de Visual Studio, consulte la lista [aquí](https://go.microsoft.com/fwlink/?LinkId=692016). Un ejemplo es [C++ Quick Fixes](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f), que admite lo siguiente:

- **Agregar #include faltante** : sugiere las directivas #include pertinentes para símbolos desconocidos en el código

- **Agregar mediante espacio de nombres o símbolo completo** : similar al elemento anterior, pero para espacios de nombres

- **Agregar punto y coma faltante**

- **Ayuda de MSDN** : buscar en MSDN los mensajes de error

  Puede mantener el puntero sobre una línea ondulada para obtener una bombilla, o bien use el método abreviado de teclado predeterminado CTRL+punto (Ctrl+.). Tenga en cuenta que en el caso del método abreviado de teclado, no es necesario situar el símbolo de intercalación en el error o token específico. Simplemente puede estar en la misma línea que el error para invocar sugerencias para cualquier elemento incluido en esa línea.

## <a name="see-also"></a>Vea también
 [Configuración de las opciones del editor específicas del idioma](../../ide/reference/setting-language-specific-editor-options.md) [refactorización en C++ (blog de VC)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
