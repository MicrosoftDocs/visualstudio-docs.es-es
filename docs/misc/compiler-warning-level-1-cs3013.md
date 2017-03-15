---
title: "Advertencia del compilador (nivel 1) CS3013 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3013"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3013"
ms.assetid: 00b3bbe1-f2a0-465c-be0e-1af700c5753d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS3013
Los módulos agregados se deben marcar con el atributo CLSCompliant para que coincidan con el ensamblado  
  
 Un módulo que se compiló con la opción [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) del compilador se agregó a una compilación con [\/addmodule](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). Sin embargo, la conformidad del módulo con Common Language Specification \(CLS\) no coincide con el estado de CLS de la compilación actual.  
  
 La conformidad con CLS se indica con el atributo module. Por ejemplo, `[module:CLSCompliant(true)]` indica que el módulo es conforme a CLS y `[module:CLSCompliant(false)]` indica que el módulo no es conforme a CLS. El valor predeterminado es `[module:CLSCompliant(false)]`. Para obtener más información sobre CLS, vea [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).