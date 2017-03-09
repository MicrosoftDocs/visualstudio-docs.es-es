---
title: "No files were found to look in. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_FRLookInEmpty"
  - "vs.message.0x800A00DE"
ms.assetid: d560aef3-7a55-4fbb-a541-1a43fc13c18b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# No files were found to look in.
Este error se produce normalmente cuando se ha especificado un nombre de archivo o directorio en la lista Buscar en y dicho nombre no existe o no se encuentra.  Este error puede aparecer también si especifica un directorio válido que no contiene la extensión de archivo especificada en la lista Tipos de archivo o si el directorio especificado no contiene ningún archivo.  El error puede aparecer también al realizar búsquedas en un directorio con el atributo `Hidden` o `System` establecido.  
  
### Para corregir este error  
  
1.  Utilice el cuadro de diálogo **Conjunto de directorios personalizado** para buscar el nombre de directorio o archivo en el que se va buscar, en lugar de escribir la ruta de acceso o el nombre de archivo.  Para obtener acceso al cuadro de diálogo **Conjunto de directorios personalizado** elija el botón de puntos suspensivos situado junto a la lista **Buscar en**.  
  
2.  Cambie la extensión de archivo especificada en la lista **Tipos de archivo** a \*.\* para buscar todos los archivos del directorio especificado.  
  
### Para omitir este error  
  
1.  Mantenga presionada la tecla CTRL y presione ScrLk.  
  
     Esto cancela el cuadro de diálogo.  
  
## Vea también  
 [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md)   
 [Buscar en archivos](../ide/find-in-files.md)   
 [Choose Search Folders](http://msdn.microsoft.com/es-es/85af6458-dcde-4a84-9ea4-f5cc6550dc80)