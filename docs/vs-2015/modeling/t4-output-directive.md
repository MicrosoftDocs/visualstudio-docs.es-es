---
title: Directiva de salida T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 149370bfee1b142876dff881625d08083afadea4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652311"
---
# <a name="t4-output-directive"></a>Directiva de salida T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En las plantillas de texto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], la directiva `output` sirve para definir la extensión de nombre de archivo y codificación del archivo transformado.

 Por ejemplo, si el proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] incluye un archivo de plantilla denominado **MyTemplate.TT** que contiene la siguiente directiva:

 `<#@output extension=".cs"#>`

 a continuación [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generará un archivo denominado **MyTemplate.CS**

 La directiva de `output` no es necesaria en una plantilla de texto en tiempo de ejecución (preprocesada), ya que, en su lugar, la aplicación obtiene la cadena generada llamando a `TextTransform()`. Para obtener más información, vea [generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

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

 `0` (valor predeterminado del sistema)

 Por lo general, se puede usar la cadena WebName o el número de CodePage de cualquiera de las codificaciones devueltas por <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.
