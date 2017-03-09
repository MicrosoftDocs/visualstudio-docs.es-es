---
title: "The selected Add-In has not been confirmed to be &#39;Command Line Safe&#39;, and may require some user intervention (possible UI). | Microsoft Docs"
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
  - "vs.message.0x800A0031"
  - "vs.message.VB_E_IDWADDINCMDLINE"
ms.assetid: 19dd24d4-b0f5-4c92-9005-aad48ffda7d9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The selected Add-In has not been confirmed to be &#39;Command Line Safe&#39;, and may require some user intervention (possible UI).
Este error suele producirse cuando se ha seleccionado un complemento que se va a utilizar desde el símbolo del sistema \(símbolo del sistema de DOS\) pero el complemento no se muestra como seguro para la línea de comandos.  Es posible que el complemento muestre una interfaz de usuario que podría interferir con el uso de la línea de comandos.  
  
### Para corregir este error  
  
1.  En el menú **Herramientas**, elija **Administrador de complementos**.  
  
2.  En el cuadro de diálogo **Administrador de complementos**, desactive la opción **Línea de comandos** para el complemento.  
  
## Vea también  
 [Cómo: Controlar complementos con el Administrador de complementos](../Topic/How%20to:%20Control%20Add-Ins%20By%20Using%20the%20Add-In%20Manager.md)   
 [Cómo: Crear un complemento](../Topic/How%20to:%20Create%20an%20Add-In.md)