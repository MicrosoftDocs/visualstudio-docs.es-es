---
title: "Los par&#225;metros &#39;InterfaceId&#39; y &#39;EventsId&#39; para &#39;Microsoft.VisualBasic.ComClassAttribute&#39; en &#39;&lt;nombreTipo&gt;&#39; no pueden tener el mismo valor. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32507"
  - "vbc32507"
helpviewer_keywords: 
  - "BC32507"
ms.assetid: 762e2990-e578-492d-b8ee-11658b6069fc
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los par&#225;metros &#39;InterfaceId&#39; y &#39;EventsId&#39; para &#39;Microsoft.VisualBasic.ComClassAttribute&#39; en &#39;&lt;nombreTipo&gt;&#39; no pueden tener el mismo valor.
Un bloque de atributos `COMClassAttribute` especifica el mismo identificador único global \(GUID\) para la interfaz que para el evento de creación. Si se proporcionan ambos identificadores, deben ser diferentes. También deben ser diferentes del identificador de clase.  
  
 Un GUID consta de 16 bytes, de los cuales los ocho primeros son numéricos y el resto son binarios. Se genera mediante utilidades de Microsoft como uuidgen.exe y se garantiza que es único.  
  
 **Identificador de error:** BC32507  
  
### Para corregir este error  
  
1.  Determine los GUID correctos necesarios para identificar el evento de interfaz y de creación del objeto COM.  
  
2.  Asegúrese de que las cadenas del GUID presentadas en el bloque de atributos `COMClassAttribute` se copian correctamente.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos usados en Visual Basic](http://msdn.microsoft.com/es-es/22231318-8a40-49af-9245-e0aab723563b)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Clase ComClassAttribute](http://msdn.microsoft.com/es-es/5c2f0835-9210-47dc-bc59-5c1769953574)