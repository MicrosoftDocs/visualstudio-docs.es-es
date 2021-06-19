---
title: Directiva de salida T4
description: Obtenga información sobre Visual Studio plantillas de texto, la directiva de salida se usa para definir la extensión de nombre de archivo y la codificación del archivo transformado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8105edc57e68aa7cedcb612ec4f6bcd0ef367d2f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386116"
---
# <a name="t4-output-directive"></a>Directiva de salida T4

En Visual Studio de texto, la directiva se usa para definir la extensión de nombre de archivo y `output` la codificación del archivo transformado.

 Por ejemplo, si el proyecto Visual Studio incluye un archivo de plantilla **denominado MyTemplate.tt** que contiene la directiva siguiente:

 `<#@output extension=".cs"#>`

 a Visual Studio generará un archivo denominado **MyTemplate.cs**

 La directiva de `output` no es necesaria en una plantilla de texto en tiempo de ejecución (preprocesada), ya que, en su lugar, la aplicación obtiene la cadena generada llamando a `TextTransform()`. Para obtener más información, vea [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

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

 Valores aceptables: cualquier extensión de nombre de archivo válida.

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

 `0` (Valor predeterminado del sistema)

 Por lo general, se puede usar la cadena WebName o el número de CodePage de cualquiera de las codificaciones devueltas por <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.
