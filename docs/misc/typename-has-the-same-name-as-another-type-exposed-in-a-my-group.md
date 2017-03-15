---
title: "&#39;&lt;typename&gt;&#39; tiene el mismo nombre que otro tipo expuesto en un grupo &#39;My&#39; | Microsoft Docs"
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
  - "vbc36015"
  - "bc36015"
helpviewer_keywords: 
  - "BC36015"
ms.assetid: cd2286da-49be-461f-bec9-58e9c53e250b
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; tiene el mismo nombre que otro tipo expuesto en un grupo &#39;My&#39;
'\<typename\>' tiene el mismo nombre que otro tipo expuesto en un grupo 'My'. Cambie el nombre del formulario o el espacio de nombres que lo contiene.  
  
 Una clase o estructura está declarada con el mismo nombre que una clase o estructura de uno de los objetos `My`.  
  
 No se puede evitar un conflicto de nombres entre dos clases a las que se puede acceder a través de un objeto `My`, como `My.Forms`.  
  
 Si hay un conflicto potencial de nombres entre clases de un objeto `My`, el compilador cambia el nombre de la propiedad del tipo de *ClassName* a *RootNamespace*\_*Namespace*\_*ClassName*. Por ejemplo, considere dos formularios denominados `Form1`. Si uno de estos formularios está en el espacio de nombres raíz `WindowsApplication1` y en el espacio de nombres `Namespace1`, accedería a ese formulario a través de `My.Forms.WindowsApplication1_Namespace1_Form1`.  
  
 Este error puede producirse si dos clases tienen el mismo nombre y están en espacios de nombres anidados con caracteres de subrayado en sus nombres. Cuando el compilador construye los nuevos nombres de propiedad de las clases, sigue habiendo un conflicto de nombres.  
  
 **Id. de error:** BC36015  
  
### Para corregir este error  
  
1.  Cambie el nombre del nuevo formulario.  
  
2.  Cambie el nombre de los espacios de nombres.  
  
     Evite poner a cualquier clase o estructura el mismo nombre que el de una existente.  
  
## Vea también  
 <xref:System.Windows.Forms.Form>   
 <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute>   
 [NO ESTÁ EN LA COMPILACIÓN: Resolver una referencia cuando varias variables tienen el mismo nombre](http://msdn.microsoft.com/es-es/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [My.Forms \(Objeto\)](/dotnet/visual-basic/language-reference/objects/my-forms-object)