---
title: Opciones, Editor de texto, F#, correcciones de código
ms.date: 01/16/2019
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9345cf5d608ec8b69d88ac1c1644510f105337fd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947080"
---
# <a name="options-text-editor-f-code-fixes"></a>Opciones, Editor de texto, F#, correcciones de código

Use la página de opciones **Correcciones de código** para especificar la configuración que puede ayudar a identificar los errores de código y a ofrecer soluciones. Para acceder a esta página de opciones, elija **Herramientas** > **Opciones** y luego elija **Editor de texto** > **F#** > **Correcciones de código**.

## <a name="code-fixes"></a>Correcciones de código

- **Simplificar nombres (quitar calificadores no necesarios)**

   Si se activa esta casilla de verificación, los nombres completos se simplifican cuando no son necesarias la calificaciones, como para un miembro de un espacio de nombres usado con frecuencia.

- **Colocar siempre instrucciones abiertas en el nivel superior**

   Si se activa esta casilla y se escribe una instrucción abierta en el código, se coloca en el nivel superior.

- **Quitar instrucciones abiertas no utilizadas**

   Si se activa esta casilla, se quitan las instrucciones abiertas del archivo actual que no están en uso.

- **Analizar y sugerir correcciones para valores no utilizados**

   Si se activa esta casilla, la herramienta reconoce un valor que no se está usando en el código. Luego, si mantiene el puntero del mouse sobre el valor no utilizado, recomienda algunas formas en las que puede usar el valor.

## <a name="see-also"></a>Vea también

- [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
- [Buscar cambios en el código y otro historial con CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)