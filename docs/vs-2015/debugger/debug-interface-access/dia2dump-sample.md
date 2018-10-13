---
title: Ejemplo Dia2dump | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d2f2dab085476a3800308c5214053c8919e84d4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300825"
---
# <a name="dia2dump-sample"></a>Ejemplo Dia2dump
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El ejemplo Dia2dump se instala con Visual Studio y contiene el archivo de origen dia2dump.cpp. El archivo ejecutable compilado se ejecuta desde la línea de comandos y muestra el contenido de un archivo de base de datos (.pdb) de programa completo.  
  
### <a name="to-install-the-sample"></a>Para instalar el ejemplo  
  
1.  Compruebe que el sistema cumple todos los requisitos de configuración que se describe en la página de inicio de instalación de Visual Studio.  
  
2.  Instale Visual Studio y siga todas las instrucciones de instalación y configuración para los ejemplos incluidos.  
  
#### <a name="to-build-the-sample"></a>Para compilar el ejemplo  
  
1.  Abra el archivo Dia2dump.sln en Visual Studio. (Si es necesario, Visual Studio le primero permitirá actualizar el proyecto Dia2dump.)  
  
2.  En las páginas de propiedades del proyecto, en el **C o C++** &#124; **General** &#124; **directorios de inclusión adicionales** propiedad, especifique el `..\DIA SDK\include` directory. Esto garantiza que el compilador puede encontrar el archivo dia2.h.  
  
3.  En el **compilar** menú, haga clic en **recompilar solución**.  
  
4.  Cierre Visual Studio.  
  
#### <a name="to-run-the-sample"></a>Para ejecutar el ejemplo  
  
1.  Abra un símbolo del sistema y escriba lo siguiente:  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Origen Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Cómo: Solucionar problemas de actualizaciones de proyecto de Visual Studio incorrectas](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)



