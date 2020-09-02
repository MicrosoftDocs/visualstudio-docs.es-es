---
title: Modificación del shell aislado mediante el. Archivo Pkgundef | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eab02fe900e96ba37c63faae535974788f99ba78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538399"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modificación del Shell aislado mediante el archivo .Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede modificar el archivo. pkgundef para excluir las entradas del registro especificadas de una aplicación de Shell aislado. Normalmente, la primera vez que se inicia una aplicación en un equipo, Visual Studio Shell copia las entradas del registro de Visual Studio existentes en la clave del Registro raíz de la aplicación. Esto incluye todas las referencias a los VSPackages instalados actualmente.  
  
 Para excluir una entrada concreta del registro de una aplicación de Shell aislado, agregue al archivo Application. pkgundef la clave del paquete seguida de la entrada. Las claves y las entradas se representan de la misma forma que en el archivo. pkgdef; es decir, como [$RootKey $] o [$RootKey $ \\ *SubKey*] y "*entry*" =*Value*, donde *SubKey* es la subclave a la que se va a afectar, *entry* es la entrada que se va a quitar y *Value* es `""` o `dword:00000000` .  
  
 Para excluir varias entradas de una clave del registro, solo tiene que mostrar la clave una vez, seguida de una línea para cada entrada que se va a excluir.  
  
 Para excluir toda una clave del registro de una aplicación de Shell aislado, agregue la clave al archivo Application. pkgundef, pero no especifique ninguna entrada del registro para esa clave.  
  
 Puede agregar comentarios al archivo. pkgundef. Un Comentario de una sola línea debe tener dos barras diagonales como los dos primeros caracteres.  
  
 Por ejemplo, para quitar los comandos **conectarse a la base de datos** y **conectar con el servicio r** en el menú **herramientas** , puede quitar la marca de comentario de la línea:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 y agregue la línea:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 al archivo. pkgundef de la aplicación.  
  
## <a name="see-also"></a>Consulte también  
 [GUID de paquete de características de Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Personalización del Shell aislado](../extensibility/customizing-the-isolated-shell.md)
