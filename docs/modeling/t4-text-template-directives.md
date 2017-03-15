---
title: "T4 Text Template Directives | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, import directive"
  - "text templates, include directive"
  - "text templates, assembly directive"
  - "text templates, output directive"
  - "text templates, directives"
  - "text templates, template directive"
ms.assetid: 6898ee02-ebb2-4635-a4e9-350774c13cf2
caps.latest.revision: 81
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 81
---
# T4 Text Template Directives
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las directivas proporcionan instrucciones al motor de transformación de plantillas de texto.  
  
 La sintaxis de directivas es la siguiente:  
  
```  
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>  
```  
  
 Todos los valores de atributo deben aparecer delimitados por comillas dobles.  Si el propio valor contiene comillas dobles, se deben incluir en secuencia de escape con el carácter \\.  
  
 Normalmente, las directivas son los primeros elementos en un archivo de plantilla o un archivo incluido.  No debería colocarlos dentro de un bloque de código `<#...#>`, ni después de un bloque de características de clase `<#+...#>`.  
  
 [T4 Template Directive](../modeling/t4-template-directive.md)  
 ```  
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>  
```  
  
 [T4 Parameter Directive](../modeling/t4-parameter-directive.md)  
 ```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 [T4 Output Directive](../modeling/t4-output-directive.md)  
 ```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 [T4 Assembly Directive](../modeling/t4-assembly-directive.md)  
 ```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 [T4 Import Directive](../modeling/t4-import-directive.md)  
 ```  
<#@ import namespace="namespace" #>  
```  
  
 [T4 Include Directive](../modeling/t4-include-directive.md)  
 ```  
<#@ include file="filePath" #>  
```  
  
 [T4 CleanUpBehavior \(Directiva\)](../modeling/t4-cleanupbehavior-directive.md)  
 ```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 También puede crear sus propias directivas.  Para obtener más información, vea [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md).  Si utiliza el SDK de visualización y modelado para crear un lenguaje específico del dominio \(ADSL\), se generará un procesador de directivas como parte del ADSL.