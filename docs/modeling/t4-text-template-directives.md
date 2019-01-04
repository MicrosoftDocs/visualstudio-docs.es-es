---
title: Directivas de plantilla de texto T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 3bf8248a7a68b914d6276e3e6f37261fb6137efc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939257"
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

 [Directiva T4 CleanUpBehavior](../modeling/t4-cleanupbehavior-directive.md)
 ```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

 También puede crear sus propias directivas. Para obtener más información, consulte [procesadores de la directiva de plantilla de creación personalizado T4 texto](../modeling/creating-custom-t4-text-template-directive-processors.md). Si utiliza el SDK de visualización y modelado para crear un lenguaje específico del dominio (ADSL), se generará un procesador de directivas como parte del ADSL.