---
title: "Could not bind to dependency &#39;assembly&#39; | Microsoft Docs"
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
  - "vs.tasklisterror.cantbinddependency"
ms.assetid: 0f76190d-d57e-4e0e-bec4-532aec978d08
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not bind to dependency &#39;assembly&#39;
Una de las referencias del proyecto contiene una referencia de ensamblado \(dependencia\) que se ha ubicado; sin embargo, el ensamblado no es válido.  Este error no impedirá la compilación del proyecto.  No obstante, puede generarse un error en tiempo de ejecución.  
  
 Esta situación implica que las tres condiciones siguientes son verdaderas:  
  
-   Hay más de un archivo en disco con el mismo nombre.  
  
-   Uno de los archivos no es un ensamblado, pero el otro sí lo es.  
  
-   La ruta de acceso de referencias busca primero en el directorio que contiene el archivo que no es un ensamblado.  
  
 **Para corregir este error**  
  
-   Modifique el orden en que el proyecto busca referencias en los directorios.  Para obtener más información, vea [NIB: Reference Paths Dialog Box \(Visual Basic\)](http://msdn.microsoft.com/es-es/8e549b39-7256-456a-8fd7-089b23facf9c).  
  
## Vea también  
 [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md)   
 [Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/es-es/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)