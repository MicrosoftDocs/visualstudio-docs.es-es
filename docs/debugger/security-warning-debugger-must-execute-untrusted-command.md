---
title: "Advertencia de seguridad: El depurador debe ejecutar un comando que no es de confianza | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.sourceserver.securityalert"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Advertencia de seguridad: El depurador debe ejecutar un comando que no es de confianza
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este cuadro de diálogo de advertencia aparece cuando utiliza un servidor de origen.  Indica que el comando que el depurador debe ejecutar para obtener el código fuente no figura en la lista de comandos de confianza del servidor de origen incluida en el archivo srcsvr.ini.  Si es un comando válido, se puede agregar al archivo srcsvr.ini.  De lo contrario, no debe ejecutarse.  Para obtener más información, consulte [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## Texto del mensaje  
 El depurador debe ejecutar el siguiente comando que no es de confianza para obtener el código fuente del servidor de origen.  
  
 Si el archivo de símbolos de depuración \(\*.pdb\) no procede de una fuente conocida y de confianza, este comando puede no ser válido o su ejecución puede ser peligrosa.  
  
 ¿Desea ejecutar este comando?  
  
## Lista de UIElement  
 Cuadro de texto  
 Comando del archivo .pdb que se va a ejecutar.  
  
 Run  
 Permite que se ejecute el comando.  
  
 No ejecutar  
 Detiene la ejecución del comando y la descarga del archivo del servidor de origen.  
  
## Vea también  
 [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Servidor de origen](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)