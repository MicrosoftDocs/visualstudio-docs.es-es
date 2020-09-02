---
title: Ejemplo de Dia2dump | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a817720c1ad73b666e0c9a586bb583120a2533c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197591"
---
# <a name="dia2dump-sample"></a>Ejemplo Dia2dump
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El ejemplo Dia2dump se instala con Visual Studio y contiene el archivo de código fuente Dia2dump. cpp. El ejecutable compilado se ejecuta desde la línea de comandos y muestra el contenido de un archivo de base de datos de programa (. pdb) completo.  
  
### <a name="to-install-the-sample"></a>Para instalar el ejemplo  
  
1. Compruebe que el sistema cumple todos los requisitos de configuración descritos en la página de inicio de la instalación de Visual Studio.  
  
2. Instale Visual Studio y siga todas las instrucciones de instalación y configuración de los ejemplos incluidos.  
  
#### <a name="to-build-the-sample"></a>Para compilar el ejemplo  
  
1. Abra el archivo Dia2dump. sln en Visual Studio. (Si es necesario, Visual Studio le ayudará primero a actualizar el proyecto Dia2dump).  
  
2. En las páginas de propiedades del proyecto, en **C/C++** &#124; **General** &#124; propiedad **directorios de inclusión adicionales** , especifique el `..\DIA SDK\include` directorio. Esto garantiza que el compilador pueda encontrar el archivo Dia2. h.  
  
3. En el menú **Compilar**, haga clic en **Recompilar solución**.  
  
4. Cierre Visual Studio.  
  
#### <a name="to-run-the-sample"></a>Para ejecutar el ejemplo  
  
1. Abra un símbolo del sistema y escriba lo siguiente:   
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Consulte también  
 [Archivo de origen Dia2dump. cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Cómo: Solucionar problemas de actualizaciones de proyecto de Visual Studio incorrectas](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)
