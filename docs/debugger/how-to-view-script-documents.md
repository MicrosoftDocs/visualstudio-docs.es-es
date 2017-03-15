---
title: "C&#243;mo: Ver documentos de script | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Explorador de scripts"
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# C&#243;mo: Ver documentos de script
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En versiones anteriores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], los archivos de script de cliente generados a partir de script de servidor aparecían en la ventana Explorador de scripts.  Esta ventana solía estar oculta, por lo que la disponibilidad de archivos de script de cliente no siempre resultaba obvia.  
  
 En [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], los archivos de script de cliente generados a partir de script de servidor aparecen en el Explorador de soluciones, que está visible de manera predeterminada.  Se ha eliminado la ventana Explorador de scripts.  
  
 Los archivos de script de cliente sólo están visibles en modo de depuración o en modo de interrupción.  Aparecen en el nodo **Documentos de script**.  
  
 Los archivos de script de servidor siempre están visibles.  Aparecen en el nodo **\<Nombre de ruta de acceso del sitio web\>**.  El nombre del nodo es similar al de este ejemplo: `c:\...\Website2\`  
  
### Para ver un documento de script de servidor  
  
1.  En el **Explorador de soluciones**, abra el nodo **\<Nombre de ruta de acceso del sitio web\>**.  
  
2.  Haga doble clic en el archivo de script que desee ver.  
  
     El archivo de script de servidor se abre en una ventana de código fuente.  
  
### Para ver un documento de script de cliente  
  
1.  En el **Explorador de soluciones**, abra el nodo **Documentos de script**.  
  
2.  Haga doble clic en el archivo de script que desee ver.  
  
     El archivo de script de cliente se abre en una ventana de código fuente.  
  
## Vea también  
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)