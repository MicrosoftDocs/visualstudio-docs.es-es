---
title: "El car&#225;cter de continuaci&#243;n de l&#237;nea &#39;_&#39; debe ir precedido de al menos un espacio en blanco y debe ser el &#250;ltimo car&#225;cter de la l&#237;nea | Microsoft Docs"
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
  - "vbc30999"
  - "bc30999"
helpviewer_keywords: 
  - "BC30999"
ms.assetid: 32caf62f-52e4-4acd-b40f-5af65e42e643
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El car&#225;cter de continuaci&#243;n de l&#237;nea &#39;_&#39; debe ir precedido de al menos un espacio en blanco y debe ser el &#250;ltimo car&#225;cter de la l&#237;nea
Puede utilizar el carácter de continuación de línea, que es un carácter de subrayado \(\_\), para dividir una línea de código larga en varias líneas en el archivo. El carácter de subrayado debe tener inmediatamente antes un espacio e inmediatamente después un terminador de línea \(retorno de carro\). Por ejemplo:  
  
```  
Dim books As XDocument = _ XDocument.Load(My.Application.Info.DirectoryPath & _ "\..\..\Data\books.xml")  
```  
  
 **Id. de error:** BC30999  
  
### Para corregir este error  
  
1.  Asegúrese de que el carácter de continuación de línea \(\_\) es el último carácter de una línea de código.  
  
2.  Asegúrese de que haya un espacio delante del carácter de continuación de línea y sepárelo de cualquier otro código en la línea.  
  
## Vea también  
 [Cómo: Interrumpir y combinar instrucciones en código](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)