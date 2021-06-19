---
title: Directivas de plantilla de texto T4
description: Obtenga información sobre las directivas de plantilla de prueba T4 y cómo proporcionan instrucciones al motor de transformación de plantillas de texto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0d9b7ca189ced11eea57e175a06b81161090070b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388742"
---
# <a name="t4-text-template-directives"></a>Directivas de plantilla de texto T4

Las directivas proporcionan instrucciones al motor de transformación de plantillas de texto.

La sintaxis de directivas es la siguiente:

```
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>
```

Todos los valores de atributo deben aparecer delimitados por comillas dobles. Si el propio valor contiene comillas dobles, se deben incluir en secuencia de escape con el carácter \.

Normalmente, las directivas son los primeros elementos en un archivo de plantilla o un archivo incluido. No debería colocarlos dentro de un bloque de código `<#...#>`, ni después de un bloque de características de clase `<#+...#>`.

[Directiva de plantilla T4](../modeling/t4-template-directive.md)

```
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>
```

[Directiva de parámetro T4](../modeling/t4-parameter-directive.md)

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

[Directiva de salida T4](../modeling/t4-output-directive.md)

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

[Directiva de ensamblado T4](../modeling/t4-assembly-directive.md)

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

[Directiva de importación T4](../modeling/t4-import-directive.md)

```
<#@ import namespace="namespace" #>
```

[Directiva Include T4](../modeling/t4-include-directive.md)

```
<#@ include file="filePath" #>
```

[T4 CleanUpBehavior (Directiva)](../modeling/t4-cleanupbehavior-directive.md)

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

También puede crear sus propias directivas. Para obtener más información, vea [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md). Si utiliza el SDK de visualización y modelado para crear un lenguaje específico del dominio (ADSL), se generará un procesador de directivas como parte del ADSL.
