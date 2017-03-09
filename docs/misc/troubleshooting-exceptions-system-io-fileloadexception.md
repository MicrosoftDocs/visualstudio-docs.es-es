---
title: "Soluci&#243;n de problemas de excepciones: System.IO.FileLoadException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "FileLoadException (clase)"
ms.assetid: 6b4519e3-4d29-4031-8aec-c2735b4ee16d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.IO.FileLoadException
Cuando se encuentra un ensamblado administrado que no es posible cargar, se produce una excepción <xref:System.IO.FileLoadException>.  
  
## Sugerencias asociadas  
 **Asegúrese de que el archivo sea un ensamblado .NET Framework válido.**  
 Esta excepción se produce si el archivo no es un ensamblado de .NET Framework válido. Para obtener más información, consulta <xref:System.Reflection.Assembly>.  
  
 **Asegúrese de que ningún ensamblado o módulo se haya cargado dos veces con dos evidencias diferentes.**  
 La evidencia es el conjunto de información que se utiliza para tomar decisiones de la directiva de seguridad, por ejemplo, qué permisos se conceden al código. Para obtener más información, vea <xref:System.EnterpriseServices.Internal.Publish.GacRemove%2A> y <xref:System.Reflection.Assembly.Evidence%2A>.  
  
 **Si se utilizan los métodos RegisterAssembly o UnregisterAssembly, asegúrese de que el nombre de ensamblado no exceda la longitud de los caracteres de MAX\_PATH.**  
 La longitud del nombre del ensamblado no puede superar el valor de MAX\_PATH. Para obtener más información, consulte <xref:System.EnterpriseServices.Internal.IComSoapPublisher.RegisterAssembly%2A> y <xref:System.EnterpriseServices.Internal.IComSoapPublisher.UnRegisterAssembly%2A>.  
  
 **Si se carga un ensamblado satélite, asegúrese de que el objeto CultureInfo especificado coincida con el objeto CultureInfo del archivo.**  
 Los ensamblados satélite contienen recursos traducidos que, a su vez, contienen código ejecutable no traducible y recursos para una referencia cultural única que actúa como la referencia cultural predeterminada o neutra. Para obtener más información, consulta <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A>.  
  
## Vea también  
 <xref:System.IO.FileLoadException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)