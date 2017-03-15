---
title: "El nombre &#39;&lt;nombre&gt;&#39; no est&#225; declarado o no est&#225; en el &#225;mbito actual. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36610"
  - "bc36610"
helpviewer_keywords: 
  - "BC36610"
ms.assetid: e66a4b8a-9252-42ae-a30d-341fad4f74be
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El nombre &#39;&lt;nombre&gt;&#39; no est&#225; declarado o no est&#225; en el &#225;mbito actual.
Una consulta LINQ hace referencia a un elemento de programación, pero el compilador no encuentra un elemento que tenga ese nombre exacto.  
  
 **Identificador de error:** BC36610  
  
### Para corregir este error  
  
1.  Compruebe que el nombre de la instrucción de referencia esté bien escrito.[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no distingue mayúsculas de minúsculas, pero cualquier otra variación en la ortografía constituye un nombre diferente. Tenga en cuenta que el carácter de subrayado \(`_`\) es parte del nombre y, por tanto, parte de la ortografía.  
  
2.  Compruebe que el elemento de programación está en el ámbito. Si la instrucción de referencia está fuera de la región que declara el elemento de programación, es posible que deba calificar el nombre del elemento. Para obtener más información, consulta [Ámbito en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/scope).  
  
3.  Asegúrese de que tiene el operador de acceso a miembro \(`.`\) entre un objeto y su miembro. Por ejemplo, si tiene un control <xref:System.Windows.Forms.TextBox> denominado `TextBox1`, para tener acceso a su propiedad <xref:System.Windows.Forms.TextBoxBase.Text%2A> debe escribir `TextBox1.Text`. Si en su lugar escribe `TextBox1Text`, ha creado un nombre diferente.  
  
## Vea también  
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Convenciones de nomenclatura de Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/naming-conventions)   
 [Referencias a elementos declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements)