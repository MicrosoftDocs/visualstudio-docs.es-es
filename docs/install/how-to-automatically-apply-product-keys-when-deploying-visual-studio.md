---
title: "C&#243;mo: aplicar autom&#225;ticamente las claves de producto durante la implementaci&#243;n de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 10
caps.handback.revision: 5
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# C&#243;mo: aplicar autom&#225;ticamente las claves de producto durante la implementaci&#243;n de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede aplicar la clave de producto mediante programación como parte de un script usado para automatizar la implementación de Visual Studio. Las claves de producto se pueden establecer en un dispositivo mediante programación durante la instalación de Visual Studio o después de completar una instalación.  
  
## Aplicar la licencia durante la instalación  
 Utilice el parámetro \/ProductKey para aplicar una clave de producto durante el proceso de instalación de Visual Studio. Este parámetro de configuración se puede utilizar con el parámetro\/Silent parámetro para instalar Visual Studio en un estado ya con licencia para el usuario final. Para usar el parámetro \/ProductKey, abra un símbolo del sistema. Ejecute el programa de configuración \(por ejemplo vs\_enterprise.exe o vs\_professional.exe\) y establezca el parámetro \/ProductKey con una clave de producto \(25 caracteres\) que no incluya guiones:  
  
 Este es un comando de ejemplo para la instalación de Visual Studio 2015 Enterprise con la clave de producto AAAAABBBBBCCCCCDDDDDEEEEEEE:  
  
 `vs_enterprise.exe [any other setup parameters] /ProductKey AAAAABBBBBCCCCCDDDDDDEEEEEE`  
  
## Aplicar la licencia después de la instalación  
 Puede activar una versión instalada de Visual Studio con una clave de producto mediante la utilidad storePID.exe en los equipos de destino en modo silencioso. StorePID.exe es una utilidad que se instala con Visual Studio en **\<drive\>:\\\\Program Files \(x86\)\\Microsoft Visual Studio 14.0\\Common7\\IDE\\StorePID.exe**.  
  
 Ejecute storePID.exe con privilegios elevados, ya sea mediante un agente de System Center o un símbolo con privilegios elevados, seguido de la clave de producto \(incluidos los guiones\) y el código de producto de Microsoft \(MPC\). Asegúrese de incluir los guiones en la clave del producto.  
  
 `StorePID.exe [product key including the dashes] [MPC]`  
  
 Este es un ejemplo de línea de comandos para la instalación de Visual Studio 2015 Enterprise, que tiene un MPC de 07060, con una clave de producto "AAAAA\-BBBBB\-CCCCC\-DDDDDD\-EEEEEE":  
  
 `C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 07060`  
  
 En la siguiente tabla se muestran los códigos MPC de cada edición de Visual Studio:  
  
|Edición de Visual Studio|MPC|  
|------------------------------|---------|  
|Visual Studio Enterprise 2015|07060|  
|Visual Studio Professional 2015|07062|  
|Visual Studio Ultimate 2013|06181|  
|Visual Studio Premium 2013|06191|  
|Visual Studio Professional 2013|06177|  
  
 Para más información sobre cómo obtener una clave de producto, vea [Cómo: Encontrar la clave de producto de Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md).  
  
 Si StorePID.exe aplicó correctamente la clave del producto, devolverá 0. Si encuentra errores, devolverá un número comprendido entre 1 y 6.  
  
## Vea también  
 [Instalar Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)