---
title: "System DLL &lt;name&gt; could not be loaded. | Microsoft Docs"
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
  - "vs.message.VB_E_TERRSYSDLLNOTLOADED"
  - "vs.message.0x800A0085"
ms.assetid: d4ccb3b1-fbc3-4395-a9b1-be50a4d7bf44
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# System DLL &lt;name&gt; could not be loaded.
No se encuentra un archivo .DLL proporcionado por el sistema operativo, como DDEML.DLL, VERSION.DLL o WINSPOOL.DRV.  Este error ocurre normalmente cuando se cumple una de estas condiciones: el archivo no está en la ruta de acceso correcta, la DLL está dañada o se eliminó, o no hay memoria suficiente.  
  
### Para corregir este error  
  
1.  Compruebe que la DLL está en el directorio System de Windows.  
  
     \-O bien\-  
  
     Vuelva a cargar la DLL.  
  
     \-O bien\-  
  
     Intente liberar memoria cerrando otras aplicaciones abiertas.