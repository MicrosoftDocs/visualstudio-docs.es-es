---
title: "Advertencia del compilador de recursos RC4204 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RC4204"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC4204"
ms.assetid: f9a83b3c-d696-4b38-9576-945d1f6d0063
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia del compilador de recursos RC4204
Carácter ASCII no equivalente a código de tecla virtual  
  
 Se usó un literal de cadena para el código de tecla virtual en un acelerador de tipo VIRTKEY.  
  
 Esta advertencia permite continuar, pero tenga en cuenta que las teclas de aceleración generadas no pueden coincidir con la cadena indicada. \(los aceleradores VIRTKEY usan códigos de tecla distintos que los aceleradores ASCII\).  
  
 Aunque los literales de cadena sean válidos sintácticamente, solo se puede asegurar de que consigue el acelerador deseado mediante los valores **VK\_\*** `#define` en WINDOWS.h.