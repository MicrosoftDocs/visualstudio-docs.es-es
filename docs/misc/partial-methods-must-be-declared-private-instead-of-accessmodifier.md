---
title: "Los m&#233;todos parciales deben declararse como &#39;Private&#39; en lugar de como &#39;&lt;modificadorDeAcceso&gt;&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31431"
  - "bc31431"
helpviewer_keywords: 
  - "BC31431"
ms.assetid: bbd757f3-7281-4488-8a06-f3b4bcc820dc
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los m&#233;todos parciales deben declararse como &#39;Private&#39; en lugar de como &#39;&lt;modificadorDeAcceso&gt;&#39;.
El modificador de acceso `Private` es necesario en las declaraciones de método parcial. En el ejemplo siguiente se muestra el uso de `Private` en la firma de método y su implementación.  
  
```vb#  
' Definition of the partial method signature. Partial Private Sub OnNameChanged() ' The body of the signature is empty. End Sub  
```  
  
```vb#  
' Implementation of the partial method. Private Sub OnNameChanged() MsgBox("Name was changed to " & Me.Name) End Sub  
```  
  
 **Identificador de error:** BC31431  
  
### Para corregir este error  
  
-   Cambie el modificador de acceso a `Private` en las declaraciones de firma e implementación.  
  
## Vea también  
 [Métodos Partial](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)