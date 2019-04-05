---
title: T4 Directivas de plantilla de texto | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
ms.assetid: 6898ee02-ebb2-4635-a4e9-350774c13cf2
caps.latest.revision: 83
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ce0acf7c1c63f0d1c05d1e1d3b59dc7a5d28862a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994916"
---
# <a name="t4-text-template-directives"></a>Directivas de plantilla de texto T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
