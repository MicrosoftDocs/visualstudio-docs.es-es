---
title: "Aplicación automática de claves de producto durante la implementación de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 1d1e0c656b91049ce53456e6c5c011c08ca2e58e
ms.openlocfilehash: db051eaf8ef98928c0fec858e4cc9380a3b7687b
ms.lasthandoff: 03/11/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Aplicación automática de claves de producto durante la implementación de Visual Studio
Puede aplicar la clave de producto mediante programación como parte de un script usado para automatizar la implementación de Visual Studio. Las claves de producto se pueden establecer en un dispositivo mediante programación durante la instalación de Visual Studio o después de completar una instalación.  
  
## <a name="apply-the-license-during-installation"></a>Aplicar la licencia durante la instalación  
 Utilice el parámetro --productKey para aplicar una clave de producto durante el proceso de instalación de Visual Studio. Este parámetro de configuración se puede utilizar con el parámetro --quiet para instalar Visual Studio en un estado ya con licencia para el usuario final. Para usar el parámetro --productKey, abra un símbolo del sistema. Ejecute el programa de instalación (por ejemplo vs_enterprise.exe o vs_professional.exe) y establezca el parámetro --productKey con una clave de producto (25 caracteres) con o sin guiones:  
  
 Este es un comando de ejemplo para la instalación de Visual Studio 2015 Enterprise con la clave de producto AAAAABBBBBCCCCCDDDDDEEEEEEE:  
  
 `vs_enterprise.exe [any other setup parameters] --productKey AAAAABBBBBCCCCCDDDDDDEEEEEE`  
  
## <a name="apply-the-license-after-installation"></a>Aplicar la licencia después de la instalación  
 Puede activar una versión instalada de Visual Studio con una clave de producto mediante la utilidad storePID.exe en los equipos de destino en modo silencioso. StorePID.exe es un programa de utilidad que se instala con Visual Studio en **\<unidad >:\\\Archivos de programa (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe**.  
  
 Ejecute storePID.exe con privilegios elevados, ya sea mediante un agente de System Center o un símbolo con privilegios elevados, seguido de la clave de producto (incluidos los guiones) y el código de producto de Microsoft (MPC). Asegúrese de incluir los guiones en la clave del producto.  
  
 `StorePID.exe [product key including the dashes] [MPC]`  
  
 Este es un ejemplo de línea de comandos para la instalación de Visual Studio 2017 Enterprise, que tiene un MPC de 08860, con una clave de producto "AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE":  
  
 `C:\Program Files (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860`  
  
 En la siguiente tabla se muestran los códigos MPC de cada edición de Visual Studio:  
  
|Edición de Visual Studio|MPC|  
|---------------------------|---------|
|Visual Studio Enterprise 2017|08860|  
|Visual Studio Professional 2017|08862|  
|Visual Studio Test Professional 2017|08866| 
|Visual Studio Enterprise 2015|07060|  
|Visual Studio Professional 2015|07062|  
|Visual Studio Test Professional 2015|07066|  
|Visual Studio Ultimate 2013|06181|  
|Visual Studio Premium 2013|06191|  
|Visual Studio Professional 2013|06177|  
|Visual Studio Test Professional 2013|06194|  
  
Si StorePID.exe aplicó correctamente la clave del producto, devolverá 0. Si encuentra errores, devolverá un número comprendido entre 1 y 6.  
  
## <a name="see-also"></a>Vea también  
 [Instalación de Visual Studio](../install/install-visual-studio.md)
 [Crear una instalación sin conexión de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
