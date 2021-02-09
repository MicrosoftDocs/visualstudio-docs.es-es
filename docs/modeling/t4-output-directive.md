---
title: Directiva de salida T4
description: Aprenda que en las plantillas de texto de Visual Studio, la Directiva de salida se usa para definir la extensión de nombre de archivo y la codificación del archivo transformado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 58e7c255d767e9b35764e03a76f9cda516dbe606
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899599"
---
# <a name="t4-output-directive"></a>Directiva de salida T4

En las plantillas de texto de Visual Studio, la `output` Directiva se usa para definir la extensión de nombre de archivo y la codificación del archivo transformado.

 Por ejemplo, si el proyecto de Visual Studio incluye un archivo de plantilla denominado **MyTemplate.TT** que contiene la siguiente directiva:

 `<#@output extension=".cs"#>`

 después, Visual Studio generará un archivo denominado **MyTemplate.CS**

 La directiva de `output` no es necesaria en una plantilla de texto en tiempo de ejecución (preprocesada), ya que, en su lugar, la aplicación obtiene la cadena generada llamando a `TextTransform()`. Para obtener más información, vea [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Uso de la directiva de salida

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 No debe haber más de una directiva de `output` en cada plantilla de texto.

## <a name="extension-attribute"></a>atributo de extensión
 Especifica la extensión de nombre del archivo de salida de texto generado.

 El valor predeterminado es **. CS**

 Ejemplos: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Valores aceptables: cualquier extensión de nombre de archivo válida.

## <a name="encoding-attribute"></a>atributo Encoding
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
