---
title: "Soluci&#243;n de problemas de excepciones: System.OutOfMemoryException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "OutOfMemoryException (clase)"
ms.assetid: eb16f008-964e-40a1-91f6-6ad25fa82d5a
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.OutOfMemoryException
Cuando falla un intento de asignar memoria, se produce una excepción <xref:System.OutOfMemoryException>.  
  
## Sugerencias asociadas  
 **Si está creando una matriz, asegúrese de que el tamaño es correcto.**  
 Para obtener más información, los usuarios de Visual Basic pueden ver [Matrices](/dotnet/visual-basic/programming-guide/language-features/arrays/index).  
  
 Para obtener más información, los usuarios de C\# pueden ver [Matrices](/dotnet/csharp/programming-guide/arrays/index).  
  
 **Compruebe que hay memoria suficiente para fines internos y nuevos objetos administrados.**  
 Si programa en [!INCLUDE[Compact](../extensibility/includes/compact_md.md)], Common Language Runtime produce esta excepción cuando no hay memoria suficiente para fines internos o nuevos objetos administrados. Para que esto no suceda, evite programar métodos extensos que consuman 64 o más kilobytes de memoria.  
  
## Comentarios  
 Por lo general, la utilización excesiva de memoria administrada se produce por:  
  
-   Leer conjuntos de datos de gran tamaño en la memoria.  
  
-   Crear demasiadas entradas de la caché.  
  
-   Cargar o descargar archivos de gran tamaño.  
  
-   Usar en forma excesiva expresiones regulares o cadenas durante el análisis de archivos.  
  
-   Demasiada utilización del estado de vista.  
  
-   Demasiados datos en estado de sesión o demasiadas sesiones.  
  
 Es posible que esta excepción se produzca con el mensaje adicional "Espacio de almacenamiento insuficiente para completar esta operación", al invocar un método en un objeto COM que devuelve un tipo definido por el usuario que contiene una matriz segura \(una matriz de tamaño flexible\). Esto se debe a que .NET Framework no puede calcular las referencias de un campo de estructura con un tipo de matriz segura.  
  
## Vea también  
 <xref:System.OutOfMemoryException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)