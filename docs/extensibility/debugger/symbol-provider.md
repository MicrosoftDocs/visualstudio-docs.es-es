---
title: "Proveedor de s&#237;mbolos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "controlador de símbolos"
  - "depurar [SDK de depuración], el controlador de símbolos"
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Proveedor de s&#237;mbolos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Una implementación del evaluador de la expresión debe tener acceso a información de depuración simbólica generada por el compilador de lenguaje para evaluar variables y expresiones.  Hacerlo utilizando las interfaces de proveedor de símbolos \(SP\), también denominadas un controlador de símbolos.  
  
 SPS de fuentes de[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]para el código administrado como código nativo utilizando el formato de archivo de símbolos de \(PDB\) la base de datos de programa.  A menos que haya una necesidad seguros de programa de utilizar los símbolos almacenados en un formato personalizado, se recomienda utilizar el SPS proporcionado por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Notas de implementación  
 Los motores de depuración de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]esperan comunicarse con el SPS mediante interfaces \(CLR\) de Common Language Runtime.  Como resultado, SP que funcionará con los motores de depuración de Visual Studio debe admitir CLR.  Una lista completa de todo el CLR que las interfaces de depuración se puede encontrar en debugref.doc, que forma parte de [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Si SP solo funciona con el motor de depuración, puede implementar SP según su conveniencia dependiendo de las necesidades del motor de depuración.  
  
## Vea también  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)