---
title: 'Cómo: Serializar la información de símbolos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f0359613586531a4cc7b80e25acc02be9ae37f9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769189"
---
# <a name="how-to-serialize-symbol-information"></a>Cómo: Serializar la información de símbolos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede serializar símbolos que debe tener para analizar la aplicación. La serialización de símbolos agrega símbolos al archivo .vsp. Al agregar información de símbolos al archivo .vsp, otras personas pueden analizar un informe de rendimiento sin tener acceso a los símbolos originales. Si no se serializan los símbolos, debe tener archivos .exe y .pdb originales instrumentados para analizar el archivo .vsp.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Para serializar información de símbolos automáticamente  
  
1.  En el menú **Herramientas** , haga clic en **Opciones**.  
  
     Se mostrará el cuadro de diálogo **Opciones**.  
  
2.  Haga clic en **Herramientas de rendimiento**.  
  
3.  En **Configuración general**, seleccione **Serializar información de símbolos automáticamente**.  
  
## <a name="see-also"></a>Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [Cómo: Guardar archivos del informe analizado](http://msdn.microsoft.com/0340ddde-caf4-48ac-8af3-d15dcdade556)
