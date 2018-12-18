---
title: Directiva de salida T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 624afd32a9b0f44e3190fba7e3b126663b96f6f4
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860204"
---
# <a name="t4-output-directive"></a>Directiva de salida T4

En las plantillas de texto de Visual Studio, el `output` directiva se usa para definir la extensión de nombre de archivo y la codificación del archivo transformado.

 Por ejemplo, si el proyecto de Visual Studio incluye un archivo de plantilla denominado **MyTemplate.tt** que contiene la siguiente directiva:

 `<#@output extension=".cs"#>`

 Visual Studio generará un archivo denominado **MyTemplate.cs**

 La directiva de `output` no es necesaria en una plantilla de texto en tiempo de ejecución (preprocesada), ya que, en su lugar, la aplicación obtiene la cadena generada llamando a `TextTransform()`. Para obtener más información, consulte [generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Uso de la directiva de salida

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 No debe haber más de una directiva de `output` en cada plantilla de texto.

## <a name="extension-attribute"></a>atributo de extensión
 Especifica la extensión de nombre del archivo de salida de texto generado.

 El valor predeterminado es **.cs**

 Ejemplos: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Los valores aceptables: Cualquier nombre de la extensión de archivo válida.

## <a name="encoding-attribute"></a>atributo de codificación
 Especifica la codificación que se va a usar cuando el archivo de salida se genera. Por ejemplo:

 `<#@ output encoding="utf-8"#>`

 El valor predeterminado es la codificación que el archivo de plantilla de texto utiliza.

 Valores aceptables: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (valor predeterminado del sistema)

 Por lo general, se puede usar la cadena WebName o el número de CodePage de cualquiera de las codificaciones devueltas por <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.