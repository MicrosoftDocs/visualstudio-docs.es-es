---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; en la clase &#39;&lt;nombreDeClase&gt;&#39; declara impl&#237;citamente el &lt;tipo&gt; &#39;&lt;nombreDeMiembro&gt;&#39; que entra en conflicto con un miembro del mismo nombre en el &lt;tipo&gt; &#39;&lt;nombreDeTipo&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BC42101"
ms.assetid: 001c8eaa-19b6-44fa-8056-4186ecffbda8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; en la clase &#39;&lt;nombreDeClase&gt;&#39; declara impl&#237;citamente el &lt;tipo&gt; &#39;&lt;nombreDeMiembro&gt;&#39; que entra en conflicto con un miembro del mismo nombre en el &lt;tipo&gt; &#39;&lt;nombreDeTipo&gt;&#39;
'Microsoft.VisualBasic.ComClassAttribute' en la clase '\<nombreDeClase\>' declara implícitamente el \<tipo\> '\<nombreDeMiembro\>' que entra en conflicto con un miembro del mismo nombre en el \<tipo\> '\<nombreDeTipo\>'. Use 'Microsoft.VisualBasic.ComClassAttribute\(InterfaceShadows:\=True\)' si quiere ocultar el nombre en el '\<nombreDeTipo\>' base.  
  
 Una clase que usa un bloque de atributos `COMClassAttribute` define implícitamente una interfaz con el mismo nombre que un miembro de la clase base. En esta situación, el nombre de la interfaz debe ocultar el miembro de la clase base.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42101  
  
### Para corregir este error  
  
1.  Si quiere ocultar el miembro de la clase base, establezca `InterfaceShadows:=True` en el bloque de atributos `ComClassAttribute`.  
  
2.  Si no quiere ocultar el miembro de la clase base, cambie el nombre de la clase.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos usados en Visual Basic](http://msdn.microsoft.com/es-es/22231318-8a40-49af-9245-e0aab723563b)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de los atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute \(Clase\)](http://msdn.microsoft.com/es-es/5c2f0835-9210-47dc-bc59-5c1769953574)   
 [ComClassAttribute.InterfaceShadows \(Propiedad\)](http://msdn.microsoft.com/es-es/0fae25bd-e0ba-4755-a76c-3b526b1ac795)