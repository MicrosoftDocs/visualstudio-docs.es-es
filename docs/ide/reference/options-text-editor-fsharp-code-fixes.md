---
title: Opciones, Editor de texto, F#, correcciones de código
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c20646c8da4101ac674a64c5ca1ed23a3b1fd7b5
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770931"
---
# <a name="options-text-editor--f--code-fixes"></a>Opciones: Editor de texto > F# > Correcciones de código

Use la página de opciones Correcciones de código para especificar la configuración que puede ayudar a identificar los errores de código y a ofrecer soluciones. Para acceder a esta página de opciones, elija **Herramientas** > **Opciones** y luego elija **Editor de texto** > **F#**  > **Correcciones de código**.

## <a name="code-fixes"></a>Correcciones de código

- **Simplificar nombres (quitar calificadores no necesarios)**

  Si se activa esta casilla de verificación, los nombres completos se simplifican cuando no son necesarias la calificaciones, como para un miembro de un espacio de nombres usado con frecuencia.

- **Colocar siempre instrucciones abiertas en el nivel superior**

  Si se activa esta casilla y se escribe una instrucción `open` en el código, se coloca en el nivel superior.

- **Quitar instrucciones abiertas no utilizadas**

  Si esta casilla está activada, los documentos se analizan para buscar instrucciones `open` no utilizadas y aparece una bombilla [Acción rápida](../quick-actions.md) con una acción para quitar todas las instrucciones `open` no utilizadas.

- **Analizar y sugerir correcciones para valores no utilizados**

  Si se activa esta casilla, la herramienta reconoce un valor que no se está usando en el código. Luego, si mantiene el puntero del mouse sobre el valor no utilizado, recomienda algunas formas en las que puede usar el valor.

## <a name="see-also"></a>Vea también

- [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
- [Buscar cambios en el código y otro historial con CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)
