---
title: "T4 Output Directive | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 4
caps.handback.revision: 4
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 Output Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En las plantillas de texto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la directiva `output` sirve para definir la extensión de nombre de archivo y codificación del archivo transformado.  
  
 Por ejemplo, si el proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] incluye un archivo de plantilla denominado **MyTemplate.tt**, que contiene la siguiente directiva:  
  
 `<#@output extension=".cs"#>`  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generará un archivo denominado **MyTemplate.cs**  
  
 La directiva de `output` no es necesaria en una plantilla de texto en tiempo de ejecución \(preprocesada\),  ya que, en su lugar, la aplicación obtiene la cadena generada llamando a `TextTransform()`.  Para obtener más información, vea [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## Uso de la directiva de salida  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 No debe haber más de una directiva de `output` en cada plantilla de texto.  
  
## Atributo extension  
 Especifica la extensión de nombre del archivo de salida de texto generado.  
  
 El valor predeterminado es **.cs**  
  
 Ejemplos:  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 Valores aceptables:  
 Cualquier extensión de nombre de archivo válida.  
  
## Atributo encoding  
 Especifica la codificación que se va a usar cuando el archivo de salida se genera.  Por ejemplo:  
  
 `<#@ output encoding="utf-8"#>`  
  
 El valor predeterminado es la codificación que el archivo de plantilla de texto utiliza.  
  
 Valores aceptables:  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` \(valor predeterminado del sistema\)  
  
 Por lo general, se puede usar la cadena WebName o el número de CodePage de cualquiera de las codificaciones devueltas por <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.