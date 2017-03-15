---
title: "Error del compilador CS1906 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1906"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1906"
ms.assetid: 1a6abf5c-f673-4256-93ac-313dce50acc0
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1906
Opción 'option' no válida; la visibilidad de los recursos debe ser 'public' o 'private'  
  
 Este error indica que una opción de línea de comandos [\/resource \(Incrustar un archivo de recursos en el resultado\)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option) o [\/linkresource \(Vincular a recursos de .NET Framework\/linkresource \(Vincular a recursos de .NET Framework\)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option) no válida. Compruebe la sintaxis de la opción de línea de comandos **\/resource** o **\/linkresource** y asegúrese de que el modificador de accesibilidad usado sea **public** o `private`.